# 创建 Office ISO

使用 Office Tool Plus 创建 ISO 映像文件可以将 Office Tool Plus 和 Office 安装文件一起打包。ISO 映像文件可以与他人共享，或者用于多次安装。

Office 会固定在每个月的第二个星期二（太平洋时间）更新一次，我们建议您在此时间后及时更新您的 Office 和 Office Tool Plus，以确保您始终可以获得最佳的部署体验。

若要创建 Office ISO，您需要完成以下步骤：

- 下载合适的 Office Tool Plus.
- 创建 Office ISO 文件。
- 测试 Office ISO 是否和预期的一样工作。

## 注意事项

为了能够确保 Office 安装文件下载完整，我们建议您**勾选「下载设置」-「下载后校验 Office 安装文件」。**

Office Tool Plus 默认下载适合当前操作系统的 Office 版本，若要下载适用于其他 Windows 的 Office 版本，请**更改「下载设置」-「UA」为对应的系统版本**。

Office Tool Plus 在 ISO 模式下工作时会自动适配某些参数，您无需更改我们没有在教程中提到的参数。

## 获取合适的 Office Tool Plus 版本

为了方便进行多次部署，我们建议您[下载](/zh-cn/start/#下载)包含框架的 Office Tool Plus，不需要在客户端上安装 .NET Desktop Runtime (x86) 即可运行 Office Tool Plus.

将 Office Tool Plus 解压到合适的位置（例如桌面），双击以运行。

您可以根据需要创建以下格式的 Office ISO 文件：

1. [不含任何配置](/zh-cn/deploy/create-iso.html#不含任何配置的-office-iso)：像正常使用一样进行配置以及部署。
2. [包含默认配置](/zh-cn/deploy/create-iso.html#包含默认配置的-office-iso)：程序会自动加载配置，询问用户是否开始部署。
3. [使用 ISO 命令](/zh-cn/deploy/create-iso.html#使用-iso-命令)：程序会自动寻找配置并直接开始部署。
4. [使用自定义命令](/zh-cn/deploy/create-iso.html#使用自定义命令)：程序会根据您指定的命令创建配置并直接开始部署。

通常情况下，如果您需要创建 32 位和 64 位的 Office ISO，我们建议您分开创建两个文件。如果您决定创建同时包含 32 位和 64 位的 Office ISO，则我们不建议您使用第二或第三种方法创建 Office ISO，这两个方法无法自由选择 32 位或 64 位进行部署。

## 不含任何配置的 Office ISO

在部署页面，更改「部署设置」-「部署模式」为「创建 ISO 文件」，勾选「下载后再部署」。

确保做好以下事情：

- 添加产品，按需选择。若不添加，则无法确保后续是否正确。
- 添加语言，按需选择。若不添加或错加，则安装时需要联网。
- 选择体系结构，如无特殊需求，保持默认即可。
- 选择合适的通道，如无特殊需求，保持默认即可。

确保以上几点做好后即可「开始部署」，其他高级设置可以按需更改。

**在开始写入 Office ISO 前（下载完成前），请按下 F5 或者手动清空所有产品和语言，以确保创建的 Office ISO 不包含 ConfigForISO.xml.**

Office ISO 创建完成后，我们建议您验证一下 ISO 是否和你预期的一样能够正常使用。

::: tip 提示
如果你需要创建同时包含 32 位和 64 位的 Office ISO，请将体系结构更改为 64 位（或 32 位），然后再次点击开始部署即可。
:::

## 包含默认配置的 Office ISO

操作步骤[同第一个](/zh-cn/deploy/create-iso.html#不含任何配置的-office-iso)，**不要清空产品和语言，保留即可**。创建完成后，**Office ISO 文件应该包含 ConfigForISO.xml 文件。**

挂载 Office ISO 后，您应该能从 CD-ROM 上下文菜单中看到「立即安装」选项，或者正常启动 Office Tool Plus 然后确认安装。

## 使用 ISO 命令

创建 Office ISO 前，您需要在 Office Tool Plus 的根目录（Office Tool 文件夹）内创建批处理文件，例如 Setup.bat.

以下示例启动 Office Tool Plus，不等待执行完毕：

``` batch
@echo off
title Office Tool Plus

"Office Tool Plus.exe" /isoInstall
````

以下示例启动 Office Tool Plus，等待执行完毕：

``` batch
@echo off
title Office Tool Plus - Console

:: Change the working directory to current directory.
:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" /isoInstall
```

批处理文件创建并保存后，再开始创建 Office ISO 文件，**注意 BAT 文件不能使用非英文命名，否则会无法识别**。

其他操作步骤[同第一个](/zh-cn/deploy/create-iso.html#不含任何配置的-office-iso)，**不要清空产品和语言，保留即可**，创建完成后，**Office ISO 文件应该包含 ConfigForISO.xml 文件。**

## 使用自定义命令

创建 Office ISO 前，您需要在 Office Tool Plus 的根目录（Office Tool 文件夹）内创建批处理文件，例如 Setup.bat.

### 使用 LoadConfig 命令

使用 LoadConfig 命令可以加载 XML 配置文件，并修改其中的参数，以便进行安装。

例如如果您创建了同时包含 32 位和 64 位的 Office ISO，您可以使用以下命令安装对应的版本：

``` batch
@echo off

:: For 32-bit
"Office Tool Plus.exe" /loadConfig %~dp0ConfigForISO.xml /SourcePath %~dp0 /edition 32

:: For 64-bit
"Office Tool Plus.exe" /loadConfig %~dp0ConfigForISO.xml /SourcePath %~dp0 /edition 64
```

### 完全自定义安装

您可以使用 deploy 命令完全自定义您的 Office 安装，您可以[在这里](/zh-cn/others/commands.html#部署命令)学习 deploy 命令，然后调用 Office Tool Plus 进行安装。

例如以下示例如何安装简体中文 32 位的 Microsoft 365，排除 Access, Bing, Groove, Lync, OneDrive 应用程序：

``` batch
@echo off
title Office Tool Plus

"Office Tool Plus" deploy /addProduct O365ProPlusRetail_zh-cn_Access,Bing,Groove,Lync,OneDrive /clientEdition 32 /sourcePath %~dp0 /version 16.0.xxxxx.xxxxx
```

::: warning 注意
请将 /version 的参数替换为 Office 对应的 Office 版本号。
:::

如果您需要等待安装完成，请调用 Office Tool Plus.Console：

``` batch
@echo off
title Office Tool Plus - Console

:: Change the working directory to current directory.
:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" deploy /addProduct O365ProPlusRetail_zh-cn_Access,Bing,Groove,Lync,OneDrive /clientEdition 32 /sourcePath %~dp0 /version 16.0.xxxxx.xxxxx
```

批处理文件创建并保存后，再开始创建 Office ISO 文件，**注意 BAT 文件不能使用非英文命名，否则会无法识别**。

其他操作步骤[同第一个](/zh-cn/deploy/create-iso.html#不含任何配置的-office-iso)，**如果您使用的是 LoadConfig 命令，不要清空产品和语言，保留即可。使用完全自定义安装时，您可以清空产品和语言，因为我们不需要使用 ConfigForISO.xml 文件。**

## 大功告成

至此，您应该完成了 Office ISO 的创建，我们建议您在虚拟机内测试此 Office ISO 是否和您预期的一样工作。
