---
title: MacOS安装NVM
date: 2023-09-26 23:33:38
tags: 
  - macos
category: 工具
---

## 前言

node 版本管理器，也就是说：一个 nvm 可以管理多个 node 版本（包含 npm 与 npx），可以方便快捷的 安装、切换不同版本的 node。

<!-- more -->

## 下载 NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

## 配置 NVM

在 `.bash_profile` 中添加如下配置

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

在 `.zshrc` 文件中添加如下配置

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

配置 `nvm` 镜像地址为淘宝镜像

```bash
export NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node/
export NVM_IOJS_ORG_MIRROR=http://npm.taobao.org/mirrors/iojs
```

执行如下命令让配置生效

```bash
source ~/.bash_profile
souece ~/.zshrc
```

## 验证安装

执行如下命令查看是否成功安装 `nvm`

```bash
➜  ~ nvm -v
```
