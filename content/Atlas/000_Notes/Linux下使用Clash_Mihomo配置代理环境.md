---
publish: true
created: 2026-08-22
modified: 2026-09-09T02:55:19.353Z
tags:
  - Linux
  - 网络环境
  - Clash
  - Mihomo
  - 代理
---

# Linux 下使用 Clash/Mihomo 配置代理环境

## 来源

<div data-auto-card-link-depth="-1" class="auto-card-link-container"><a href="https://github.com/nelvko/clash-for-linux-install?tab=readme-ov-file" class="auto-card-link-card external-link"><div class="auto-card-link-main"><div class="auto-card-link-title">GitHub - nelvko/clash-for-linux-install: 😼 优雅地使用基于 clash/mihomo 的代理环境</div><div class="auto-card-link-description">😼 优雅地使用基于 clash/mihomo 的代理环境. Contribute to nelvko/clash-for-linux-install development by creating an account on GitHub.</div><div class="auto-card-link-host"><span>github.com</span></div></div><img draggable="false" src="https://opengraph.githubassets.com/32b540ace82f7e290bd99ef34c99eaaeff2e6fa920cfde5c5683f1a26d1a39bb/nelvko/clash-for-linux-install" class="auto-card-link-thumbnail" /></a></div>

## 安装依赖

```shell
apt-get update
apt-get install -y net-tools
```

## 安装 clash-for-linux

```shell
git clone --branch master --depth 1 https://gh-proxy.org/https://github.com/nelvko/clash-for-linux-install.git \
  && cd clash-for-linux-install \
  && ./install.sh
```

## clashctl 常用命令

当前仓库使用统一的 `clashctl` 命令管理代理。先查看完整帮助：

```shell
clashctl -h
```

### 代理与状态

```shell
clashctl on              # 开启代理
clashctl off             # 关闭代理
clashctl status          # 查看内核状态
clashctl ui              # 查看 Web 面板地址
clashctl log             # 查看运行日志
```

### 订阅管理

```shell
clashctl sub add <订阅地址>   # 添加订阅
clashctl sub update          # 更新订阅
clashctl node                # 切换节点
```

### 其他管理命令

```shell
clashctl tun              # 管理 Tun 模式
clashctl mixin             # 管理 Mixin 配置
clashctl secret            # 查看或管理 Web 密钥
clashctl upgrade           # 升级代理内核
```

卸载时，在项目目录执行：

```shell
bash uninstall.sh
```

> [!note] 旧版本命令
> `clashsub` 和 `clashmixin` 是旧版本文档中出现的命令。当前 `master` README 推荐使用 `clashctl sub ...` 和 `clashctl mixin ...`；如果本机安装版本仍提供旧命令，应以 `clashctl -h` 或对应子命令的帮助输出为准。

## 配置订阅

```
clashsub add xxx(扭拟灯蛾订阅地址)
```

## 配置 Web 控制面板

在 VS Code 中转发本地 `9090` 端口，然后执行：

```shell
clashctl mixin
```

从输出中找到 `secret`，使用该密码登录：

```text
http://localhost:9090/ui
```

进入 Web 控制面板后即可进行代理配置。
