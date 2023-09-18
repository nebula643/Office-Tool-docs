# 部署命令

这些命令可以在命令行和命令框中使用，命令不区分大小写。如果命令参数中含有空格，请使用 "" (英文双引号) 将其包括起来。

deploy *[options]*

使用部署命令时，你需要指定为 deploy，然后再写参数，例如以下是一条简单的部署命令：

``` batch
deploy /addProduct O365ProPlusRetail
```

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /addProduct *values[]* | 添加产品 | values: productID_language_excludeApps_MAK，**其中 productID 为必需参数**。使用方法见[部署示例](deploy.md#部署-office-示例)。 |
| /removeProduct *values[]* | 卸载产品 | values: productID_language，使用方法同 /addProduct |
| /removeAll | 卸载全部产品 |  |
| /channel *value* | 设置通道 | *value*: 通道 ID，默认值为 *Current*，[更多信息](/zh-cn/deploy/settings/basic.md#更新通道) |
| /clientEdition *value* | 设置体系结构 | *value*: 32 或 64，默认值为 32。 |
| /migrateArch | 迁移体系结构 |  |
| /version *value* | 设置 Office 版本号 | *value*: Office 版本号。 |
| /sourcePath *value* | 设置源路径属性 | *value*: 路径，支持本地、SMB 路径。 |
| /display *value* | 设置是否显示 Office 安装界面 | *value*: true 显示，false 隐藏，默认值为 *true* |
| /acceptEULA | 代表用户接受许可条款 |  |
| /module *value* | 设置安装模块 | *value*: 0: Office 部署工具，1: Office Tool Plus。默认值为 0 |
| /downloadFirst | 设置下载后安装 |  |
| /createShortcuts | 创建桌面快捷方式 |  |

## 部署 Office 示例

在计算机上部署简体中文版的 Office 2021 专业增强版 - 批量版，排除 Access, Outlook, OneNote:

``` batch
deploy /addProduct ProPlus2021Volume_zh-tw_Access,Outlook,OneNote /channel PerpetualVL2021
```

使用本地源部署 Office，你需要设置 `/sourcePath` 和 `/version` 参数。如果你需要安装 64 位的 Office，你还需要设置 `/clientEdition`。

``` batch
deploy /addProduct O365ProPlusRetail_en-us_Access,Outlook,OneNote /clientEdition 64 /sourcePath "D:\Test\Office Tool" /version 16.0.xxxxx.xxxxx
```

如果你需要为批量产品设置 MAK，你可以使用以下命令：

``` batch
deploy /addProduct ProPlus2021Volume_zh-tw_Access,Outlook,OneNote_XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /channel PerpetualVL2021
```

如果你需要忽略某个参数，可以将其置空。例如不设置语言（不建议这样做）：

``` batch
deploy /addProduct ProPlus2021Volume__Access,Outlook,OneNote /channel PerpetualVL2021
```

指定多个应用程序或语言时，你需要使用「英文逗号」将其隔开，例如 Access,Lync 或 zh-tw,en-us。

如果需要添加多个产品，请指定多个 addProduct 参数。

如果需要添加语言包或者校对工具，请使用 **LanguagePack** 或 **ProofingTools** 作为产品 ID.
