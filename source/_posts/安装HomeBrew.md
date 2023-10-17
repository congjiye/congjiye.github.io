---
title: 安装HomeBrew
date: 2023-09-26 23:26:06
tags: 
  - macos
category: 工具
---

## 前言

[HomeBrew](https://brew.sh) 是一个 mac 平台上的终端管理工具，用户可以通过使用 `brew` 命令来安装/管理 mac 平台上的各种软件。

<!-- more -->

## 安装

```bash
# 官网安装
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 国内安装
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

使用国内安装方式无需再做其他的换源操作，安装简单方便、实用。

## 卸载

```bash
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/HomebrewUninstall.sh)"
```

## 常见命令

```shell
Example usage:
  brew search TEXT|/REGEX/
  brew info [FORMULA|CASK...]
  brew install FORMULA|CASK...
  brew update
  brew upgrade [FORMULA|CASK...]
  brew uninstall FORMULA|CASK...
  brew list [FORMULA|CASK...]

Troubleshooting:
  brew config
  brew doctor
  brew install --verbose --debug FORMULA|CASK

Contributing:
  brew create URL [--no-fetch]
  brew edit [FORMULA|CASK...]

Further help:
  brew commands
  brew help [COMMAND]
  man brew
  https://docs.brew.sh
```
