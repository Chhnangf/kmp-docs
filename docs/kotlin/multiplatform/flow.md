# 响应式网络通信状态管理流程

这个流程展示了如何使用协程、Flow 和 Resource 类来监控和管理网络通信的状态。

1. UI发起请求并监听状态变化做出不同操作 
2. ViewModel订阅数据并发起请求
3. Repository处理请求并返回封装的响应状
4. api处理实际请求并返回http状态码

## UI发起请求并监听状态变化做出不同操作

```kotlin title="Login.kt"
val loginModel: LoginViewModel = getScreenModel()

Button(
    onClick = {
        scope.launch {
            loginModel.getUserLogin(username.value,password.value)}      
)

val state = loginModel.state.value

when (state.success) {
    0 -> {}

    1 -> { LaunchedEffect(key1 = Unit) { navigator.push(MuseumPaging()) } }

    202 -> { LaunchedEffect(key1 = Unit) { navigator.push(SignUp()) } }

}

```

## 网络请求状态

Resource 类是用来封装网络请求的不同状态的，包括成功、错误和加载中状态

```kotlin title="Resource.kt"
sealed class Resource<T>(val data: T? = null, val message:String? = null) {
    class Success<T>(data: T) : Resource<T>(data = data)
    class Error<T>(message: String, data:T? = null) : Resource<T>(data = data,message=message)
    class Loading<T>(data:T?= null) : Resource<T>(data=data)
    class Internet<T>(message: String, data:T? = null) : Resource<T>(data = data,message=message)
}
```

* Success：请求成功，包含请求返回的数据。
  
* Error：请求失败，包含错误信息。
  
* Loading：请求正在进行中。
  
* Internet：网络错误。


## 网络请求响应体

ResponseData 类用于表示 API 响应的数据结构

```kotlin title="ResponseData.kt"
@Serializable
data class ResponseData<T>(
    @SerialName("status") val status: Int,
    @SerialName("quota") val quota: Quota?,
    @SerialName("error") val error: CodableException?,
    @SerialName("main") @Serializable val main: T
)

@Serializable
data class TokenObject(val token: String)

@Serializable
data class Quota(val times: Int)
```

* status: 一个整数，通常用于表示 HTTP 状态码或操作的状态。例如，200 表示成功，4XX 表示客户端错误，5XX 表示服务器错误。

* quota: Quota 类型的对象，可能为 null。这个字段用于表示剩余的请求配额。

* error: CodableException 类型的对象，可能为 null。如果响应包含错误信息，这个字段将包含错误详情。

* main: 泛型字段 T，使用 @Serializable 注解。这个字段用于存储主要的响应数据，可以是任何类型的数据。


## ViewModel订阅数据并发起请求

```kotlin title="ViewModel.kt"

// 使用StateFlow 来存储状态暴露给UI
private val _state = mutableStateOf(LoginState<TokenObject>())
val state: State<LoginState<TokenObject>> = _state

// 声明状态类，用于存储viewmodel的状态暴露给ui
data class LoginState<T> (
    val isLoading : Boolean = false,
    val success : Int = -1,
    val loginList: ResponseData<T>? = null,//List<LoginModel.LoginJSON> = emptyList(),
    val error : CodableException? = null,
    val internet: Boolean = false
)

// 发起请求
val flow = postRepository.getUserLogin(email, password)

// 订阅数据
try {
    flow.collect { result ->
        println("LoginViewModel -> getUserLogin -> getUserLogin.collect: $result") // 打印结果
        when (result) {
            is Resource.Loading -> {
                println("LoginViewModel -> collect: Loading")
                _state.value = LoginState(
                    isLoading = true,
                    internet = false
                )
            }

            is Resource.Error -> {
                println("LoginViewModel -> collect: Error ${result.message}")
                _state.value = LoginState(
                    isLoading = false,
                    internet = false,
                    error = result.data?.error
                )
            }

            is Resource.Internet -> {
                println("LoginViewModel -> collect: Error ${result.message}")
                delay(100)
                _state.value = LoginState(
                    internet = true,
                    isLoading = false
                )
            }

            is Resource.Success -> {
                println("LoginViewModel -> collect: Success ${result.data?.status}")
                when (result.data?.status) {

                    0 -> {
                        _state.value = LoginState(
                            isLoading = false,
                            success = 0,
                            internet = false,
                            error = result.data.error
                        )
                    }



                    203 -> {}
                }


            }

        }
    }
} catch (e: Exception) {
    println("Exception caught: ${e.message}")
    _state.value = e.message?.let { LoginState(error = CodableException(-1, it)) }!!
}

```


## 存储层接收网络请求处理并返回

```kotlin title="Repository.kt"
fun getUserLogin(email:String, password:String):Flow<Resource<ResponseData<TokenObject?>>> = flow {

    emit(Resource.Loading())

    try {

        val process = postApi.userLogin(email, password)

        coroutineScope {

            emit(Resource.Success((process)))
            println("PostRepository -> getUserLogin: Success")

        }

    } catch (e: HttpException){
        println("PostRepository -> getUserLogin: e: HttpException")
        emit(Resource.Error("e: HttpException"))
    } catch (e: IOException) {
        println("PostRepository -> getUserLogin: e: IOException")
        // TODO网络链接测试
        emit(Resource.Internet("e: IOException"))
    }
}

```

!!! note
    网络请求处理中使用协程和flow时，emit发送数据到下游。在代码中使用emit发送Resource.Loading() 的目的是通知下游（比如 UI 层）当前操作已经开始，并且正在加载数据。

    Flow 是响应式的，这意味着它可以发送多个数据项，而不像 LiveData 那样只能发送一个数据项。Flow 可以持续地发送更新，这在处理数据流时非常有用，比如在数据发生变化时实时更新 UI。
    

    1. emit(Resource.Loading())：这是在开始执行登录操作之前发送的，用来告诉 UI 显示加载指示器。
    2. emit(Resource.Success((process)))：这是在登录操作成功之后发送的，用来传递成功的结果。

## api处理实际请求并返回http状态码

```kotlin title="ApiService.kt"

// setBody需要一个T对象，所以需要声明一个类来处理要发送的数据
@Serializable
data class AccountLoginEmailStruct(val email: String, val password: String)

suspend fun userLogin(email: String, password: String): ResponseData<TokenObject?> {

        val response: HttpResponse = client.post(lesterWorkLogin) {

            contentType(ContentType.Application.Json)

            setBody(AccountLoginEmailStruct(email, password))
        }

            println("Post HTTP -> userLogin response.bodyAsText: ${response.bodyAsText()}")

            return response.body()

    }

```


