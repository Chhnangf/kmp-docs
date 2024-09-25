---
date:
  created: 2024-09-14
draft: false
categories: 
    - Python
---

# 基于Selenium和Webdriver的网页爬虫

## Python 环境

安装pip 包管理器

## WebDriver 驱动

浏览器驱动是运行自动化测试的必要工具，它负责模拟浏览器行为，如点击、输入，还可以动态地显示jscript代码效果。

* ChromeDriver：Chrome浏览器的驱动，用于控制Chrome浏览器。
* [Microsoft Edge WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/?form=MA13LH#downloads)：Edge浏览器的驱动，用于控制Edge浏览器。

---

2. 安装ChromeDriver
    pip install webdriver_manager

    pip install --upgrade selenium webdriver-manager

!!! warning "browser"
    浏览器驱动需要与浏览器版本匹配，否则可能会导致无法正确运行自动化测试。（浏览器更最新）


## Selenium Web自动化

  * **用途**：用于Web自动化测试和浏览器自动化库。

  * **特点**：Selenium 可以模拟用户的行为，如点击、滚动、填写表单等，这些操作可以触发JavaScript和Ajax调用，从而加载和更新页面内容。因此，Selenium 能够处理动态网页，获取页面在用户交互后的状态。
  
---

### 1. 安装selenium

    pip install selenium

    pip install --upgrade selenium

### 2. python脚本

#### 2.1 IDE

推荐使用`Visual Studio Code`

安装插件`Python`

创建.py文件,编写code

右键空白处终端运行python即可预览

---

#### 2.2 示例

此处以edge为例

##### 2.2.1 导入库
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.edge.service import Service
from webdriver_manager.microsoft import EdgeChromiumDriverManager
```

##### 2.2.2 创建浏览器实例

```
# 创建Edge浏览器实例
service = Service(EdgeChromiumDriverManager().install())
driver = webdriver.Edge(service=service)
```

##### 2.2.3 打开网页

```
# 网页的URL
url = 'https://xff.one/'

# 浏览器实例打开网页
driver.get(url)
```

##### 2.2.4 等待页面加载完成

``` python
try:
    # 等待歌单列表元素加载完成
    wait = WebDriverWait(driver, 300)  # 等待最多30秒
    
    wait.until(EC.presence_of_all_elements_located((By.CSS_SELECTOR, ".myhkplaylist-bd .album-list .myhklist .mCSB_container ul li")))
    print("歌单列表加载完成！")
    
    # 获取歌词列表的所有元素
    lyrics_elements = driver.find_elements(By.CSS_SELECTOR, ".myhkplaylist-bd .album-list .myhklist .mCSB_container ul li")
    print("获取到歌词列表！", lyrics_elements)
    
    # 遍历所有歌词元素，提取文本
    lyrics = [element.get_attribute('textContent').strip() for element in lyrics_elements if element.get_attribute('textContent').strip()]
    print("提取到歌词！", lyrics)

    # 打印歌词
    for line in lyrics:
        print(line)

    # 如果需要，可以将歌词保存到文件
    with open('lyrics.txt', 'w', encoding='utf-8') as file:
        for line in lyrics:
            file.write(line + '\n')
            
except Exception as e:
    print("发生错误：", e)
    
finally:
    # 关闭浏览器
    driver.quit()
```

!!! tip "注意"
    1. 使用try ... except ... finally ... 块来处理元素加载和异常。
    2. 查询前要等待页面加载完成，否则可能获取不到数据。
          1. `WebDriverWait`: 超时时间
          2. `until`: 等待要查询的元素加载完成
          3. `presence_of_all_elements_located`: 指定要加载的全部元素
          4. `By.CSS_SELECTOR`: CSS选择器，需要通过html定位到要查询的元素及关系，需要具备html基础知识
    3. 提取元素的内容，使用`get_attribute('textContent')`更稳定
    4. 提取的内容一般是table，使用for循环遍历提取行列数据
    
### 完整代码
``` python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.edge.service import Service
from webdriver_manager.microsoft import EdgeChromiumDriverManager

# 创建Edge浏览器实例
service = Service(EdgeChromiumDriverManager().install())
driver = webdriver.Edge(service=service)

# 网页的URL
url = 'https://xff.one/'

# 浏览器实例打开网页
driver.get(url)

try:
    # 等待歌单列表元素加载完成
    wait = WebDriverWait(driver, 30)  # 等待最多30秒
    
    wait.until(EC.presence_of_all_elements_located((By.CSS_SELECTOR, ".myhkplaylist-bd .album-list .myhklist .mCSB_container ul li")))
    print("歌单列表加载完成！")
    
    # 获取歌词列表的所有元素
    lyrics_elements = driver.find_elements(By.CSS_SELECTOR, ".myhkplaylist-bd .album-list .myhklist .mCSB_container ul li")
    print("获取到歌词列表！", lyrics_elements)
    
    # 遍历所有歌词元素，提取文本
    lyrics = [element.get_attribute('textContent').strip() for element in lyrics_elements if element.get_attribute('textContent').strip()]
    print("提取到歌词！", lyrics)

    # 打印歌词
    for line in lyrics:
        print(line)

    # 如果需要，可以将歌词保存到文件
    with open('lyrics.txt', 'w', encoding='utf-8') as file:
        for line in lyrics:
            file.write(line + '\n')
            
except Exception as e:
    print("发生错误：", e)
    
finally:
    # 关闭浏览器
    driver.quit()
```




## BeautifulSoup 静态网页解析库

Python的BeautifulSoup库是一个用于解析HTML和XML文档的库。它常与requests库一起使用来抓取静态的网页内容

- **用途**：用于解析HTML和XML文档。

- **特点**：它提取静态内容，即页面的初始HTML代码。如果内容是通过JavaScript动态加载的，那么在页面加载时 BeautifulSoup 可能无法获取到这些内容，除非它在解析之前已经被渲染到HTML中。


### 1. 安装
``` title="安装BeautifulSoup"
pip install beautifulsoup4
pip install lxml  # 或者安装其他解析器如 html5lib
```

### 2. 导入库


    import requests
    from bs4 import BeautifulSoup


### 3. 抓取网页内容


    url = 'https://www.example.com'
    response = requests.get(url)


### 4. 解析网页内容

将获取到的HTML内容传递给BeautifulSoup，同时指定一个解析器。

    soup = BeautifulSoup(html_content, 'lxml')  # 或者使用 'html.parser'

### 5. 查找元素

```
for link in links:
    print(link.get('href'))  # 获取href属性

print(first_paragraph.text)  # 获取文本内容

# 查找所有的<a>标签
links = soup.find_all('a')

# 查找第一个<p>标签
first_paragraph = soup.find('p')

# 使用CSS选择器
headlines = soup.select('h1, h2, h3')

# 使用属性查找
images = soup.find_all('img', {'src': True})
```

### 6. 提取数据

```
# 打印整个文档
print(soup.prettify())

# 保存到文件
with open('output.html', 'w', encoding='utf-8') as file:
    file.write(str(soup))
```