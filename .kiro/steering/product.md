# 产品概述

## 项目名称
NekoBox for Android (NB4A)

## 产品定位
基于 sing-box 的 Android 通用代理工具链，提供多协议代理支持的开源 VPN 应用。

## 核心功能
- 支持多种代理协议（Shadowsocks、VMess、Trojan、VLESS、Hysteria、WireGuard 等）
- 订阅管理（支持多种订阅格式）
- 分应用代理
- 路由规则配置
- 内置 Web 控制面板（Yacd-meta）
- 流量统计和监控

## 目标用户
需要在 Android 设备上使用代理服务的用户

## 技术特点
- 使用 sing-box 作为核心代理引擎
- Go 语言编写的核心库（libcore）
- Kotlin/Java 编写的 Android UI 层
- 最低支持 Android API 21 (Android 5.0)

## 包名
`moe.nb4a`

## 版本信息
版本号在 `nb4a.properties` 文件中维护
