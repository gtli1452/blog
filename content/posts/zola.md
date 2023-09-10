+++
title="使用 Zola 架設部落格"
date=2023-09-10

[taxonomies]
categories = ["Sample Post"]
tags = ["zola", "SSG"]
+++

## 前言

- 第一聽到 [Zola](https://www.getzola.org/)是從 PJW 的 [Pin 起來改版了！從 Wordpress 搬家到 Zola！](https://pinchlime.com/blog/rebuilt-pinchlime/)
- 其樣板改自 [owen](https://www.owenyoung.com/) 的 [source code](https://github.com/theowenyoung/blog)，且 PJW 也是因為當初看到 owen 的 迁移博客和Wiki到 Zola 後，才考慮使用 [Zola](https://www.getzola.org/)

<!-- more -->

## 開始

先列出主要參考資料

- [官方文件](https://www.getzola.org/documentation/getting-started/overview/)
- [\[Zola\] 開始架自己的部落格-使用Zola建置專案](https://marvinhsu.eth.limo/zola-01-introduction/)
- [Zola 静态博客快速指南](https://caiye.one/zola-quick-start/)
- [靜態網站產生器 Zola](https://editor.leonh.space/2022/zola/)

流程分為三個步驟 (參考自[\[Zola\] 開始架自己的部落格-使用Zola建置專案](https://marvinhsu.eth.limo/zola-01-introduction/))

1. 建置 Zola 專案: `$ zola init`

   1. In Windows: `$ scoop install zola`
   2. `$ zola init myblog` (將專案放置指定資料夾 `myblog`)
      1. 初始化完會有以下資料夾結構

         ```xml
         ├── config.toml
         ├── content
         ├── sass
         ├── static
         ├── templates
         └── themes
         ```

         - config.toml: 專案屬性的設定檔
         - content: 之後網站的實際內容都會存成 .md 檔放在這邊
         - sass: 放專案的 SASS 樣式檔
         - static: 放一些靜態資源，e.g., 圖檔
         - templates: 放網站主題
         - themes: 設定網站模板

      2. 實際使用結果

      ```!xml
      ├── config.toml
      ├── content/
      │   └── blog/
      │       ├── _index.md
      │       ├── first.md
      │       └── second.md
      ├── sass/
      ├── static/
      ├── templates/
      │   ├── base.html
      │   ├── blog-page.html
      │   ├── blog.html
      │   └── index.html
      └── themes/
      ```

2. Theme: 套用主題
   1. 使用 git submodule 套用主題，後續主題有更新可直接使用

      ```bash
      ## git submodule add [url] themes/tale-zola
      ## [url]是該主題的Repository來源
      $ $ git submodule add git@github.com:aaranxu/tale-zola.git themes/tale-zola
      ```

   2. 設定 `config.toml`

      ```bash
      // The URL the site will be built for
      base_url = "https://example.com"

      //指定主題的名稱
      theme="tale-zola"
      ```

   3. 待選主題 → 最後決定使用 [DeepThough](https://deepthought-theme.netlify.app/)
      1. <https://getzola.github.io/even/>
      2. <https://tale-zola.netlify.app/>
      3. <https://schoenenberg.github.io/zola-paper/>
      4. <https://cydave.github.io/zola-theme-papermod/>
      5. <https://deepthought-theme.netlify.app/>

3. Deployment: 佈署網頁

## 參考資料

[Hello World | Blog (](https://funcxiao.wang/blog/2020/hello-world/)[funcxiao.wang](funcxiao.wang)[)](https://funcxiao.wang/blog/2020/hello-world/)

1. Build local project

   ```bash
   # 创建文件夹myblog，Git初始化并新建zola项目
   $ git init && zola init
   # 添加Float主题，作为Git子模块加入
   $ git submodule add https://gitlab.com/float-theme/float.git themes/float
   ```

2. 發布
   最简单的办法就是编写一份 [++netlify.toml++](https://www.getzola.org/documentation/deployment/netlify/)，这样在 netlify 网站中添加 github 仓库后，每次本地写完了推送到 github 上，netlify 就会拉过去使用配置文件中指定版本的的 `zola` 来生成静态网页并部署在 netlify 上

[PZY | 本站成功搬迁到 Zola](https://pzy.io/posts/migrate-to-zola/)
