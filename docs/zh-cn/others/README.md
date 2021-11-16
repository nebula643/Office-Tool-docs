# 更多信息

## 应用程序设置

如果需要保存 Office Tool Plus 的设置，例如语言、主题或者背景图设置，请勾选“保存设置到本地”选项。

高级设置里面可以更改语言显示格式以及开启高级功能。

### 语言显示格式

默认情况下，Office Tool Plus 显示语言为本地格式，例如英语显示为 English (United States).

- 默认：不进行任何更改，按照默认的设置显示。
- 本地名称：显示语言的本地名称，例如英语是 English，德语是：Deutsch
- 英文名称：显示语言的英文名称，例如中文是 Chinese，德语是：German
- 本地化名称：按照系统语言设置显示，例如你的系统语言是中文，那么所有的语言都显示为中文。

本地名称、英文名称以及本地化名称由 Windows 提供数据，不同版本的 Windows 显示结果可能不同。

::: tip 提示
要更改为默认值，你需要重新启动应用程序才能生效。
:::

### 高级功能

启用此选项后，Office Tool Plus 将会加载 Office 内部通道和内部产品，例如 Dogfood 通道和 Mondo 2016 产品。

## Office Tool Plus 快捷键

- <kbd>Esc</kbd>: 返回
- <kbd>F1</kbd>: 显示帮助
- <kbd>F5</kbd>: 刷新信息/重置配置（仅部署页面）
- <kbd>Ctrl + 1</kbd>: 切换到部署页面
- <kbd>Ctrl + 2</kbd>: 切换到激活页面
- <kbd>Ctrl + 3</kbd>: 切换到工具箱页面
- <kbd>Ctrl + 4</kbd>: 切换到文档转换页面
- <kbd>Ctrl + T</kbd>: 显示设置页面
- <kbd>Ctrl + B</kbd>: 显示关于页面
- <kbd>Ctrl + L</kbd>: 安装 iSlide（仅部署页面）
- <kbd>Ctrl + Shift + D</kbd>: 忽略警告或错误，强制进行部署（仅部署页面）

## Office Tool Plus 应用内命令

命令不区分大小写，按照输入顺序执行。如果路径中含有空格，请使用 "" (英文双引号) 将路径包括起来。

### 程序命令

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /setImage value | 设置背景图 | value: 路径，支持 PNG 或 JPG。<br>支持本地以及 HTTP 路径。 |
| /getKey value | 获取产品默认密钥 | value: 产品 ID. |
| /getBWP | 获取今日必应壁纸 |  |

### 部署命令

deploy [options]

使用部署命令时，你需要指定为 deploy，然后再写参数，例如以下是一条简单的部署命令：

``` batch
deploy /addProduct O365ProPlusRetail
```

| 命令 | 说明 |  |
| :-- | :-- | :-- |
| /addProduct value | 添加产品 | value: productID_language_excludeApps_MAK<br>其中 productID 为必需参数。<br>详细使用方法见下面的部署示例。 |
| /removeProduct value | 卸载产品 | value: productID_language<br>使用方法同 /addProduct |
| /removeAll | 卸载全部产品 |  |
| /channel value | 设置通道 | value: 通道 ID, [查看详细信息](https://docs.microsoft.com/zh-cn/deployoffice/office-deployment-tool-configuration-options#channel-attribute-part-of-add-element) |
| /clientEdition value | 设置体系结构 | value: 32 或 64。 |
| /migrateArch | 迁移体系结构 |  |
| /version value | 设置 Office 版本号 | value: Office 版本号。 |
| /sourcePath value | 设置源路径属性 | value: 路径，支持本地、SMB 路径。 |
| /module value | 设置安装模块 | value: 0 或 1。<br>0: Office 部署工具，1: Office Tool Plus. |
| /downloadFirst | 设置下载后安装 |  |
| /createShortcuts | 创建桌面快捷方式 |  |

#### 部署 Office 示例

在计算机上部署简体中文版的 Office 2021 专业增强版 - 批量版，排除 Access, Outlook, OneNote:

``` batch
deploy /addProduct ProPlus2021Volume_zh-cn_Access,Outlook,OneNote /channel PerpetualVL2021
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

### OSPP 命令

ospp [options]

使用 OSPP 命令时，你需要指定为 OSPP，然后再写参数，例如以下是一条简单的激活命令：

``` batch
ospp /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /act
```

| 命令 | 说明 | 使用方法 |
| :-- | :-- | :-- |
| /ilbyid value | 安装指定产品的 Office 许可证。 | /ilbyid MondoVolume |
| /inpkey:value | 安装指定的 Office 密钥。 | /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX |
| /unpkey:value | 卸载指定的 Office 密钥。 | /unpkey:XXXXX |
| /sethst:value | 设置 KMS 主机地址。 | /sethst:kms.example.com |
| /setprt:value | 设置 KMS 主机端口，默认 1688. | /setprt:1688 |
| /act | 激活 Office 客户端产品。 | /act |

有关 OSPP 的更多命令请查看[微软官方文档](https://docs.microsoft.com/zh-cn/deployoffice/vlactivation/tools-to-manage-volume-activation-of-office)。
