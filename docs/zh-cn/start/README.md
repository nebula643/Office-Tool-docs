# 欢迎使用 Office Tool Plus

## 介绍

Office Tool Plus 是一个强大且实用的 Office 部署工具。

Office Tool Plus 基于 [Office 部署工具](https://aka.ms/ODT)和 [OSPP](https://docs.microsoft.com/en-us/DeployOffice/vlactivation/tools-to-manage-volume-activation-of-office) 制作，可以很方便的部署 Office，其内置迅雷引擎可帮助您更快地下载 Office，当然，你也可以使用 Office Tool Plus 内置的各种小工具或者功能快捷、方便地激活和管理 Office 哦！

支持下列产品：

- Microsoft 365
- Office 2016, 2019, 2021
- Visio 2016, 2019, 2021 & Online Plan 2
- Project 2016, 2019, 2021 & Online Desktop Client

无论你是个体还是团队，Office Tool Plus 都是你的得力小助手。

## 功能

- 创建 Office 安装配置，支持导出到本地、从本地或网络位置导入。
- 下载 Office，支持所有通道的 Office，支持所有的 Office 语言。
- 安装 Office，支持对现有的 Office 进行修改，包括新增产品和应用程序，卸载产品或应用程序。
- 创建 Office ISO，支持默认安装配置、静默安装配置。
- 激活 Office，支持在线激活、电话激活、KMS 激活
- 支持 Office 授权管理，包括许可证管理，密钥管理以及 KMS 管理。
- 修改 Office 更新通道，支持在不重装 Office 的情况下升级/降级 Office.
- 移除 Office，在 Office 无法正常卸载的情况下强制移除 Office，支持 Office 2003 - Office 最新版本。
- 内置 Office 工具箱，包括重置设置，修复模板问题，修复激活问题等。
- 转换 Office 文档，基于 Office COM，稳定可靠。
- 自定义主题，打造你自己的专属 Office Tool Plus.
- 高级设置允许你使用更高级的功能，例如 Office 的内部通道。

::: warning 注意事项

1. Office 文档转换功能可能无法兼容 64 位版本的 Office.
2. Office Tool Plus 只提供激活管理功能，你需要拥有正版许可才可以激活你的 Office.

:::

::: details 关于零售、批量互转
Office 许可证能够共存，而不只是零售版或者批量版本

在零售版的基础上再安装批量版许可证，并且将其都激活，Office 将会同时显示零售版激活信息和批量版激活信息。
:::

## 组件与结构

``` txt
Office Tool
├── Office Tool Plus.exe (主程序)
├── Office Tool Plus.Console.exe (终端助手)
├── hostfxr.dll (.NET Host)
├── shared (.NET Runtimes)
└── files
    ├── setup.exe (微软 Office 部署工具)
    ├── activate (包含 OSPP 以及相关文件)
    │   └── OSPP.VBS (Office Software Protection Platform)
    ├── clean
    │   ├── x64 (64 位系统专用 Office 激活信息清除工具)
    │   └── x86 (32 位系统专用 Office 激活信息清除工具)
    ├── preferences (Office 应用程序首选项数据，由微软提供)
    └── Thunder (迅雷云加速开放平台相关文件)
```

通常情况下，Office Tool Plus 会自动下载缺失的组件并自动保持其为最新版本。如果某些组件丢失或者无法自动下载，建议重新下载 Office Tool Plus 以解决问题。
