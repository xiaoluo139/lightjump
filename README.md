# 轻跳 LightJump

「轻跳」是基于 [GKD](https://github.com/gkd-kit/gkd) 二次开发的极简版安卓自动跳过工具：
通过系统无障碍服务识别界面上的「跳过 / 关闭」按钮并自动点击，用来跳过 App 启动时的开屏广告，
以及各种更新提示、评价提示、通知权限弹窗。

本仓库是「轻跳」的**安装包发布仓库**，提供 APK 下载、版本信息、文件校验值和第三方组件说明。

![Android 8.0+](https://img.shields.io/badge/Android-8.0%2B-3DDC84?logo=android&logoColor=white)
![License GPL-3.0](https://img.shields.io/badge/license-GPL--3.0-blue)
![Latest release](https://img.shields.io/github/v/release/xiaoluo139/lightjump?label=release)

## 下载安装包

| 文件 | 版本 | 大小 | 说明 |
| --- | --- | --- | --- |
| [`packages/LightJump-v1.7.0.apk`](packages/LightJump-v1.7.0.apk) | 1.7.0（versionCode 9） | 5.90 MiB | 最新版本 |
| [Releases 页面](https://github.com/xiaoluo139/lightjump/releases) | — | — | 全部历史版本安装包 |

在手机上直接点击下载即可。也可以在 [Releases](https://github.com/xiaoluo139/lightjump/releases)
页面按版本下载，或扫描页面上的二维码分享给其他人。

### 版本信息

| 项目 | 值 |
| --- | --- |
| 应用名 | 轻跳 |
| 包名 | `com.lightjump.adskip` |
| 当前版本 | 1.7.0（versionCode 9） |
| 最低系统 | Android 8.0（API 26） |
| 目标系统 | API 37 |
| CPU 架构 | arm64-v8a、x86_64（通用包，绝大多数手机可用） |
| 签名 | Android 调试证书（自签名） |

### 历史版本

历史安装包发布在 [Releases](https://github.com/xiaoluo139/lightjump/releases) 页面。

| 版本 | versionCode | 大小 | SHA-256 |
| --- | --- | --- | --- |
| 1.7.0 | 9 | 5.90 MiB | `99c56977135fb59a875e77eb9917bbd7e598b67a36ad2256df8278604de95efd` |
| 1.6.0 | 8 | 5.91 MiB | `0a46c87734537b49097c43e2cc4b12c1897ec1d6676bce890a97566c1dc5b4ef` |
| 1.3.0 | 5 | 5.90 MiB | `14e69ae9e462fb279171635e081ef7206deecba58cc0e9b58c438cb205d05365` |
| 1.1.1 | 3 | 4.22 MiB | `99c77aa90439eb13bf26a6b0b64f68fa02a6639149ed62e7a91377b6ab9208ff` |

## 它是什么

Android 不允许普通应用直接点击别的应用，所以「轻跳」需要借助系统的**无障碍服务**来读取屏幕内容，
再根据内置的订阅规则判断「这个按钮是不是跳过按钮」，最后代替你点一下。

「轻跳」把 GKD 的完整功能裁剪成了一条最短路径：安装后按引导做三步设置就能用，
不需要理解规则语法，也不需要自己订阅规则。

## 功能特性

- **一键配置向导**：一键开启基础无障碍、一键安装内置 Shizuku、一键解除系统限制、一键授权。
- **内置两套订阅规则**：GKD 订阅 `v595` 与 AIsouler 订阅 `v406`，安装后默认全部启用，开箱即用。
- **多种提权方式**：无障碍（基础）、Shizuku 增强模式、无线调试 ADB、Root、外部授权器，按设备情况任选其一。
- **触发记录与事件日志**：能看到每条规则在什么时间、对哪个应用、点击了什么。
- **规则管理**：按应用 / 规则组单独开关，支持为指定应用添加或编辑规则。
- **备份与恢复**：导出、导入个人开关配置，换机不丢设置。
- **外观**：主题色、深色模式跟随系统。
- **无广告、无账号、无后台服务**，不联网也能跳过广告（联网仅用于下载规则和检查更新）。

## 安装与首次配置

1. 下载并安装 `LightJump-v1.7.0.apk`。首次安装需要允许「安装未知来源应用」。
2. 打开「轻跳」，按首页引导依次完成：
   - **开启无障碍服务**：系统设置 → 无障碍 → 已安装的应用 → 轻跳 → 开启。
   - **（可选，推荐）Shizuku 增强模式**：点击「一键安装内置 Shizuku」，装好后在 Shizuku 里启动服务，
     再回到「轻跳」点击「一键授权」。
   - **（可选）解除后台限制**：点击「一键去解除系统限制 / 允许忽略电池优化」，避免被系统杀后台。
3. 在应用列表里确认要启用规则的应用，保持开关为打开状态。
4. 打开任意有开屏广告的 App 验证效果；在「事件日志」里可以看到命中记录。

> 部分机型（MIUI / HyperOS、HarmonyOS、ColorOS 等）会限制无障碍或后台运行，按应用内提示的
> 「一键去开启无障碍」「一键去解除限制」操作即可；若仍无效，可在本仓库提 Issue。

## 权限说明

| 权限 | 用途 |
| --- | --- |
| 无障碍服务（BIND_ACCESSIBILITY_SERVICE） | 核心功能：读取屏幕节点并执行点击 |
| 悬浮窗（SYSTEM_ALERT_WINDOW） | 显示控制面板 / 提示 |
| 读取已安装应用（QUERY_ALL_PACKAGES、GET_INSTALLED_APPS） | 匹配当前打开的应用，决定用哪套规则 |
| 前台服务（FOREGROUND_SERVICE 及相关子类型） | 保证无障碍服务与规则引擎常驻运行 |
| 通知（POST_NOTIFICATIONS） | 前台服务状态提示、无线调试配对码输入 |
| 修改安全设置（WRITE_SECURE_SETTINGS） | 授权后可在无障碍服务被系统关闭时自动重新开启 |
| 忽略电池优化、修改 WiFi 状态、本地网络 | 后台保活、自动发现局域网内的无线调试服务 |
| 安装应用（REQUEST_INSTALL_PACKAGES） | 安装内置 Shizuku、应用内更新 |
| 读写存储 | 导入 / 导出规则与备份文件 |
| 网络（INTERNET、ACCESS_NETWORK_STATE） | 下载订阅规则、检查更新 |

所有规则匹配、点击记录都在本机完成。只有你主动使用「上传分享」时，快照与截图才会被上传。

## 校验安装包

`packages/SHA256SUMS.txt` 中记录了每个安装包的 SHA-256 校验值。

```bash
# Linux / macOS
sha256sum -c SHA256SUMS.txt

# Windows PowerShell
Get-FileHash *.apk -Algorithm SHA256
```

当前最新版本：

```
99c56977135fb59a875e77eb9917bbd7e598b67a36ad2256df8278604de95efd  LightJump-v1.7.0.apk
```

## 常见问题

**装不上、覆盖安装失败？**
安装包使用 Android 调试证书签名。如果手机上已装过来自其他渠道的同名应用（包名相同但签名不同），
需要先卸载旧版本再安装。卸载会清除已保存的规则开关配置，建议先备份。

**提示「无障碍服务已被限制」「特殊用途的前台服务已被限制」？**
这是系统层面的限制。按应用内「一键去解除限制」的指引操作，或在系统设置中允许该应用后台运行。

**和官方 GKD 冲突吗？**
不冲突，包名不同，可以同时安装。两者会同时响应无障碍事件，建议只保留其中一个启用。

**能完全替代 GKD 吗？**
不能。「轻跳」只保留了跳过广告这条主路径，高级选择器调试、订阅编辑、快照对比等能力请使用官方 GKD。

**会不会收集隐私？**
规则匹配与日志都在本机处理，应用不申请任何账号，也不上传数据。「上传分享」（分享规则快照到图床）
需要你手动触发，上传前请自行确认截图与节点数据不含隐私信息。

## 关于源码

「轻跳」是基于 [GKD](https://github.com/gkd-kit/gkd) 的二次开发版本，按 GPL-3.0 授权。
GPL-3.0 要求在分发安装包时向接收者提供完整的对应源码，对应源码整理完成后会在此仓库公开。

在源码公开之前，如果需要获取对应源码，请在本仓库提 Issue 说明，作者会提供获取方式。

## 许可与致谢

- 本项目基于 [gkd-kit/gkd](https://github.com/gkd-kit/gkd) 二次开发，遵循 **GPL-3.0** 授权，详见 [LICENSE](LICENSE)。
- 内置规则订阅来自 [Lin-arm/GKD_subscription](https://github.com/Lin-arm/GKD_subscription)（👻Fork 版，id667 v595）
  与 [AIsouler/GKD_subscription](https://github.com/AIsouler/GKD_subscription)（v406）。
- 内置 [Shizuku](https://github.com/RikkaApps/Shizuku)（Apache-2.0）用于免 Root 提权。

第三方组件的详细版权与许可信息见 [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)。

## 免责声明

本应用仅用于减少广告干扰、提升个人使用体验。使用者应遵守所在地区的法律法规与相关应用的服务条款，
因使用本应用产生的一切后果由使用者自行承担。请勿将本应用用于任何商业用途或非法用途。
