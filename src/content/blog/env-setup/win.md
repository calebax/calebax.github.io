---
title: 现代开发环境搭建指南（Windows）
description: '通过 Scoop 快速搭建、管理系统环境，软件推荐'
publishDate: 2023-3-25 22:58:29
updatedDate: 2025-9-30 00:35:29
tags:
  - env
  - Windows
  - Scoop
---

> **目标**
>
> 1. 使用 **Scoop** 高效管理 Windows 开发软件；
> 2. 5 分钟内搭建开发环境；

---

## 一、Scoop：Windows 的命令行包管理神器

> **Scoop** 是 Windows 的命令行安装程序，支持搜索、下载、安装、更新、卸载等一站式管理。

[Scoop GitHub 地址](https://github.com/ScoopInstaller/Scoop)

### Scoop 的优势

- 一行命令即可安装任意软件；
- 防止污染 PATH 环境变量；
- 自动解决并安装依赖项；
- 特别适合开发者配置环境；
- ......

---

## 二、安装 Scoop

### 1. 允许 PowerShell 执行脚本

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 2. 下载安装程序

```powershell
irm get.scoop.sh -outfile 'install.ps1'
```

### 3. 自定义目录安装

```powershell
.\install.ps1 -ScoopDir 'D:\Environment\Scoop' -ScoopGlobalDir 'D:\Environment\Scoop\GlobalApps'
```

### 验证安装

```powershell
scoop help
```

---

## 三、进阶配置

### 1. 配置代理

```powershell
# clash 默认端口 7890
scoop config proxy localhost:7890

# 恢复系统代理
scoop config rm proxy
```

### 2. 添加 bucket 仓库

```powershell
scoop bucket add extras
scoop bucket add java
scoop bucket add versions
scoop bucket add <bucket-name> [<git-repo-url>]
```

### 3. 启用 Aria2 多线程加速

```powershell
scoop install aria2
```

---

## 四、常用命令

### 软件管理

```powershell
scoop search <app>
scoop install (-g) <app>
scoop update
scoop update <app>
scoop update *
scoop uninstall <app>
```

### 版本切换

```powershell
scoop reset <app>
```

### 清理缓存

```powershell
scoop cache show
scoop cache rm *
```

---

## 六、实战篇：5分钟搭建现代开发环境

> 现在我们用 Scoop 安装所有主流开发工具：Git、JDK、Node（NVM）与 Maven。

### 安装 Git

```powershell
scoop install -g git
git --version
```

### 安装 JDK

```powershell
scoop bucket add java
scoop search jdk
scoop install -g openjdk8-redhat
scoop install -g openjdk17
java -version
scoop reset openjdk17
```

### 安装 NVM / Node.js

```powershell
scoop install -g nvm
nvm list available
nvm install 18.15.0
node -v
npm -v
```

### 安装 Maven

```powershell
scoop install -g maven
mvn -v
```

---

## 七、总结与扩展阅读

现在你已经拥有一个完整的现代开发环境：

| 工具          | 作用              | 验证命令        |
| ------------- | ----------------- | --------------- |
| Git           | 版本控制          | `git --version` |
| JDK           | Java 开发环境     | `java -version` |
| Node.js / NVM | JS 运行与版本管理 | `node -v`       |
| Maven         | Java 构建工具     | `mvn -v`        |

📚 推荐阅读：

- [配置 Git 用户信息与 SSH](./git.md)
- [了解 NVM 的版本切换与 Node 工具链优化](./nvm.md)
- [配置 Maven 镜像与依赖仓库](./maven.md)

---
