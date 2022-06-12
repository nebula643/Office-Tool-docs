# 更多資訊

## Office Tool Plus 設定

如需儲存 Office Tool Plus 的設定，例如介面語言、主題或背景圖片設定，請勾選 [儲存個人偏好設定] 選項。

「進階設定」中可以變更語言顯示的格式，和開啟更進階的功能。

### 語言顯示設定

預設情況下，Office Tool Plus 顯示語言為當地格式，例如 English (United States)。

- 預設：不進行任何更改，按照預設的格式顯示。
- 當地語言：顯示語言的當地名稱，例如英語是 English，德文是：Deutsch
- 英文名稱：顯示語言的英文名稱，例如中文是 Chinese，德文是：German
- 本機語言：依照系統語言設定顯示，例如你的系統語言是中文，那麼所有的語言都顯示為中文。

當地語言、英文名稱以及本機語言由 Windows 提供數據，不同版本的 Windows 顯示結果可能不同。

::: tip 提醒
如要變更預設值，您需要重新啟動應用程式方能生效。
:::

### 進階功能

啟用此選項後，Office Tool Plus 將會載入 Office 內部通道和內部產品，例如 Dogfood 通道和 Mondo 2016 產品。

## Office Tool Plus 快速鍵

### Office Tool Plus 9

- <kbd>F1</kbd>: 檢視協助文件
- <kbd>F5</kbd>: 重新載入資訊/重設配置 (僅部署功能頁)
- <kbd>Ctrl + 1</kbd>: 切換到主畫面
- <kbd>Ctrl + 2</kbd>: 切換到部署功能頁
- <kbd>Ctrl + 3</kbd>: 切換到啟用功能頁
- <kbd>Ctrl + 4</kbd>: 切換到工具箱功能頁
- <kbd>Ctrl + 5</kbd>: 切換到轉換文件功能頁
- <kbd>Ctrl + T</kbd>: 檢視設定
- <kbd>Ctrl + B</kbd>: 檢視關於
- <kbd>Ctrl + L</kbd>: 安裝 iSlide (僅部署功能頁)
- <kbd>Ctrl + Shift + D</kbd>: 忽略警告或錯誤，強制進行部署 (僅部署功能頁)

### Office Tool Plus 8

- <kbd>Esc</kbd>: 返回
- <kbd>F1</kbd>: 檢視協助文件
- <kbd>F5</kbd>: 重新載入資訊/重設配置 (僅部署功能頁)
- <kbd>Ctrl + 1</kbd>: 切換到部署功能頁
- <kbd>Ctrl + 2</kbd>: 切換到啟用功能頁
- <kbd>Ctrl + 3</kbd>: 切換到工具箱功能頁
- <kbd>Ctrl + 4</kbd>: 切換到轉換文件功能頁
- <kbd>Ctrl + T</kbd>: 檢視設定
- <kbd>Ctrl + B</kbd>: 檢視關於
- <kbd>Ctrl + L</kbd>: 安裝 iSlide (僅部署功能頁)
- <kbd>Ctrl + Shift + D</kbd>: 忽略警告或錯誤，強制進行部署 (僅部署功能頁)

## Office Tool Plus 命令區指令

命令不區分大小寫，按照輸入順序執行。如果路徑中含有空格，請使用 "" (英文雙引號) 將路徑包括起來。

### Office Tool Plus Console Helper

Office Tool Plus.Console 是一个命令列程式，正常情況下，透過  Office Tool Plus 執行命令時，CMD 將會立即返回，無需等待 Office Tool Plus 關閉。透過 Office Tool Plus.Console 執行命令時，CMD 將會等待程式關閉，且支援輸出程式記錄檔。

以下命令範例為啟動 Office Tool Plus 日誌輸出：

``` batch
@echo off
title Office Tool Plus - Console

:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" /enableLog
```

以下命令範例為啟動 Office 2021 線上安裝：

``` batch
@echo off
title Office Tool Plus - Console

:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" deploy /addProduct ProPlus2021Volume_zh-cn_Access,Outlook,OneNote /channel PerpetualVL2021
```

如要進行離線安裝，建議您提前下載 Office 安裝文件，然後使用 */sourcePath* 參數以指定安裝文件的位置，並且使用 /version 指定 Office 安裝文件版本：

``` batch
@echo off
title Office Tool Plus - Console

:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" deploy /addProduct ProPlus2021Volume_zh-cn_Access,Outlook,OneNote /channel PerpetualVL2021 /sourcePath "D:\Office Tool" /version 16.0.00000.00000
```

以下命令範例為使用 KMS 啟用 Office 2021 專業增強版客戶端：

``` batch
@echo off
title Office Tool Plus - Console

:: Make sure you have administrator permission.
set "Apply=%*"
cd /d "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  cmd /u /c echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && ""%~s0"" %Apply%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Run commands.
"Office Tool Plus.Console" ospp /insLicID ProPlus2021Volume /sethst:kms.example.com /setprt:1688 /act
```

建議您可先執行 deploy 命令，再執行 ospp 命令，以達到自動安裝和啟用的效果。

::: tip 提醒
deploy 和 ospp 命令預設啟用記錄檔輸出，您無須再額外設定/enableLog 參數。deploy 和 ospp 命令不可與其他命令混用，否則將無法識別。
:::

### 命令區指令

| 指令 | 說明 |  |
| :-- | :-- | :-- |
| /setImage value | 設定背景圖 | value: 路徑, 支援 PNG, JPG。<br>支援本機和 HTTP 路徑。 |
| /getKey value | 取得產品預設金鑰 | value: 產品識別碼。 |
| /resetNotif | 重設通知以再次顯示已關閉的通知。 | |
| /loadConfig value | 從網際網路載入 XML 配置檔案。 | value: 網址。 |

::: warning 注意
Office Tool Plus 9 已不再支援 /getkey 命令，但您仍然可從 [產品列表](https://www.coolhub.top/tech-articles/products.html) 取得金鑰。
:::

### 部署指令

deploy [options]

使用部署指令時，您需要指定為 deploy，然後再寫參數，例如:

``` batch
deploy /addProduct O365ProPlusRetail
```

| 指令 | 說明 |  |
| :-- | :-- | :-- |
| /addProduct value | 新增產品 | value: productID_language_excludeApps_MAK。<br>其中 productID 為必要參數。<br>詳細使用方法見下方的部署範例。 |
| /removeProduct value | 移除產品 | value: productID_language。<br>使用方式同 /addProduct |
| /removeAll | 移除全部產品 |  |
| /channel value | 設定頻道 | value: 頻道識別碼。[檢視詳細資訊](https://docs.microsoft.com/zh-tw/deployoffice/office-deployment-tool-configuration-options#channel-attribute-part-of-add-element) |
| /clientEdition value | 設定架構 | value: 32, 64。 |
| /migrateArch | 變更架構 |  |
| /version value | 設定 Office 版本編號 | value: Office 版本編號。 |
| /sourcePath value | 設定來源路徑屬性 | value: 路徑。支援本機, SMB 路徑。 |
| /display value | 設定是否顯示 Office 安裝畫面 | value: true 显示，false 隐藏 |
| /acceptEULA | 代表用戶接受 OTP 授權合約 |  |
| /module value | 設定安裝模組 | value: 0, 1。<br>0: Office 部署工具，1: Office Tool Plus。 |
| /downloadFirst | 設定下載後安裝。 |  |
| /createShortcuts | 在桌面建立捷徑。 |  |

::: warning 注意
/display 和 / acceptEULA 參數僅在 Office Tool Plus 9 中可用。
:::
#### 部署 Office 範例

在電腦上部署繁體中文版的 Office 專業增強版 2021 (大量授權版)，排除 Access, Outlook, OneNote:

``` batch
deploy /addProduct ProPlus2021Volume_zh-tw_Access,Outlook,OneNote /channel PerpetualVL2021
```

如果您需要為大量授權的產品設定 MAK 金鑰，您可以使用以下指令:

``` batch
deploy /addProduct ProPlus2021Volume_zh-tw_Access,Outlook,OneNote_XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /channel PerpetualVL2021
```

如果你需要忽略某個參數，可以將其空白。例如不設定語言 (不建議這樣做):

``` batch
deploy /addProduct ProPlus2021Volume__Access,Outlook,OneNote /channel PerpetualVL2021
```

指定多個應用程式或語言時，您需要使用「英文逗號」將其隔開。例如 Access,Lync 或 zh-tw,en-us。

如果需要新增多個產品，請指定多個 addProduct 參數。

如果需要新增語言套件或校訂工具，請使用 **LanguagePack** 或 **ProofingTools** 作為產品識別碼。

### OSPP 命令

ospp [options]

使用 OSPP 命令時，你需要指定為 OSPP，然後再寫參數，例如以下是一條簡單的激活命令：

``` batch
ospp /insLicID ProPlus2021Volume /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /act
```

| 指令 | 說明 | 使用方法 |
| :-- | :-- | :-- |
| /insLicID value | 安裝指定產品的 Office 授權 | /insLicID ProPlus2021Volume |
| /inpkey:value | 安裝指定的 Office 金鑰 | /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX |
| /unpkey:value | 移除指定的 Office 金鑰(輸入後五碼) | /unpkey:XXXXX |
| /sethst:value | 設定 KMS 主機位址 | /sethst:kms.example.com |
| /setprt:value | 設定 KMS 連接埠，預設 1688 | /setprt:1688 |
| /act | 啟用 Office 產品 | /act |

有關 OSPP 的更多命令請參閱「[管理 Office 大量啟用的工具](https://docs.microsoft.com/zh-tw/deployoffice/vlactivation/tools-to-manage-volume-activation-of-office)」。
