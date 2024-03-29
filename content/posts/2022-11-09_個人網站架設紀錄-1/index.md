---
title: "個人網站架設紀錄 #1"
description: "千里之行，始於足下"
author: "Jian"
authorLink: "https://JianLiu666.github.io"
date: 2022-11-09T00:00:00+08:00
draft: false
categories: ["Blog"]
tags: ["Hugo", "GitPages", "GitAction"]
resources:
- name: "featured-image"
  src: "featured-image.jpg"
---

<!--more-->

Blog 的第一篇文章就用來記錄自己從零到一的個人網站架設紀錄，使用到的工具如下：

- Hugo
- Github

## Hugo

網路上有很多對於 Hugo 的說明以及教學，在這裡我就不多做介紹了，有興趣的話可以直接 Google Hugo 的關鍵字搜尋，我選擇 Hugo 的原因很簡單：

1. 社群活躍度高，模板豐富
2. 編譯速度快，請參考: [Hugo vs Jekyll: Benchmark](https://forestry.io/blog/hugo-vs-jekyll-benchmark/)

### Quick Start

環境建置可以直接參考[官方文件](https://gohugo.io/getting-started/)，裡面有詳細的教學流程可以快速建置出一個 Demo Site

> 備註：我是使用 macOS + Homebrew 進行安裝

### Theme

接著到 [Hugo Themes](https://themes.gohugo.io/) 挑選自己喜歡的模板後，透過下面的方式引用

```bash
git submodule add [-b <branch>] [--name <name>]

# e.g.
# git submodule add https://github.com/dillonzq/LoveIt.git themes/hugo-theme-loveit
```

記得到根目錄下的 `config.yaml` 或 `config.toml` 指定該樣板

```yaml
...

# See Module Config for how to import a theme.
title: "your-theme"

...
```

其餘的參數設定可以到 [Configure Hugo](https://gohugo.io/getting-started/configuration/#themesdir) 查詢

### giscus

將 GitHub Discussions 嵌入至個人網站成為訪客使用的留言系統，詳細運作原理與快速設定請參考 [giscus](https://giscus.app/zh-TW)  

設定好後可視 theme 本身是否已經預留 giscus 的擴充功能，或是自行嵌入頁面

> 這邊 shout out to LoveIt Hugo Theme 的作者，真的簡潔乾淨又好用 🫡

## Github

有了個人網站的雛形後，可以嘗試將網站發佈到 GitHub 上看看結果怎麼樣，執行以下操作編譯靜態網站：

```bash
hugo --minify
```

編譯結果會放在根目錄下的 `/public` 內，接著將靜態網站推送到 GitHub Pages 的專案位置就完成了，如果還沒有 GitHub Pages 的人可以到這裡查看官方的[建置文件](https://pages.github.com/)

### Git Action

為了讓日後只需專注在內容的產出，我們可以建立 Git Action 當 `main` branch 更新時就自動幫我們執行部署流程，workflow 的腳本可以參考官方的[部署文件](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

- 部署工具 [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-first-deployment-with-github_token)

記得在第一次執行腳本後要到 repo 設定 GitPages 的預設分支到 `gh-pages` 上，當然也可以改成自己喜歡的分支，還是不清楚的話可以參考 GitHub 的教學文件
 - [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

---

至此，我們就完成了使用 Hugo Framework + GitPages 的個人網站建置，日後有時間會再將更多的管理工具依序加入，例如：

- 內容管理服務: Forestry.io
- 網站內容即時搜尋服務: Algolia
- 網站流量統計服務: Google Analytics
- 廣告服務: Google Ads