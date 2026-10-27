# 我的博客（Astro + Fuwari）

照着 [coldflame324.github.io](https://coldflame324.github.io/) 的样子搭的个人博客：
主页 / 归档 / 友链 / 留言板 / 关于，RSS、站点地图、分类和标签都有，纯静态，可以直接丢到 GitHub Pages 上。

## 本地跑起来

```bash
cd blog
npm install      # 第一次需要，已经装好就不用管
npm run dev      # 打开 http://localhost:4321 预览
```

改完东西按 `Ctrl+C` 停掉，再 `npm run build` 确认能构建成功。

## 常改的地方

| 想改什么 | 改哪个文件 |
| --- | --- |
| 站名、副标题、头像、导航栏、社交链接、主题色 | `src/config.ts` |
| 关于页 | `src/content/spec/about.md` |
| 友链列表 | `src/pages/friends.astro` 顶部的 `friends` 数组 |
| 留言板 | `src/pages/guestbook.astro`（默认 giscus，按页面里的步骤填 4 个变量） |
| 文章 | `src/content/posts/*.md` |
| 首页横幅图、头像图 | `src/assets/images/` |

### 写一篇新文章

```bash
npm run new-post -- "文章标题"
```

或者直接在 `src/content/posts/` 新建 `xxx.md`：

```markdown
---
title: 文章标题
published: 2026-10-27
description: 一句话摘要，会显示在列表和搜索结果里
tags: [标签1, 标签2]
category: 分类名
draft: false
---

正文……
```

可以用的排版：标题、列表、引用、表格、代码块（带复制按钮）、`$公式$`、图片灯箱、
`::github{repo="owner/repo"}` GitHub 卡片、`:::note` / `:::tip` / `:::warning` 提示块。
现有两篇示例文章可以照着改，改完把 `reading-note-demo.md` 删掉即可。

## 发到 GitHub Pages

1. 在 GitHub 上建仓库。**想要 `https://你的用户名.github.io` 这种地址，仓库名必须叫 `你的用户名.github.io`**；
   别的名字也行，只是地址变成 `https://你的用户名.github.io/仓库名`。
2. 把 `blog` 目录里的东西推到仓库的 `main` 分支。
3. 仓库 Settings → Pages → Build and deployment → Source 选 **GitHub Actions**。
4. 推送后 `.github/workflows/deploy.yml` 会自动构建部署，几分钟后就能访问。

如果是第二种（项目站点），把 `.github/workflows/deploy.yml` 里的 `BASE_PATH: /` 改成 `BASE_PATH: /仓库名`。

> 仓库里有 `.gitignore`，`node_modules` 和 `dist` 不会被提交，放心。

## 目录速览

```
blog/
├─ src/
│  ├─ config.ts            站点配置（改这里最多）
│  ├─ content/posts/       文章
│  ├─ content/spec/        关于页
│  ├─ pages/               页面（归档、友链、留言板…）
│  ├─ components/          组件
│  └─ i18n/                多语言文案（已含简中）
├─ public/                 静态资源
├─ .github/workflows/      自动部署
└─ astro.config.mjs        站点地址、base 路径、插件
```

## 备注

- 主题是 [Fuwari](https://github.com/saicaca/fuwari)（MIT），字体和图标都随包自带，不需要联网。
- 站内搜索用 Pagefind，`npm run build` 时会一起生成索引。
- 想换配色：`src/config.ts` 里的 `themeColor.hue`（0 红 / 200 青 / 250 蓝 / 345 粉）。
