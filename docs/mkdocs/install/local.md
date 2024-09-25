# Local Enviroment Setup
-----

## Install python && pip

MkDocs的主题材料（Theme Material）以Python包的形式发布，通过pip包管理器进行安装和管理

1. 检验是否安装有python和pip环境（windows）

    1.1 有环境执行终端

    === "Windows"

        ``` 
        python --version
        Python 3.12.5
      
        pip --version
        pip 24.2 from C:\Users\admin\AppData\Local\Programs\Python\Python312\Lib\site-packages\pip (python 3.12)
        ```
    === "Macos"

        ``` 
        $ python --version
        ```


    1.2 没有环境则需安装

    * 安装python：[Python Release Python 3.12.5 | Python.org](https://www.python.org/downloads/release/python-3125/)

        !!! warning
             安装过程中启用配置python到环境变量或手动配置

    * 安装pip：

         ```
         curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
         python get-pip.py
         ```

2. 通过pip安装`material`主题的`mkdocs`

    ```
    pip install -e mkdocs-material
    ```

## Create a project

选择一个目录进入终端，执行`mkdocs new [dir-name]`或者`mkdocs new .`命令创建一个项目

```python title='mkdocs new my-project'
PS F:\> mkdocs new my-project
```

## Start the server && preview local html

在项目终端执行`mkdocs serve`启动服务

出现下面的代码表示文档构建成功并且在本地服务器上运行，通过浏览器预览效果
```python title='mkdocs serve'
PS F:\mkdocs> mkdocs serve
...
INFO    -  Documentation built in 0.44 seconds
INFO    -  [17:07:54] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [17:07:54] Serving on http://127.0.0.1:8000/mysite/
INFO    -  [17:07:56] Browser connected: http://127.0.0.1:8000/mysite/install/local/
```

## Build a static site


```python title='mkdocs build'
PS F:\> mkdocs build
INFO    -  Documentation built in 0.42 seconds
```

构建成功会在项目根目录生成一个`site`目录，其中存放着编写的markdown静态网页文件
