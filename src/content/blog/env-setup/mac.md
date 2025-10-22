---
title: 现代开发环境搭建指南（Mac）
description: '通过 Homebrew 快速搭建、管理系统环境，软件推荐'
publishDate: 2025-10-02 20:14:29
tags:
  - env
  - Mac
  - Homebrew
---

## 终端

### Homebrew

[Homebrew](https://brew.sh) 是 macOS 上的包管理器，用于安装和管理软件。

安装（官方推荐）：

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

| **常用命令**                   | **描述**                                       |
| ------------------------------ | ---------------------------------------------- |
| `brew install <包名>`          | 安装指定的包                                   |
| `brew uninstall <包名>`        | 卸载指定的包                                   |
| `brew update`                  | 更新 Homebrew 本身                             |
| `brew upgrade`                 | 升级所有已安装的包                             |
| `brew list`                    | 列出所有已安装的包                             |
| `brew search <包名>`           | 搜索可用的包                                   |
| `brew info <包名>`             | 获取指定包的详细信息                           |
| `brew doctor`                  | 检查系统环境是否存在问题                       |
| `brew cleanup`                 | 清理旧版本的包，释放空间                       |
| `brew outdated`                | 列出所有需要升级的包                           |
| `brew services list`           | 查看 Homebrew 服务的状态（例如后台运行的服务） |
| `brew services start <服务名>` | 启动指定服务                                   |
| `brew services stop <服务名>`  | 停止指定服务                                   |
| `brew tap <tap名>`             | 添加一个自定义 tap（源）                       |
| `brew untap <tap名>`           | 删除自定义 tap（源）                           |
| `brew switch <包名> <版本>`    | 切换已安装的包到指定版本（用于一些旧版本的包） |
| `brew help`                    | 显示帮助信息                                   |
| `brew versions <包名>`         | 查看包的历史版本（需要通过 tap 安装）          |

### iTerm

[iTerm2](https://iterm2.com/)

### oh-my-zsh

[oh-my-zsh](https://ohmyz.sh)

### 自定义指令

#### proxy

> proxy 用于在终端设置代理，提供科学加速
>
> unproxy 取消科学

```shell
#proxy
alias proxy='export http_proxy=http://127.0.0.1:7890;export https_proxy=http://127.0.0.1:7890;'

alias unproxy='unset all_proxy'
```

## Env

### Java

[sdkman](https://sdkman.io/)

jvm 相关依赖。javajdk、maven

```shell
# 使用官方安装脚本安装 sdkman
curl -s "https://get.sdkman.io" | bash
# 按提示重启 shell，或手动加载
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

### Node

[nvm](https://nvm.sh)

Node版本管理

```shell
# 安装 nvm
brew install nvm
```

### Go

[go](https://go.dev)

Go 语言开发环境。

```shell
brew install go
```

### Python

[pyenv](https://github.com/pyenv/pyenv)

切换 Python 环境，更多安装与配置见下方文档链接。

```shell
brew install pyenv
```

[UV](https://github.com/astral-sh/uv)

Python 包管理工具。

```shell
pip install uv
```

### Flutter

[fvm](https://fvm.app/)

Flutter 版本管理器

```shell
# Install FVM
brew tap leoafarias/fvm
brew install fvm
```

[Quick Start](https://fvm.app/documentation/getting-started)

### Docker

[Orbstack](https://orbstack.dev)

容器与虚拟化工具（Orbstack 为 macOS 上的替代方案）。

```shell
brew install orbstack
```

[Quick Start](https://docs.orbstack.dev/quick-start)

## 软件

### 柠檬清理

## 杂项

### 启动台图标大小调整

> （好了我们没有启动台了，完😩）

```shell
# 调整每一列显示图标数量，9表示每一列显示9个
defaults write com.apple.dock springboard-columns -int 9
# 调整多少行显示图标数量
defaults write com.apple.dock springboard-rows -int 6

```

恢复默认

```shell
defaults write com.apple.dock springboard-rows Default

defaults write com.apple.dock springboard-columns Default
```

调整完后重启

```shell
# 重置Launchpad
defaults write com.apple.dock ResetLaunchPad -bool TRUE
# 重启Dock
killall Dock
```
