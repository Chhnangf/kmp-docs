---
date:
  created: 2024-09-20
draft: false
categories: 
    - Github
---

# GitHub

## GitHub简洁、历史与发展

GitHub 是一个开发者平台，允许开发者创建、存储、管理和共享他们的代码。它使用 Git 软件，为每个项目提供 Git 的分布式版本控制以及访问控制、错误跟踪、软件功能请求、任务管理、持续集成和 wiki。

它通常用于托管开源软件开发项目。截至 2023 年 1 月，GitHub 报告称拥有超过 1 亿开发者和超过 4.2 亿个存储库，其中包括至少 2800 万个公共存储库。截至 2023 年 6 月，它是世界上最大的源代码托管者。

Mascot 吉祥物

GitHub 的吉祥物是一只拟人化的“章鱼猫”，有五只章鱼般的手臂。这个角色是由平面设计师 Simon Oxley 创作的剪贴画，在 iStock 上出售，这是一个让设计师能够销售免版税数字图像的网站。GitHub 选择的插图是 Oxley 命名为 Octopuss 的角色。由于 GitHub 希望将 Octopuss 作为其徽标（iStock 许可证不允许使用），他们与 Oxley 协商购买该图像的独家使用权。

GitHub 将 Octopuss 更名为 Octocat，并将该角色与新名称一起注册为商标。后来，GitHub 聘请插画师 Cameron McEfee 将 Octocat 改编为网站和宣传材料上的不同用途；此后，McEfee 和各种 GitHub 用户已经创建了数百种该角色的变体，这些变体可在 Octodex 上找到。

该公司总部位于加利福尼亚州，自 2018 年以来一直是微软的子公司。



## 镜像网站

### What is a mirror?
镜像原意是光学里指的物体在镜面中所成之像。引申到计算机网络上，镜像通常用于为相同信息内容提供不同的源，特别是在下载量大的时候提供了一种可靠的网络连接。制作镜像是一种文件同步的过程。

### What is a mirror site?
镜像网站，即把一个互联网上的网站数据“拷贝”到本地服务器，并保持本地服务器数据的同步更新，因此也称为“复制网络站点” 。它和主站并没有太大差别，或者可算是为主站作的后备措施。

有了镜像网站的好处是：如果不能对主站作正常访问（如某个服务器死掉或出了意外），但仍能通过其它服务器正常浏览。

### Why use mirrored websites?

由于一些特殊原因，Github 在国内访问并不稳定。日常使用中，其官网偶尔会间接性的被屏蔽，访问速度慢，在 Clone GitHub 上的代码时很容易出现连接超时的情况，给无法翻墙的同学造成了很多困扰，我们可以使用镜像网站来代替 Github，基本包含了 Github 上已有的项目信息，并且可以查看和下载相关项目，可以作为备用网站使用。

## Usage

1. 初始化仓库
```
git init
```

2. 添加远程仓库
```
git remote add origin <url>
```

3. 将文件添加到暂存区
```
git add .
```

4. 将文件提交到本地仓库
```
git commit -m "message"
```

-u 参数是 --set-upstream 的简写


5. 将本地仓库提交到远程仓库
```
git push -u origin main
```

6. 处理可能的合并冲突

```
git pull origin main
```

7. 设置 SSH 密钥（如果使用 SSH 方式连接）


### 

### Message

feature（功能）

factory（重构框架）

fix（）

