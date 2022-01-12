# 配置选项

## 产品

购买了 Microsoft 365 的用户，添加产品的时候选择 Microsoft 365 产品即可，具体视你所拥有的授权而选择家庭版、个人版或企业版。

购买了 Office 2019/2021 的用户，按照自己购买的版本选择即可，例如家庭和学生版，或者专业增强版。

如果需要使用 KMS 或 MAK 激活，请安装批量许可证产品，例如 Office 2019 批量许可证或 Office 2021 批量许可证。

> 不确定自己是否拥有 Office 授权？个人账户请[从这里查看](https://account.microsoft.com/services/)，企业用户可以[从这里查看](https://portal.office.com/account/?ref=MeControl#subscriptions)。

::: details Office 365 产品对照表
| 订阅计划        | 产品 ID  |
| ------------- |:-------------:|
| 适用于企业的 Microsoft 365 应用 | O365ProPlusRetail |
| Office 365 企业版 E3 | O365ProPlusRetail |
| Office 365 企业版 E4 | O365ProPlusRetail |
| Office 365 企业版 E5 | O365ProPlusRetail |
| Office 365 中型企业版 | O365ProPlusRetail |
| Office 365 商业版 | O365BusinessRetail |
| Office 365 商业高级版 | O365BusinessRetail |
| Office 小型企业高级版 | O365SmallBusPremRetail |
| Microsoft 365 E3 | O365ProPlusRetail |
| Microsoft 365 E5 | O365ProPlusRetail |
| Microsoft 365 商业版 | O365BusinessRetail |
:::

## 语言

点击添加语言时，Office Tool Plus 会默认匹配当前系统的语言，如果匹配不正确或者需要选择其他语言，请手动更改。

可以添加一个语言，也可以添加多个语言，列表中的首个完整类型的语言决定了 Shell UI 区域性，包括快捷方式、右键单击关联菜单和工具提示。如果决定要在初始安装后更改 Shell UI 语言，必须卸载并重新安装 Office。

如果你没有添加语言，安装 Office 时将会自动匹配系统语言，如果系统语言无法匹配，则回退到 *高级设置 - 安装设置 - 备用语言* 所指定的语言。

如果你选择了“仅部署校对工具”，则该语言将会被安装为校对工具，不包含 Office 显示语言。

### 语言类型区别

| 语言类型　　　　　　　| 说明 |
| :------------------ | :--- |
| 完整　　　　　　　　　| 语言包包含显示语言和校对工具 |
| 部分　　　　　　　　　| 语言包包含部分 Office 应用程序的显示语言，包含校对工具 |
| 部分但不包含校对工具　| 语言包包含部分 Office 应用程序的显示语言，但不包含校对工具 |
| 校对工具　　　　　　　| 语言包仅包含拼写检查器 |

## 应用程序

应用程序会随你选择的产品不同而显示不同的内容。

Groove 代表的是 OneDrive for Business, Lync 代表的是 Skype for Business. 某些应用程序（例如 Teams 和 OneDrive）可能需要重启系统才能完成安装。

Bing 是一个用于 Chrome 和 Edge 的扩展，若要获取更多信息，请访问 [Microsoft 必应搜索和 Microsoft 365 企业应用版](https://docs.microsoft.com/zh-cn/deployoffice/microsoft-search-bing).

选择 Visio 或 Project 等产品时，由于其本身为一个不可选组件，因此不会出现在应用程序列表中。

有关产品和应用程序的信息，可以查看 [Office Products Information](https://www.coolhub.top/tech-articles/products.html).

## 通道

大多数情况下，只需要从当前通道或者半年度企业通道选择即可，下表列出了通道之间的区别：

| 通道                   | 发布频率                       | 功能更新            |
| --------------------- | ------------------------------ | ------------------- |
| 当前通道               | 每个月至少一次（可能更频繁）  | 同发布频率             |
| 半年度企业通道         | 每个月一次，每月的第二个星期二 | 一年两次（一月和七月） |
| 月度企业通道           | 每个月一次，每月的第二个星期二 | 同发布频率            |
| Office 2019 企业长期版 | 每个月一次，每月的第二个星期二 | 无                    |
| Office 2021 企业长期版 | 每个月一次，每月的第二个星期二 | 无                    |

> 企业长期版通道是 Office 2019/2021 批量许可证的专用通道。

表中列出的所有通道都是稳定通道，非测试通道，因此都可以日常使用。

每个通道都会在每个月的第二个星期二发布安全更新（如果需要），这是设定好的计划。

如果需要了解详细信息，请参阅 [Microsoft 365 应用版的更新通道概述](https://docs.microsoft.com/zh-cn/deployoffice/overview-update-channels)。

## 体系结构

**通常情况下，我们建议你安装 32 位的 Office**，但如果存在下列情况，则推荐安装 64 位的 Office:

- 处理大型数据集，例如包含复杂计算、许多数据透视表、与外部数据库的数据连接、Power Pivot、三维地图、Power View 或获取和转换的企业级 Excel 工作簿。 在这些情况下，64 位版 Office 可能表现更出色。
- 在 PowerPoint 中处理超大图片、视频或动画。 64 位版 Office 可能更适合处理这些复杂幻灯片。
- 在 Project 中处理超过 2 GB 的文件，尤其是项目包含许多子项目时。
- 开发内部 Office 解决方案，例如加载项或文档级别的自定义。 使用 64 位版 Office 将允许你提供这些解决方案的 64 位版和 32 位版。
- Access 中的 Long Long 数据类型，虽然 32 位 Access 支持此数据类型，但在使用 32 位 VBA 库的代码或表达式时可能会看到意外结果。 64 位 VBA 提供 Long Long 数据类型的完整支持。

如果需要了解详细信息，请参阅[选择 64 位或 32 位版本的 Office](https://support.microsoft.com/zh-cn/office/%E9%80%89%E6%8B%A9-64-%E4%BD%8D%E6%88%96-32-%E4%BD%8D%E7%89%88%E6%9C%AC%E7%9A%84-office-2dee7807-8f95-4d0c-b5fe-6c6f49b8d261)

## 部署模式

| 模式          | 说明 |
| ------------- | ----- |
| 编辑配置      | 仅用于生成/修改 XML 配置文件，不能进行部署   |
| 下载          | 仅下载 Office 安装包，不会也不能启动安装程序 |
| 安装          | 可以在计算机上进行安装、卸载、修改 Office 等操作 |
| 创建 ISO 文件 | 将 Office 安装包与 Office Tool Plus 一起打包，如果有安装配置，则连同配置一起写入 Office ISO 中 |

Office 安装包包含 Office、Visio 和 Project，由微软提供，无法精简。

## 安装模块

### Office 部署工具

Office 部署工具是微软官方工具，提供了部署 Office 的完整支持，适合所有人使用。

### Office Tool Plus

此模块是我们自行开发的安装模块，可以实现 Office 部署工具的大多数功能，并且还有 Office 部署工具无法做到的功能。不过缺点自然是不支持部分功能。

下表列出了两者之间的区别：

| 功能 | Office 部署工具 | Office Tool Plus |
| :-- | --- | --- |
| MECM 支持                    | ✓ | × |
| 更新截止时间                 | ✓ | × |
| 强制更新 Office              | ✓ | × |
| 移除现有的 MSI 版本的 Office | ✓ | × |
| 安装与 MSI 版本相同的语言    | ✓ | × |
| 使用 Office 内部通道         | × | ✓ |
| 安装特殊产品                 | × | ✓ |

我们建议优先使用 Office 部署工具，如果 Office 部署工具出现了无法修复的问题，或者有特殊需求，才应该选择 Office Tool Plus 作为安装模块。

## 下载设置

下载设置仅在 *下载* 模式，或者在勾选 *下载后再部署* 的情况下生效。

下载引擎的区别：

| 引擎                   | 显示下载信息 | 设置代理 | 暂停 & 继续 | 取消 |
| :--------------------- | :--- | :--- | :--- | :--- |
| 迅雷                   | ✓ | ✓ | ✓ | ✓ |
| Office Tool Plus       | ✓ | ✗ | ✗ | ✓ |
| Office 部署工具         | ✗ | ✗ | ✗ | ✗ |

通常情况下，使用迅雷引擎是一个不错的选择，它不仅能够提供更多支持，下载速度也会更快，此处的迅雷并非走的是 P2P，而是传统的 HTTP 协议。

当 Office Tool Plus 找不到迅雷组件时，将会回退到 Office Tool Plus 作为下载引擎。

### UA 设置

默认情况下，Office Tool Plus 会自动检测你的 Windows 系统版本，然后为你下载合适的 Office 版本。

如果你需要为别的 Windows 版本下载 Office 安装包，你可以更改 UA 为特定的 Windows 版本。

## 安装文件管理

默认情况下，当你从 Office Tool Plus 下载 Office 安装包后，Office Tool Plus 会自动识别 Office 安装包信息并显示在此处。

如果你有本地安装包，你可以点击 *选择文件*，然后指定 Office 安装文件中的任意一个 CAB 文件。

Office ISO 镜像应先挂载或者解压后，再选择其中内含的 CAB 文件。

点击版本可以删除某个版本的 Office 安装包；点击语言则可以删除该安装包下的特定语言。

如果安装包显示错误，则不应该继续部署 Office，检查问题所在，解决问题后再继续部署操作。

点击重置可以清除安装包信息，重置源路径属性为默认值，相当于不再使用本地安装包进行部署。

## 版本

此设置位于 *高级设置 - 安装设置* 中。

默认安装 Office 可用的最新版本，你无需设置 Office 的版本号。

如果你需要安装 Office 的历史版本，你可以点击右侧的刷新按钮，从 Office 服务器获取所有可用的 Office 版本，每个通道都有不同的 Office 历史版本。

如果你下载了 Office 安装包，则此处会显示相应通道下所有 Office 安装包的版本。

## 源路径

此设置位于 *高级设置 - 安装设置* 中。

默认情况下，在线安装 Office 时，Office 安装程序会从 Office CDN 服务器上获取 Office 安装文件。如果你在本地有 Office 安装包，则应该在安装文件管理中选择文件，而不是在此处写入路径。

如果使用了 SMB 共享 Office 安装文件，则可以在此处写入 SMB 共享路径，与此同时，还应该指定 Office 的版本号。

使用现有的安装包时，还应该确保通道与 Office 安装包对应，你不能够使用当前通道的安装包而指定半年度企业通道作为安装通道。

**在下载模式，源路径属性用于指定应将 Office 安装包储存在什么位置。**

## 应用程序首选项

`应用程序首选项由微软提供数据，其文本均为机器翻译，可能存在某些语法错误，请以英文版本的为准。`

应用程序首选项使你可以在部署 Office 前进行 Office 的设置，包括 VBA 宏通知、默认文件位置和默认文件格式。

除此之外，你还可以将应用程序首选项应用到现有的 Office 中，配置完毕后，在 *查看 XML 代码* 的子菜单中选择 *将首选项应用于 Office 应用程序* 即可，Office 部署程序会自动应用设置。

您所定义的应用程序首选项将应用于设备的所有现有用户以及未来添加到该设备的任何新用户。如果在 Office 应用程序运行时应用首选项，则新的设置将在 Office 下次运行时生效。

## 其他选项

其他选项介绍以及用法在[微软官方文档](https://docs.microsoft.com/zh-cn/deployoffice/office-deployment-tool-configuration-options)中有详细介绍，使用方法相同，在这里不再重复叙述。
