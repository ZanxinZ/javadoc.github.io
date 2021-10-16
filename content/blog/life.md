---
title: "Life"
date: 2021-09-08T18:37:17+08:00
draft: true
---
## 关于 Hugo GeekDoc

- GitHub 先新建一个仓库，并配置 Github Pages。
- 把项目 clone 下来
- 把 hugo 可运行程序放置到项目目录下。
- 下载 geekdoc 的 **release**，放到 theme 文件夹下。
- 配置config.toml
  ```toml
    baseURL = 'http://example.org/'
    languageCode = 'en-us'
    title = '技术学习笔记'
    theme = "hugo-geekdoc"

    # Match the github rule.
    publishdir = "./docs/" 

    pluralizeListTitles = false

    # Geekdoc required configuration
    pygmentsUseClasses = true
    pygmentsCodeFences = true
    disablePathToLower = true

    # Needed for mermaid shortcodes
    [markup]
    [markup.goldmark.renderer]
        # Needed for mermaid shortcode
        unsafe = true
    [markup.tableOfContents]
        startLevel = 1
        endLevel = 9

    [taxonomies]
    tag = "tags"
   
  ```
- 开始写文章
  ```cmd
  hugo new blog/life.md
  ```
- 测试
  ```cmd
  hugo server -D
  ```
- 生成 HTML
  ```cmd
  hugo -D
  ```

## Hugo 使用方法
- 提示板
  {{<hint ok>}}
  提示板

  这是 hint ok
  {{</hint>}}

  {{<hint info>}}
  提示板

  这是 hint info
  {{</hint>}}

  {{<hint warning>}}
  提示板
  
  这是 hint warn
  {{</hint>}}

  {{<hint danger>}}
  提示板
  
  这是 hint danger
  {{</hint>}}

  {{<hint >}}
  提示板
  
  这是 hint 
  {{</hint>}}

- 导航栏
  - 目录只允许在 content 下多加一层。
  

## 在学校
### 研一9月
- 到校占工位啦

  把思昊君赠予的显示器摆上了我的工位，桌板上有个洞和显示器支架的脚刚好契合，可以把显示器竖起来，竖屏即刻体验拉满。
  ![me](/table.jpg)

