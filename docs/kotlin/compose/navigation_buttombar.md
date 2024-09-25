# Navigation BottomBar

## 使用到的依赖

需要添加的依赖：
1. 图标库

=== "libs"
    ```
    [versions]
    composeIcons = "1.1.0"

    [libraries]
    composeIcons-cssGg = { module = "br.com.devsrsouza.compose.icons:css-gg", version.ref = "composeIcons" }
    composeIcons-weatherIcons = { module = "br.com.devsrsouza.compose.icons:erikflowers-weather-icons", version.ref = "composeIcons" }
    composeIcons-evaIcons = { module = "br.com.devsrsouza.compose.icons:eva-icons", version.ref = "composeIcons" }
    composeIcons-feather = { module = "br.com.devsrsouza.compose.icons:feather", version.ref = "composeIcons" }
    composeIcons-fontAwesome = { module = "br.com.devsrsouza.compose.icons:font-awesome", version.ref = "composeIcons" }
    composeIcons-lineAwesome = { module = "br.com.devsrsouza.compose.icons:line-awesome", version.ref = "composeIcons" }
    composeIcons-linea = { module = "br.com.devsrsouza.compose.icons:linea", version.ref = "composeIcons" }
    composeIcons-octicons = { module = "br.com.devsrsouza.compose.icons:octicons", version.ref = "composeIcons" }
    composeIcons-simpleIcons = { module = "br.com.devsrsouza.compose.icons:simple-icons", version.ref = "composeIcons" }
    composeIcons-tablerIcons = { module = "br.com.devsrsouza.compose.icons:tabler-icons", version.ref = "composeIcons" }
    ```
=== "gradle"
    ```
    
    commonMain.dependencies {

      // Icons Collection
      implementation(libs.composeIcons.cssGg)
      implementation(libs.composeIcons.weatherIcons)
      implementation(libs.composeIcons.evaIcons)
      implementation(libs.composeIcons.feather)
      implementation(libs.composeIcons.fontAwesome)
      implementation(libs.composeIcons.lineAwesome)
      implementation(libs.composeIcons.linea)
      implementation(libs.composeIcons.octicons)
      implementation(libs.composeIcons.simpleIcons)
      implementation(libs.composeIcons.tablerIcons)

    }
    ```

## 定义目标页面枚举

=== "NavScreen.kt"
```

import androidx.compose.ui.graphics.vector.ImageVector

enum class NavBtmBar (

  val unselectIcon: ImageVector,
  val selectIcon: ImageVector,
  val title: String,
) {
  SCREEN_HOME(
    EvaIcons.Outline.Home,
    EvaIcons.Fill.Home,
    "账号"
  ),

  SCREEN_KEY(
    EvaIcons.Fill.PlusSquare,
    EvaIcons.Fill.PlusSquare,
    "密码"
  ),

  SCREEN_SETTINGS(
    EvaIcons.Outline.Person,
    EvaIcons.Fill.Person,
    "设置"
  ),
}

```

## 定义目标页面路由

使用voyager

=== "libs"
    ```
    [versions]
    voyager = "1.0.0"

    [libraries]
    voyager-navigator = { module = "cafe.adriel.voyager:voyager-navigator", version.ref = "voyager" }
    voyager-screenModel = { module = "cafe.adriel.voyager:voyager-screenmodel", version.ref = "voyager" }
    voyager-bottomSheetNavigator = { module = "cafe.adriel.voyager:voyager-bottom-sheet-navigator", version.ref = "voyager" }
    voyager-tabNavigator = { module = "cafe.adriel.voyager:voyager-tab-navigator", version.ref = "voyager" }
    voyager-transitions = { module = "cafe.adriel.voyager:voyager-transitions", version.ref = "voyager" }
    voyager-koin = { module = "cafe.adriel.voyager:voyager-koin", version.ref = "voyager" }
    voyager-hilt = { module = "cafe.adriel.voyager:voyager-hilt", version.ref = "voyager" }
    ```
=== "gradle"
    ```
    commonMain.dependencies {

      // Voyager
      implementation(libs.voyager.navigator)
      implementation(libs.voyager.transitions)
      implementation(libs.voyager.hilt)

    }
    
    
    
    
    ```

------
=== "MainScreen.kt"
    ```
    ```