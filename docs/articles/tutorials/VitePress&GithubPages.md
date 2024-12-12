# VitePress&GithubPages 建站

## VitePress
[VitePress](https://vitepress.dev/zh/) 
### 创建本地项目
这边使用 pnpm 安装vitepress
```sh
npm -g i pnpm
pnpm add -D vitepress
```
创建项目文件夹并进入
```sh
mkdir my-blog
cd my-blog
```
在使用脚手架,初始化项目
```sh
pnpm init vitepress
```
填写项目信息

### 配置
配置.vitepress文件夹的config 文件
```ts
import { defineConfig } from 'vitepress'

// https://vitepress.dev/reference/site-config
export default defineConfig({
  title: "sishui' blog",
  description: "A VitePress Blog",
  head: [
    ['link', { rel: 'icon',type:"image/png",href: '/favicon.png' }]
  ],
  themeConfig: {
    // https://vitepress.dev/reference/default-theme-config
    siteTitle:"sishui' blog",
    logo: '/favicon.png', 
    // 放置在public文件夹下直接用 经过vitepress处理 直接使用/开头
    nav: [
      { text: '关于', link: '/about' },
      {
        text: '文章',
        // link 目录 默认index.md
        items: [
          { text: "教程", link: "/articles/tutorials/" }
        ]
      }
    ],
    docFooter: {
      prev: "上一篇",
      next: "下一篇",
    },
    sidebar: [
      {
        text: '文章',
        items: [
          { text: '教程', link: '/tutorials' },
        ]
      }
    ],
    
    socialLinks: [
      { icon: 'github', link: 'https://github.com/inspiringforever' }
    ]
  }
})

```


## GithubPages

### GitHub
本地项目文件夹中新建 /.github/workflows/deploy.yml 文件
```yml
name: Deploy

on:
  push:
    branches:
      - main
      
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        # with:
        #   node-version: '16' 
      - run: npm install -g pnpm
      - run: pnpm install --frozen-lockfile

      - name: Build
        run: pnpm docs:build

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3 
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: docs/.vitepress/dist
```
这个执行action脚本执行后会创建一个gh-pages分支，
然后将dist文件夹中的内容推送到gh-pages分支

### 初始化Git 连接Github中创建的仓库
```sh
git init
git add . # 记得配置.gitignore文件
git commit -m "1"
git branch -M main
git remote add origin https://github.com/inspiringforever/VitePress-Blog.git 
git push -u origin main

