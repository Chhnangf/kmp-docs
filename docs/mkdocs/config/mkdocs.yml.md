# [配置MkDocs的设置](https://www.mkdocs.org/user-guide/configuration/)

-----

## 1. site

```
site_name:                                  #项目名称，显示在导航栏上。这是必要的选项
site_url: https://mydomain.org/mysite       #站点地址

```

!!! info "site_url"
    The site_url setting is important for a number of reasons. By default, MkDocs will assume that your site is hosted at the root of your domain. This is not the case, for example, when publishing to GitHub pages - unless you use a custom domain. Another reason is that some of the plugins require the site_url to be set, so you should always do this.


## 2. theme
---

### 2.1 name

修改name属性来启用主题

```
theme:
  name: material                            # 启动material主题
```

!!! note "默认主题"
    若不设置`name`属性，则默认使用mkdocs的默认主题

### 2.2 features

修改features属性来启用主题功能，例如导航栏、侧边栏、搜索等功能

```
 features:
    #- navigation.indexes        # 章节索引
    - navigation.instant         # 启用即时搜索
```

### 2.3 icons

## 3. nav

```
nav:
  - MkDocs: index.md
  - Usage: usage.md
  - Blog:
     - blog/index.md
  - About:              # 一级目录
    - aboutA:           # 二级目录
      - aboutA1.md      # 三级目录
      - aboutA2.md      # 三级目录
```

在此目录下创建的md文件会作为目录导航文档显示在站点中

嵌套目录使用文件路径的方式完成编辑

## 4. plugins

插件可以扩展基础功能为其提供更强大的额外效果

```
plugins:
  - search                                      # 启用搜索功能
  - blog:                                       # 启用博客功能
      blog_toc: true                            # 启用博客目录        
      archive_date_format: MMMM yyyy            # 博客归档日期格式
      authors_file: "{blog}/.authors.yml"       # 博客作者文件
      # ... more options
  - tags                                        # 启用标签功能
```