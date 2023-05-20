# Application commands

The commands are case-insensitive and are executed in the order they are entered. If the path contains spaces, use "" (double quotes) to include the path.

## In-Application commands

These commands can only be used in command box.

![Command box](/assets/img/en-us/command-box.png)

| Command             | Description                        |                                                                       |
| :--                 | :--                                | :--                                                                   |
| /setImage *value*   | Set background image.              | *value*: path, support BMP, PNG and JPG. Support local and HTTP path. |
| /getKey *value*     | Get product default key.           | *value*: product ID.                                                  |
| /getBWP             | Get Bing wallpaper.                |                                                                       |
| /resetNotif         | Reset notifications to show again. |                                                                       |
| /loadConfig *value* | Load XML config from web.          | *value*: url.                                                         |

## Application commands

These commands can only be used in command-line.

| Command                | Description                                 |                                                      |
| :--                    | :--                                         | :--                                                  |
| /isoInstall            | Read the ISO config and start installation. | You must create a ISO and mount it first, make sure the ISO contains *ConfigForISO.xml*, or the command will not invoke.
| /loadConfig *value*    | Read a config and start installation.       | *value*: path to XML config. |
| /sourcePath *value*    | Override the source path of config.         | *value*: path of the source. The command must be used with the `/loadConfig` command. |
| /clientEdition *value* | Override the architecture of config.        | *value*: 32 or 64. The command must be used with the `/loadConfig` command. |
| /enableHWAcc *value*   | Enable hardware acceleration.               | *value*: *true* or *false*, default value is *true*. |

## Deploy commands

These commands can be used in command-line and command box.

deploy *[options]*

When using the deploy command, you need to specify it as deploy and then write the parameters, for example, the following is a simple deploy command.

``` batch
deploy /addProduct O365ProPlusRetail
```

| Command | Description |  |
| :-- | :-- | :-- |
| /addProduct *values[]* | Add product. | values: productID_language_excludeApps_MAK<br><br>**productID is required.**<br>See deploy examples below for details. |
| /removeProduct *values[]* | Uninstall product. | values: productID_language<br><br>Same as /addProduct |
| /removeAll | Uninstall all products. |  |
| /channel *value* | Set channel. | value: channel ID, default value is *Current*, [more info](/deploy/basic-settings.html#channel). |
| /clientEdition *value* | Set architecture. | value: 32 or 64, default value is *32*. |
| /migrateArch | Migrate architecture. |  |
| /version *value* | Set Office version | value: Office version. |
| /sourcePath *value* | Set source path. | value: path, support local or SMB path. |
| /display *value* | Display office installation interface. | value: true (Visible), false (Hidden), default value is *true*. |
| /acceptEULA | Accept EULA for users. |  |
| /module *value* | Set installation module. | value: 0 or 1, default value is 0.<br>0: Office Deployment Tool, 1: Office Tool Plus. |
| /downloadFirst | Set install after download. |  |
| /createShortcuts | Create desktop shortcuts. |  |

::: warning Warning
/display and /acceptEULA commands only available on V9.
:::

### Deploy Office examples

Deploy English edition of Office 2021 Pro Plus - Volume online, excludes Access, Outlook, OneNote:

``` batch
deploy /addProduct ProPlus2021Volume_en-us_Access,Outlook,OneNote /channel PerpetualVL2021
```

Deploy Office from local source, you need to set the `/sourcePath` and `/version` parameters. You will also need to set `/clientEdition` if you want to install 64-bit of Office.

``` batch
deploy /addProduct O365ProPlusRetail_en-us_Access,Outlook,OneNote /clientEdition 64 /sourcePath "D:\Test\Office Tool" /version 16.0.xxxxx.xxxxx
```

If you want to set MAK, you can do like that:

``` batch
deploy /addProduct ProPlus2021Volume_en-us_Access,Outlook,OneNote_XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /channel PerpetualVL2021
```

To ignore some attributes, leave blank like that:

``` batch
deploy /addProduct ProPlus2021Volume__Access,Outlook,OneNote /channel PerpetualVL2021
```

When specifying multiple applications or languages, you need to use commas to separate them. Such as Access,Lync or zh-cn,en-us.

If you need to add more than one product, specify multiple addProduct parameters.

If you need to add a language pack or proofreading tool, please use **LanguagePack** or **ProofingTools** as the product ID.

## OSPP commands

These commands can be used in command-line and command box.

ospp *[options]*

When using the OSPP command, you need to specify it as OSPP and then write the parameters, for example, the following is a simple OSPP command.

``` batch
ospp /insLicID ProPlus2021Volume /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /act
```

| Command | Description | Usage |
| :-- | :-- | :-- |
| /insLicID *value* | Installs licenses with user-provided product ID. | /insLicID ProPlus2021Volume |
| /inpkey:*value*   | Installs a product key.                          | /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX |
| /unpkey:*value*   | Uninstalls an installed product key.             | /unpkey:XXXXX |
| /sethst:*value*   | Sets a KMS host name.                            | /sethst:kms.example.com |
| /setprt:*value*   | Sets a KMS port, default *value* is 1688.        | /setprt:1688 |
| /act              | Activates installed Office product keys.         | /act |

For more information please visit [OSPP documentation](https://docs.microsoft.com/en-us/deployoffice/vlactivation/tools-to-manage-volume-activation-of-office).

## Office Tool Plus console helper

Office Tool Plus.Console is a command line program. By default, when executing a command through Office Tool Plus, the CMD will return immediately and will not wait for Office Tool Plus to exit. Office Tool Plus.Console will wait for the program to exit and supports outputting the log when executing commands.

Here is a example to enable logging output for Office Tool Plus:

``` batch
"Office Tool Plus.Console" /enableLog
```

::: tip Tip
The *deploy* and *ospp* commands enable logging by default, you do not need to specify the /enableLog parameter again. *deploy* and *ospp* commands cannot be mixed with other commands, or they will not be recognized.
:::

If you want to run *deploy* or *ospp* commands, specify the command like that:

``` batch
"Office Tool Plus.Console" deploy /addProduct ...
```

You can run *deploy* commands first, then *ospp* commands. The Office will be installed and activated automated.

### Batch file

If you want to create a batch file and run "Office Tool Plus.Console", make sure you have the administrator permission to execute the script.

Here is a template to create a batch file:

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
