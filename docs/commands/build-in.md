# Application Commands

The commands are not case-sensitive. If a command argument contains spaces, use "" (double quotes) to include them.

## In-application commands

These commands can be only used on command box. You can open command box via button or keyboard shortcuts <kbd>Ctrl + Shift + P</kbd>.

![Command box](/images/en-us/command-box.png)

| Command | Instruction |  |
| :-- | :-- | :-- |
| /setimage *value* | Set the background image. | *value*: path to image file. Support BMP, PNG or JPG. Support local or web location. |
| /getkey *value* | Get the default key for a product. | *value*: product ID. |
| /resetnotif | Reset notifications to show closed notifications again. | |
| /loadconfig *value* | Load config from web location. | *value*: web url. |

## Commands

These commands can be only used on command line.

| Command | Instruction |  |
| :-- | :-- | :-- |
| /isoinstall | 读取 ISO 配置文件并启动安装程序。 | 你必须创建 Office ISO，确保 ISO 内含 ConfigForISO.xml，挂载后再执行命令 |
| /loadconfig *value* | 读取 XML 配置文件并启动安装程序。 | *value*: XML 文件路径 |
| /srcpath *value* | 覆写 XML 配置文件中的源路径属性，该命令需配合 `/loadConfig` 命令使用 |
| /edition *value* | 覆写 XML 配置文件中的体系结构属性，*value*: `32` 或 `64`，该命令需配合 `/loadConfig` 命令使用 |
| /enablehwacc *value* | 启用硬件加速 | *value*: `true` or `false`, default value is `true` |

## Office Tool Plus Console Helper

Office Tool Plus.Console 是一个命令行程序，默认情况下，通过 Office Tool Plus 执行命令时，CMD 将会立即返回，不会等待 Office Tool Plus 退出。通过 Office Tool Plus.Console 执行命令时，CMD 将会等待程序退出，并且支持输出程序日志。

以下命令示例启动 Office Tool Plus 日志输出：

``` batch
"Office Tool Plus.Console" /enablelog
```

::: tip Tip

`deploy` and `ospp` 命令默认启用日志输出，您无需额外指定 `/enablelog` 参数。`deploy` 和 `ospp` 命令不可以和其他命令混用，否则会无法识别。

:::

如果您需要使用[部署命令](deploy.md)或者[激活命令](activate.md)，像这样用即可：

``` batch
"Office Tool Plus.Console" deploy /add ...
```

您可以先执行 `deploy` 命令，然后执行 `ospp` 命令，以便达到自动安装以及激活的效果。

### Batch File

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
"Office Tool Plus.Console" /isoinstall
"Office Tool Plus.Console" ospp /inslicid ProPlus2021Volume /sethst kms.example.com /setprt 1688 /act
```

第 1-9 行的内容无需更改，您只需要按照需求更改第九行之后的文本即可。
