---
title: MacOS安装NVM
date: 2023-09-26 23:33:38
tags: macos
category: 工具
---

# MacOS 安装 NVM

## 下载 NVM

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

## 配置 NVM

在 `.bash_profile` 中添加如下配置

```shell
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

在 `.zshrc` 文件中添加如下配置

```shell
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

配置 `nvm` 镜像地址为淘宝镜像

```shell
export NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node/
export NVM_IOJS_ORG_MIRROR=http://npm.taobao.org/mirrors/iojs
```

执行如下命令让配置生效

```shell
source ~/.bash_profile
souece ~/.zshrc
```

## 验证安装

执行如下命令查看是否成功安装 `nvm`

```shell
➜  ~ nvm -v
```
