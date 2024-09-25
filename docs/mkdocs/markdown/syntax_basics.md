# Markdown Basics Syntax
---

## 1.0 Introduction

markdwon语法使用条件基本为`符号`后跟`空格`再跟`内容`

## 1.1 Title

`#`接着字符表示1-6级标题

```
# 一级标题   
## 二级标题   
### 三级标题   
#### 四级标题   
##### 五级标题   
###### 六级标题
```

!!! note
    * 一个.md文件中只能有1个一级标题，如果有多个一级标题则不会自动生成页目录。
    * 如果有 #，则使用该标题作为本页正文部分第一行，如果没有#，则为mkdocs.yml里指定的pages名。

------

## 1.2 段落

一个段落表示一个语法块，每个语法块之间要有空行，若想在段内强制换行的方式是使用 两个以上 空格加上回车。

建议: 如果写一个语法，效果和想象的不一样，比如挤在一行内，或者没有缩进，则多1、2个换行试试

---

## 1.3 引用

使用`>`接字符表示引用，引用的文本会以灰色背景显示，并且会缩进。还可以进一步嵌套引用

```
> 引用文本
>> 嵌套引用
```

示例
> 引用文本
>> 嵌套引用

## 1.4 表格

```
| 字段1 | 字段2 | 字段3 |
| :---- | :---- | :---- |
| A1    | B1    | C1    |
| A2    | B2    | C2    |
```

示例  

| 字段1 | 字段2 | 字段3 |
| :---- | :---: | ----: |
| A1    |  B1   |    C1 |
| A2    |  B2   |    C2 |

!!! note
    * `:----` 表示左对齐  
    * `:---:` 表示居中  
    * `----:` 表示右对齐  

## 1.5 Code

### 1.5.1 Line Highlight

使用`表示行内高亮

```
A `B` C
```
A `B` C

### 1.5.2 Code Block

4 个空格或 1 个制表符

        4 * space
        print('hello world')

或者3个反引号
    
    ```python
    print('hello world')
    ```  

```python
print('hello world')
``` 

!!! note
    * 代码块的语法高亮默认是python，如果要高亮其他语言，则需要使用````language`来指定。

## 1.6 Font
---

### 1.6.1 Bold
    **bold** or __bold__

**bold** or __bold__  

### 1.6.2 Italic

    *italic* or _italic_

**bold** or __bold__  

### 1.6.3 Bold Italic

    ***italic bold*** or ___ bold italic ___

***bold italic*** or ___bold italic___

### 1.6.4 删除线

### 1.6.5 下划线

## 1.7 List

### 1.7.1 Unordered List

使用`*`/`-`/`+`开头表示无序列表

```
- item1
- item2
- item3
```

- item1
- item2
- item3

### 1.7.2 Ordered List

数字加`.`
```
1. item1
2. item2
3. item3
```
1. item1
2. item2
3. item3

### 1.7.3 任务列表

依赖模块: pymdownx.tasklist

用法：`- [ ] `或 `- [x] `,其中`[ ]`表示未完成，`[x]`表示已完成。`-`可以替换为`+`或`*`

```
- [ ] item1
* [x] item2
- [ ] item3
```

- [ ] item1

- [ ] item2
  
- [x] item3

## 1.8 分割线

连续3个以上的`-`、`*`、`_`即可

```
---
```

---
## 1.9 link

### 1.9.1 普通链接

```
[example](http://www.example.com/ "title")
```

[example](http://www.example.com/ "title")

鼠标悬停在链接上可以看到"title"字样

### 1.9.2 自动连接

依赖模块: pymdownx.magiclink

当识别到HTML、FTP、Email地址时候会自动转为超链接，如

```
http://www.example.cpm/
```

http://www.example.cpm/

!!! note "支持的链接格式"
    1. http://www.example.com/    
    2. https://www.example.com/  
    3. ftp://www.example.com/  
    4. www.example.com  
    5. user@example.com

## 2.0 Image

添加图片与链接类似，只需要在链接前面加上`!`即可

```
![example](https://gd-hbimg.huaban.com/4f244417fcf2faa1b2c9a028ed4fda0b7ce524d046023d-IpQKmW_fw658webp)
```

![example](https://gd-hbimg.huaban.com/4f244417fcf2faa1b2c9a028ed4fda0b7ce524d046023d-IpQKmW_fw658webp)


## 2.1 注解

写注解使用，依赖模块: admonition

支持多种样式，如带有标题、无标题、空标题，还支持折叠式(常用于FAQ)

支持多种颜色风格，包括警告提示、错误提示、成功提示等11种风格

### 2.1.1 Note reminder

```
!!! note "自定义标题"
    内容

!!! note ""
    空标题

!!! note 
    默认标题
```

!!! note "自定义标题"
    内容

!!! note ""
    空标题

!!! note 
    默认标题

### 2.1.2 Fold reminder

```
??? note "标题"
    内容
```

??? note "标题"
    内容

!!! warning 
    折叠中的内容在折叠未打开时候通过ctrl-f是搜索不出来的，但可以通过页面上方的Search栏里搜到

### 2.1.3 Other reminder

```
!!! note "note, seealso"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! summary "summary, tldr"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! info "info, todo"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! tip "tip, hint, important"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! success "success, check, done"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! question "question, help, faq"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! warning "warning, caution, attention"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```


```
!!! failure "failure, fail, missing"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! bug "bug"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

```
!!! quote "quote, cite"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
```

!!! note "note, seealso"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! summary "summary, tldr"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! info "info, todo"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! tip "tip, hint, important"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! success "success, check, done"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! question "question, help, faq"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! warning "warning, caution, attention"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! failure "failure, fail, missing"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! danger "danger, error"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! bug "bug"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! quote "quote, cite"
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.


