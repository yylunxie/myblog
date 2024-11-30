---
title: "Hugo + GitHub Pages 個人網站建置教學"
date: "2024-11-30T22:36:51+08:00"
tags: ["Hugo", "GitHub Pages", "PaperMod"]
slug: hugo_tutorial
draft: true
cover:
  image: "<image path/url>" # image path/url
  alt: "<alt text>" # alt text
  caption: "<text>" # display caption under cover
  relative: false # when using page bundles set this to true
  hidden: true # only hide on current single page
---

在現在好像沒有自己的品牌是一件很稀有的事（ 比日本製的壓縮機還要稀少 ）。為了解決大家的煩惱，這是一篇帶你使用 **Hugo + Github Pages** 從零開始製作個人網站的教學！

那我們就直接開始！

### 1. 安裝 Hugo

### 2. 選擇主題

### 3. PaperMod Config 設定

### 4. GitHub Pages 部署

**Step 1.**

建立一個 GitHub repository，repository 的名字可以隨意命名

**Step 2.**

將你的本地檔案 push 到剛剛創建的 GiuHub repository

**Step 3.**

進入你的 GitHub repository，選擇 **Settings** > **Pages**

在畫面中間的 **Build and Deployment** 段落可以看到 **Source**，我們將 **Source** 設定為 **GitHub Actions**

**Step 4.**

在本地 repository 新增一個檔案

```
touch .github/workflows/hugo.yaml
```

並將下列內容複製貼上到你新增的`.github/workflows/hugo.yaml`，依照你的需求，有可能需要更改 **branch name** 和 **hugo version**

```
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.137.1
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          HUGO_CACHEDIR: ${{ runner.temp }}/hugo_cache
          HUGO_ENVIRONMENT: production
          TZ: America/Los_Angeles
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

最後，將變更提交並推送到 GitHub

**Step 5.**

回到 GitHub repository 的 main menu，選擇 **Actions** 就會看到剛剛提交的 commit 變成一個橘色的 workflow，代表我們的網站正在交給 GitHub Pages 部署。

等到變成綠色，代表網站部署成功！

### 5. 自訂域名

**Step 0.**

購買域名，可到例如 [namecheap](https://www.namecheap.com/)、[GoDaddy](https://tw.godaddy.com/) 等網站購買

**Step 1.**

進入網站的 GitHub repository，點選 **Settings > Pages**

並在 **Custom Domain** 中，設定購買的域名。接著，通常沒有在域名購買的網站上設定過，會顯示失敗

**Step 2.**

到域名購買商的網站，幫你購買的域名設定 DNS， `A record` 以及 `CNAME`

- A record

  host 或 record name 是 `@`

  ```
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```

- CNAME

  host 或 record name 是 `www`

  ```
  <your github account name>.github.io
  ```

當設定完成後，過一下 GitHub Pages 的自訂域名就設定完成了！

## 參考資料

- [Custom Doamin](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [Hugo on GitHub Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
- []
