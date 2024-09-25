# Syntax adn yml Config

## nav

### 基本目录

```
nav:
    - directory nameA: directory path
    - directory nameB: directory path
    ...
```

### 嵌套目录

```
nav:
    - directory nameA: directory path
        - subdirectory nameA: subdirectory path
        - subdirectory nameB: subdirectory path
        ...
    - directory nameB: directory path
    ...
```

设置主目录的页面内容，必须以**index.md**文件结尾

```
nav:
    - directory nameA: 
        - directory path/index.md:
        - subdirectory nameA: subdirectory path
```

## 内容目录

根据标题等级自动生成，一级最大

## 隐藏导航/目录栏

```
---
hide:
  - navigation
  - toc
---

# Page title
...
```