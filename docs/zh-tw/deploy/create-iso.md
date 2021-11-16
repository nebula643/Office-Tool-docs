# 建立 Office ISO

透過建立 Office ISO 檔案，您可以輕鬆與他人共享 Office 安裝文件，適合公司用於大量、多次部署。

為了確保您得到最佳體驗，請確保您始終從我們的 [官方網站](https://otp.landian.vip/) 下載了最新的 with runtime 版本的 Office Tool Plus。在必要時，我們會更新函式庫文件和 .NET Runtime 檔案，這些檔案並不會隨著 Office Tool Plus 更新系統跟著更新。需要您手動重新下載。

另外，我們也建議您在**每月的第二個星期二**更新一次 Office ISO 文件，使得 Office 能處在最新版本中。

Office ISO 建立完成後，我們建議您檢查 ISO 檔案，以確保檔案能與您預期一樣正常使用。

::: tip 提醒
with runtime 版本的 Office Tool Plus 允許您在沒有安裝 .NET Desktop Runtime 函式庫的情況下直接執行程式，這對於大量部署非常有幫助。
:::

## 建立包含預設配置的 Office ISO

在確保您使用的 Office Tool Plus 無誤後，開啟 Office Tool Plus.exe。

新增產品，按需求選擇 (例如 Office 2021 專業增強版 (大量授權) )。

新增語言套件，按需求選擇。如不新增，安裝時可能需要連線網際網路。

根據需求修改架構、頻道設定，和其他進階設定。

**為了確保 Office 安裝檔案的完整性，我們建議您勾選 「下載設定」 -> [下載完成後驗證 Office 安裝文件]。**

::: tip 提醒
如果您需要為不同版本的 Windows 下載 Office (例如在 Windows 10 中下載 Office 安裝文件供 Windows 7 使用)，請變更 *「下載設定」 -> [系統標示]*，以對應目標 Windows 版本。
:::

確認設定無誤後，點擊 [開始部署] 即可。

使用此方式所建立的 Office ISO 將會包含預設配置，在 ISO 中執行 Office Tool Plus 時，會詢問用戶是否直接開始 Office 的安裝。

掛載 Office ISO 後，如果您需要直接開始安裝，您可以在 CD-ROM 右鍵選單中點選 [立即安裝] 按鈕。

## 建立不含預設配置的 Office ISO

開啟 Office Tool Plus，在 [部署] 功能頁，切換 [部署模式] 到  [下載]。

新增產品，按需求選擇 (例如 Office 2021 專業增強版 (大量授權) )。

新增語言套件，按需求選擇。如不新增，安裝時可能需要連線網際網路。

根據需求修改架構、頻道設定，和其他進階設定。

**為了確保 Office 安裝檔案的完整性，我們建議您勾選 「下載設定」 -> [下載完成後驗證 Office 安裝文件]。**

::: tip 提醒
如果您需要為不同版本的 Windows 下載 Office (例如在 Windows 10 中下載 Office 安裝文件供 Windows 7 使用)，請變更 *「下載設定」 -> [系統標示]*，以對應目標 Windows 版本。
:::

確認設定無誤後，點擊 [開始部署] 即可。

下載完成後，按下 F5 鍵重設所有選項，亦可以在 [檢視代碼] 的子選單中找到 [重設] 選項。

然後切換 「部署模式」 > [建立 ISO 檔案]，點擊 [開始部署] 即可。
