# 创建 Office ISO

创建 Office ISO 文件允许你与其他人分享 Office，或者用于大批量、多次安装。

为了获得更好的体验，请确保你始终从[官方网站](https://otp.landian.vip/)下载最新的包含框架的 Office Tool Plus，有时候我们会更新 .NET Runtime，这些文件不会随着 Office Tool Plus 的自动升级而更新，需要手动重新下载。

我们建议您一个月更新一次 Office ISO，与 Office 更新频率保持一致，每个月的第二个星期二为 Office 固定的补丁日。

Office ISO 创建完成后，我们建议您验证一下 ISO 是否和你预期的一样能够正常使用。

::: tip 提示
使用包含框架的 Office Tool Plus 允许你在没有安装 .NET Desktop Runtime 的情况下直接运行程序，这对大批量安装非常有帮助。
:::

## 创建包含默认配置的 Office ISO

打开 Office Tool Plus，在部署页面，切换部署模式为“创建 Office ISO”，并勾选下载后部署。

添加产品，按需选择，比如 Office 2021 专业增强版 - 批量许可证。

添加语言，按需选择，如果一个都不加，安装的时候依然需要联网。

根据需要修改体系结构和通道设置，其他设置可以按需更改。

**为了能够验证 Office 安装文件的完整性，我们建议您勾选「下载设置」-「下载后校验 Office 安装文件」。**

::: tip 提示
如果你需要为其他版本的 Windows 下载 Office，例如在 Windows 10 中下载 Office 安装包给 Windows 7 使用，请更改 *下载设置 - UA* 为对应系统版本，反之亦然。
:::

确认所有设置无误后，点击“开始部署”即可。

使用此方法创建的 Office ISO 包含默认配置，在 ISO 中双击打开 Office Tool Plus 时会询问用户是否开始 Office 的安装。

挂载 Office ISO 后，如果你需要直接开始安装，您可以在 CD-ROM 的上下文菜单（右键菜单）中找到“立即安装”选项。

## 创建不含默认配置的 Office ISO

打开 Office Tool Plus，在部署页面，切换部署模式为“下载”。

添加产品，按需选择，比如 Office 2021 专业增强版 - 批量许可证。

添加语言，按需选择，如果一个都不加，安装的时候依然需要联网。

根据需要修改体系结构和通道设置，其他设置可以按需更改。

**为了能够验证 Office 安装文件的完整性，我们建议您勾选「下载设置」-「下载后校验 Office 安装文件」。**

::: tip 提示
如果你需要为其他版本的 Windows 下载 Office，例如在 Windows 10 中下载 Office 安装包给 Windows 7 使用，请更改 *下载设置 - UA* 为对应系统版本，反之亦然。
:::

确认所有设置无误后，点击“开始部署”即可开始下载。

下载完成后，按 F5 重置所有选项，也可以在「查看 XML 代码」的子菜单中找到「重置」选项，重置后所有产品和语言应该变为空。

然后切换部署模式为“创建 Office ISO”，点击开始部署即可。

## 更多信息

### 如何同时下载 32 位和 64 位的 Office？

在下载 Office 安装文件时，将体系结构从 32 位切换到 64 位（反之同理），然后再次点击 「开始部署」，Office Tool Plus 会将新的下载任务添加到当前任务中，下载完毕后，32 位和 64 位的 Office 就应该一起下载完毕了。当然您也可以选择下载完一个版本后再下载另一个版本，Office Tool Plus 会跳过已存在的文件，仅下载缺失的文件。

### 没有开启自动播放的 Windows 如何使用一键安装功能？

某些情况下，客户端上的 Windows 可能未开启自动播放功能或者该功能无法正常工作。为了依然能够使用一键安装，我们需要自行编写 BAT 文件并保存在 Office Tool Plus 的根目录下，以便创建 Office ISO 时 Office Tool Plus 能将其一并打包。

::: tip 提示
BAT 文件不能使用非英文字符命名，否则会无法正常打包至 Office ISO 中。

ConfigForISO.xml 在创建 Office ISO 时由 Office Tool Plus 自动生成，您需要确保创建包含默认配置的 Office ISO.
:::

通常情况下，如果你只创建了单个版本的 Office ISO (例如 32 位)，则我们可以创建如下的 BAT 文件：

**Setup.bat:**

```batch
@echo off

"Office Tool Plus.exe" /isoInstall
```

执行以上命令时，Office Tool Plus 会查找 ConfigForISO.xml 并自动适配当前环境以便开始安装。

如果创建了 32 位和 64 位二合一的版本，则可以分别使用以下命令启动安装程序：

**Setup-32.bat:**

```batch
@echo off

:: For 32-bit
"Office Tool Plus.exe" /loadConfig %~dp0ConfigForISO.xml /SourcePath %~dp0 /edition 32
```

**Setup-64.bat:**

```batch
@echo off

:: For 64-bit
"Office Tool Plus.exe" /loadConfig %~dp0ConfigForISO.xml /SourcePath %~dp0 /edition 64
```

执行以上命令时，Office Tool Plus 会根据参数查找 XML 并加载，然后按照指定的参数修改体系结构和源路径属性值以便启动安装程序。

_注意：如果没有特别需求，以上命令中的参数不需要使用双引号包括，否则可能会因为字符串转义而发生不可预料的问题。_
