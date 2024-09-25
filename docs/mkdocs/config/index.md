# MkDocs项目结构和配置项

[MkDocs基础设置](https://squidfunk.github.io/mkdocs-material/setup/)

[MkDocs插件](https://squidfunk.github.io/mkdocs-material/plugins/)

[MkDocs官方示例](https://squidfunk.github.io/mkdocs-material/reference/)

-----

## Commands

```
mkdocs new [dir-name]           # Create a new project.
mkdocs serve                    # Start the live-reloading docs server.
mkdocs build                    # Build the documentation site.
mkdocs -h                       # Print help message and exit.
mkdocs gh-deploy --force        # Deploy to GitHub Pages.
```

## Project layout
```python title='Structure Tree' 
$ tree
.
├── docs                            # 文档目录
│   ├── blog                        # 博客目录
│   │   ├── posts                   # 博客文章
│   │   ├── .author.yml             # 作者信息
│   │   └── index.md                # 博客首页
│   └──index.md                     # 站点首页
├── overrides                       # 覆盖文件
│   ├─ .icons/                             # Bundled icon sets
│   ├─ assets/
│   │  ├─ images/                          # Images and icons
│   │  ├─ javascripts/                     # JavaScript files
│   │  └─ stylesheets/                     # Style sheets
│   ├─ partials/
│   │  ├─ integrations/                    # Third-party integrations
│   │  │  ├─ analytics/                    # Analytics integrations
│   │  │  └─ analytics.html                # Analytics setup
│   │  ├─ languages/                       # Translation languages
│   │  ├─ actions.html                     # Actions
│   │  ├─ alternate.html                   # Site language selector
│   │  ├─ comments.html                    # Comment system (empty by default)
│   │  ├─ consent.html                     # Consent
│   │  ├─ content.html                     # Page content
│   │  ├─ copyright.html                   # Copyright and theme information
│   │  ├─ feedback.html                    # Was this page helpful?
│   │  ├─ footer.html                      # Footer bar
│   │  ├─ header.html                      # Header bar
│   │  ├─ icons.html                       # Custom icons
│   │  ├─ language.html                    # Translation setup
│   │  ├─ logo.html                        # Logo in header and sidebar
│   │  ├─ nav.html                         # Main navigation
│   │  ├─ nav-item.html                    # Main navigation item
│   │  ├─ pagination.html                  # Pagination (used for blog)
│   │  ├─ palette.html                     # Color palette toggle
│   │  ├─ post.html                        # Blog post excerpt
│   │  ├─ progress.html                    # Progress indicator
│   │  ├─ search.html                      # Search interface
│   │  ├─ social.html                      # Social links
│   │  ├─ source.html                      # Repository information
│   │  ├─ source-file.html                 # Source file information
│   │  ├─ tabs.html                        # Tabs navigation
│   │  ├─ tabs-item.html                   # Tabs navigation item
│   │  ├─ tags.html                        # Tags
│   │  ├─ toc.html                         # Table of contents
│   │  ├─ toc-item.html                    # Table of contents item
│   │  └─ top.html                         # Back-to-top button
│   ├─ 404.html                            # 404 error page
│   ├─ base.html                           # Base template
│   ├─ blog.html                           # Blog index page
│   ├─ blog-archive.html                   # Blog archive index page
│   ├─ blog-category.html                  # Blog category index page
│   ├─ blog-post.html                      # Blog post page
│   └─ main.html                           # Default page
├── site                            # 静态站点
└── mkdocs.yml                      # 配置文件
```

## Introduction

默认情况下，使用项目目录中名为mkdocs.yml的 YAML 配置文件来配置项目设置

该配置文件至少必须包含`site_name` 。所有其他设置都是可选的

## Project information

**自定义主题**



> The site_url setting is important for a number of reasons. By default, MkDocs will assume that your site is hosted at the root of your domain. This is not the case, for example, when publishing to GitHub pages - unless you use a custom domain. Another reason is that some of the plugins require the site_url to be set, so you should always do this.

