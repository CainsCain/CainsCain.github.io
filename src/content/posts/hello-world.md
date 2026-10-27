---
title: 你好，世界
published: 2026-10-27
description: 站点搭好了，先写一篇开张文章。
tags: [随笔, 建站]
category: 随笔
draft: false
---

这里是我的新博客。

以前写的东西散在各种地方，现在想找个固定的角落把它们收起来：游戏笔记、读书笔记，还有一些当时想不明白、事后回看还挺有意思的问题。

## 这个站是怎么搭的

用 [Astro](https://astro.build/) 加 [Fuwari](https://github.com/saicaca/fuwari) 主题，纯静态，托管在 GitHub Pages 上，不花一分钱。

写文章就是在 `src/content/posts/` 下新建一个 Markdown 文件，`git push` 之后自动构建发布。

```bash
npm run new-post -- "文章标题"
npm run dev     # 本地预览 http://localhost:4321
npm run build   # 构建到 dist/
```

## 之后想写点什么

- 打完游戏之后那些没处说的感想
- 读完书想记住的句子
- 一些技术上的踩坑记录

慢慢来吧。
