# 第三方组件与许可声明

「轻跳」（`com.lightjump.adskip`）是基于开源项目二次开发的衍生应用，分发时遵循上游许可证要求，
在此列出主要第三方组件及其许可协议。

## 1. GKD（上游项目）

- 项目：gkd-kit/gkd — <https://github.com/gkd-kit/gkd>
- 说明：基于无障碍服务与高级选择器的自定义屏幕点击应用，是本应用的上游代码来源。
- 许可证：GNU General Public License v3.0（GPL-3.0）
- 说明：本应用为其衍生作品，因此同样以 GPL-3.0 授权分发，完整许可证文本见仓库根目录 [`LICENSE`](LICENSE)。

## 2. GKD 规则订阅（内置规则数据）

应用内置以下两套第三方订阅规则，作为数据文件随安装包分发（`assets/gkd.json5`、`assets/AIsouler_gkd.json5`）：

| 订阅 | 作者 / 仓库 | 内置版本 | 许可 |
| --- | --- | --- | --- |
| id667 的 GKD 订阅（👻Fork 版） | [Lin-arm/GKD_subscription](https://github.com/Lin-arm/GKD_subscription) | v595 | 仓库未附许可证文件，版权归原作者所有 |
| AIsouler 订阅 | [AIsouler/GKD_subscription](https://github.com/AIsouler/GKD_subscription) | v406 | 仓库未附许可证文件，版权归原作者所有 |

> 上述订阅仓库均未附带许可证文件，默认保留全部权利。本应用仅将其作为规则数据内置以便开箱即用。
> 若原作者对内置分发有异议，请在 Issues 中告知，我们会立即移除或改为在线订阅方式。

## 3. Shizuku

- 项目：RikkaApps/Shizuku — <https://github.com/RikkaApps/Shizuku>
- 说明：以 adb / root 权限直接调用系统 API 的工具，应用内以 `assets/shizuku.apk` 内置提供，便于用户安装。
- 许可证：Apache License 2.0

## 4. Public Suffix List

- 项目：Mozilla Public Suffix List — <https://publicsuffix.org/>
- 说明：随 `assets/PublicSuffixDatabase.list` 分发，用于域名处理。
- 许可证：Mozilla Public License 2.0（MPL-2.0）

## 5. 其他开源库

应用还使用了 AndroidX / Jetpack Compose、Kotlin 标准库与协程、OkHttp/Okio 等常见的开源库，
均按其各自许可证（Apache-2.0 / MIT / BSD 等）分发。这些组件的许可证文本可在其官方仓库中查阅。

---

如果你是本列表中某个项目的作者，并认为本仓库的分发方式不符合你的许可要求，
请在本仓库提交 Issue，我们会尽快调整。
