# 应用程序命令

命令不区分大小写，按照输入顺序执行。如果路径中含有空格，请使用 "" (英文双引号) 将路径包括起来。

## 程序内命令

这些命令只能在命令框中使用。

![Command box](/docs/assets/img/zh-cn/command-box.png)

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /setImage *value* | 设置背景图 | *value*: 路径，支持 BMP, PNG 或 JPG。<br>支持本地以及 HTTP 路径。 |
| /getKey *value* | 获取产品默认密钥 | *value*: 产品 ID. |
| /getBWP | 获取今日必应壁纸 |  |
| /resetNotif | 重置通知，以便再次显示已经关闭了的通知 | |
| /loadConfig *value* | 从 Web 路径加载 XML 配置文件 | *value*: 网址 |

## 程序命令

这些命令只能够从命令行中执行。

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /isoInstall | 读取 ISO 配置文件并启动安装程序。 | 你必须创建 Office ISO，确保 ISO 内含 ConfigForISO.xml，挂载后再执行命令 |
| /loadConfig *value* | 读取 XML 配置文件并启动安装程序。 | *value*: XML 文件路径 |
| /sourcePath *value* | 覆写 XML 配置文件中的源路径属性，该命令需配合 `/loadConfig` 命令使用 |
| /clientEdition *value* | 覆写 XML 配置文件中的体系结构属性，*value*: 32 或 64，该命令需配合 `/loadConfig` 命令使用 |
| /enableHWAcc *value* | 启用硬件加速 | *value*: *true* 或 *false*，默认为 *true* |

## 部署命令

这些命令可以在命令行和命令框中使用。

deploy *[options]*

使用部署命令时，你需要指定为 deploy，然后再写参数，例如以下是一条简单的部署命令：

``` batch
deploy /addProduct O365ProPlusRetail
```

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /addProduct *values[]* | 添加产品 | values: productID_language_excludeApps_MAK<br><br>**其中 productID 为必需参数。**<br>详细使用方法见下面的部署示例。 |
| /removeProduct *values[]* | 卸载产品 | values: productID_language<br><br>使用方法同 /addProduct |
| /removeAll | 卸载全部产品 |  |
| /channel *value* | 设置通道 | *value*: 通道 ID，默认值为 *Current*，[更多信息](/zh-cn/deploy/basic-settings.html#通道) |
| /clientEdition *value* | 设置体系结构 | *value*: 32 或 64，默认值为 32。 |
| /migrateArch | 迁移体系结构 |  |
| /version *value* | 设置 Office 版本号 | *value*: Office 版本号。 |
| /sourcePath *value* | 设置源路径属性 | *value*: 路径，支持本地、SMB 路径。 |
| /display *value* | 设置是否显示 Office 安装界面 | *value*: true 显示，false 隐藏，默认值为 *true* |
| /acceptEULA | 代表用户接受许可条款 |  |
| /module *value* | 设置安装模块 | *value*: 0 或 1，默认值是 0<br>0: Office 部署工具，1: Office Tool Plus. |
| /downloadFirst | 设置下载后安装 |  |
| /createShortcuts | 创建桌面快捷方式 |  |

::: warning 注意
/display 和 /acceptEULA 参数仅在 V9 版本中可用。
:::

### 部署 Office 示例

在计算机上部署简体中文版的 Office 2021 专业增强版 - 批量版，排除 Access, Outlook, OneNote:

``` batch
deploy /addProduct ProPlus2021Volume_zh-cn_Access,Outlook,OneNote /channel PerpetualVL2021
```

使用本地源部署 Office，你需要设置 `/sourcePath` 和 `/version` 参数。如果你需要安装 64 位的 Office，你还需要设置 `/clientEdition`。

``` batch
deploy /addProduct O365ProPlusRetail_en-us_Access,Outlook,OneNote /clientEdition 64 /sourcePath "D:\Test\Office Tool" /version 16.0.xxxxx.xxxxx
```

如果你需要为批量产品设置 MAK，你可以使用以下命令：

``` batch
deploy /addProduct ProPlus2021Volume_zh-cn_Access,Outlook,OneNote_XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /channel PerpetualVL2021
```

如果你需要忽略某个参数，可以将其置空。例如不设置语言（不建议这样做）：

``` batch
deploy /addProduct ProPlus2021Volume__Access,Outlook,OneNote /channel PerpetualVL2021
```

指定多个应用程序或语言时，你需要使用「英文逗号」将其隔开，例如 Access,Lync 或 zh-cn,en-us。

如果需要添加多个产品，请指定多个 addProduct 参数。

如果需要添加语言包或者校对工具，请使用 **LanguagePack** 或 **ProofingTools** 作为产品 ID.

## OSPP 命令

ospp *[options]*

使用 OSPP 命令时，你需要指定为 OSPP，然后再写参数，例如以下是一条简单的激活命令：

``` batch
ospp /insLicID ProPlus2021Volume /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /act
```

| 命令 | 说明 | 使用方法 |
| :-- | :-- | :-- |
| /insLicID *value* | 安装指定产品的 Office 许可证 | /insLicID ProPlus2021Volume |
| /inpkey:*value* | 安装指定的 Office 密钥 | /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX |
| /unpkey:*value* | 卸载指定的 Office 密钥 | /unpkey:XXXXX |
| /sethst:*value* | 设置 KMS 主机地址 | /sethst:kms.example.com |
| /setprt:*value* | 设置 KMS 主机端口，默认值: 1688 | /setprt:1688 |
| /act | 激活 Office 客户端产品 | /act |

有关 OSPP 的更多命令请查看[微软官方文档](https://docs.microsoft.com/zh-cn/deployoffice/vlactivation/tools-to-manage-volume-activation-of-office)。

## Office Tool Plus Console Helper

Office Tool Plus.Console 是一个命令行程序，默认情况下，通过 Office Tool Plus 执行命令时，CMD 将会立即返回，不会等待 Office Tool Plus 退出。通过 Office Tool Plus.Console 执行命令时，CMD 将会等待程序退出，并且支持输出程序日志。

以下命令示例启动 Office Tool Plus 日志输出：

``` batch
"Office Tool Plus.Console" /enableLog
```

::: tip 提示
deploy 和 ospp 命令默认启用日志输出，您无需额外指定 /enableLog 参数。deploy 和 ospp 命令不可以和其他命令混用，否则会无法识别。
:::

如果你需要使用 *deploy* 或者 *ospp* 命令，像这样用即可：

``` batch
"Office Tool Plus.Console" deploy /addProduct ...
```

您可以先执行 *deploy* 命令，然后执行 *ospp* 命令，以便达到自动安装以及激活的效果。

### Batch 文件

如果你需要使用 BAT 文件运行 "Office Tool Plus.Console"，请确保你有管理员权限执行这个脚本。

以下是一个模板：

``` batch
@echo off
title Office Tool Plus - Console

:: Change the working directory to current directory.
:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" /isoInstall
"Office Tool Plus.Console" ospp /insLicID ProPlus2021Volume /sethst:kms.example.com /setprt:1688 /act
```
