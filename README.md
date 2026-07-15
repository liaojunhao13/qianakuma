# 张雨茜的学习实验室

基于 [Astro](https://astro.build/) 与 [CuteLeaf/Firefly](https://github.com/CuteLeaf/Firefly) 的个人技术学习博客。

- 域名：<https://qianakuma.xyz>
- 方向：CUDA / 深度学习 / 多相流仿真 / LLM Agent / 量化系统
- 内容：长期学习记录、项目实践和研究整理

## 环境要求

- Node.js >= 22
- pnpm >= 9

检查本机版本：

```bash
node --version
pnpm --version
```

## 本地运行

```bash
pnpm install
pnpm dev
```

开发服务器默认运行在 <http://localhost:4321>。

构建并预览生产版本：

```bash
pnpm build
pnpm preview
```

构建产物位于 `dist/`。

## 新增文章

文章存放在 `src/content/posts/`，支持 Markdown 和 MDX。可以手动新建文件，也可以使用主题脚本：

```bash
pnpm new-post cuda-new-note
```

基础 frontmatter 示例：

```yaml
---
title: "文章标题"
published: 2026-07-14
description: "文章摘要"
image: "api"
tags: ["CUDA", "GEMM"]
category: "CUDA学习之路"
draft: false
---
```

写作流程：

1. 在 `src/content/posts/` 新建 `.md` 或 `.mdx` 文件。
2. 填写 frontmatter，并用中文编写正文。
3. 运行 `pnpm dev` 本地预览。
4. 执行 `git add`、`git commit` 和 `git push`。
5. Cloudflare Pages 在推送后自动构建部署。

## 主要配置

- `src/config/siteConfig.ts`：站点标题、域名、主题色、页面开关和文章布局
- `src/config/profileConfig.ts`：头像、作者简介和个人链接
- `src/config/navBarConfig.ts`：顶部导航
- `src/config/backgroundWallpaper.ts`：本地背景图和壁纸显示模式
- `src/content/spec/about.md`：关于页面

头像和背景图位于 `public/images/`。

## Cloudflare Pages 部署

先将本项目推送到你自己的 GitHub 仓库，再在 Cloudflare Pages 中连接该仓库：

| 配置项 | 值 |
| --- | --- |
| Framework preset | Astro |
| Build command | `pnpm run build` |
| Install command | `pnpm install` |
| Build output directory | `dist` |
| Production branch | `master` |

在 Cloudflare Pages 项目的 Custom domains 中添加 `qianakuma.xyz`。如果域名已托管在同一个 Cloudflare 账号，平台会自动创建所需 DNS 记录；否则按页面提示添加 CNAME 记录。

## GitHub 首次推送

当前项目来自 Firefly 官方仓库。先在 GitHub 创建自己的空仓库，然后替换远程地址：

```bash
git remote rename origin upstream
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin master
```

后续需要同步 Firefly 更新时，可以从 `upstream` 获取，但合并前应先备份并检查配置差异。

## 致谢与许可

本站基于 [Firefly](https://github.com/CuteLeaf/Firefly) 与 [Fuwari](https://github.com/saicaca/fuwari) 构建。仓库主许可详见 `LICENSE`；Firefly 与 Fuwari 的 MIT License 和原始版权声明保留在 `LICENSE-FIREFLY`。
