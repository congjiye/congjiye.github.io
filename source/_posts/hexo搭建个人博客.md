---
title: Hexo + NexT + Github Pages搭建博客
date: 2023-09-24 13:50:47
tags: 
  - hexo
category: 工具
---

## 介绍

hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他标记语言）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

本文采用 Hexo + NexT + Github Pages 搭建个人博客。

<!-- more -->

## 前置条件

- 安装 NodeJS
- 安装 Git

## 安装 Hexo

确认[前置条件](#前置条件)已经全部满足后执行如下命令

```bash
npm install -g hexo-cli
hexo init <your-project-name>
cd <your-project-name>
pnpm i # 使用 npm install 可能会遇到 link 问题，建议直接使用 pnpm 安装依赖包
```

## 安装 NexT

进入先前创建的 hexo 目录中，执行如下命令

```bash
pnpm add hexo-theme-next@latest
```

修改根目录下的 `_config.yml` 文件，将 theme 修改为 next

```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next # 修改主题为 next
```

## 部署 Hexo

安装一键部署工具 `hexo-deployer-git`

```bash
pnpm add hexo-deployer-git
```

修改根目录下的 `_config.yml` 文件配置，增加一键部署配置

```yaml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git 
  repo: git@github.com:congjiye/username.github.io.git
  branch: main
```

运行如下命令即可直接部署 hexo 到个人博客中

```bash
hexo clean
hexo g
hexo s
```