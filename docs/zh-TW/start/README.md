# 歡迎

## 介紹

Office Tool Plus 是一個多功能集於一身的 Office 部署工具。

Office Tool Plus 是基於 [Office 部署工具](https://docs.microsoft.com/en-us/deployoffice/overview-office-deployment-tool) 和 [OSPP](https://docs.microsoft.com/en-us/DeployOffice/vlactivation/tools-to-manage-volume-activation-of-office) 進行開發，透過整合 Thunder 下載引擎、小工具，協助您輕鬆、快速地部署、啟用、管理 Office。

下列產品的皆受支援：

- Microsoft 365
- Office 2016, 2019, 2021
- Visio 2016, 2019, 2021 以及 Online Plan 2
- Project 2016, 2019, 2021 以及Online Desktop Client

無論你是個體還是團隊，Office Tool Plus 都是你的得力小幫手。

## 下載

Office Tool Plus 下載位址如次：

- [Office Tool Plus 官方網站](http://otp.landian.vip/)

版本區別：

- 可攜式版：內包含 .NET 執行階段元件——無需安裝 .NET 執行階段即可執行 Office Tool Plus。
- 普通版本：僅包含 Office Tool Plus 和基本元件。

> 推薦使用可攜式版，以便使用。

### 解壓縮

請將 Office Tool Plus 壓縮檔解壓縮至合適的位置（例如桌面）。**請注意，勿在未解壓縮的情況下執行 Office Tool Plus** 。

## 特色功能

- 建立 Office 安裝設定檔：支援匯出到您的電腦，或是從電腦、網路位址匯入 Office Tool Plus。
- 下載 Office：支援所有更新頻道的 Office 和所有 Office 語言套件的下載。
- 安裝 Office：支援對已安裝的 Office 進行管理，例如新增/移除產品或應用程式。
- 建立 Office ISO 檔案：支援預設安裝設定、安靜安裝設定。
- 啟用 Office：支援線上啟用、電話啟用、KMS 啟用和更多方式。
- 支援 Office 授權管理：例如授權管理、金鑰管理和 KMS 管理。
- 修改 Office 更新頻道：支援在不重新安裝 Office 的情況下，進行升級/降級 Office。
- 移除 Office：在 Office 無法正常移除的情況下，強制解除安裝 Office（支援所有版本）。
- 整合實用 Office 工具：包括重設 Office 設定、修復 Office 問題等實用工具。
- 轉檔 Office 文件：基於 Office COM，穩定可靠。
- 自訂個人化主題: 打造專屬於自己的 Office Tool Plus。
- 進階設定——讓您使用更加進階的部署設定，例如 Office 的內部頻道。

::: warning 注意事項

1. Office 文件轉換功能可能無法相容 64 位元的 Office 版本。
2. Office Tool Plus 提供啟用管理功能，但您必須擁有正版授權，才能啟用 Office。

::::

## 元件與架構

```txt
Office Tool
├── Office Tool Plus.exe (主程式)
├── Office Tool Plus.Console.exe (主控台協助程式)
├── hostfxr.dll (.NET Host)
├── shared (.NET Runtimes)
└── files
    ├── setup.exe (Microsoft Office 部署工具)
    ├── activate (OSPP 和其他相關檔案)
    │   └── OSPP.VBS (Office 軟體保護平台)
    ├── clean
    │   ├── x64 (64 位元系統專用的 Office 啟用資訊清理工具)
    │   └── x86 (32 位元系統專用的 Office 啟用資訊清理工具)
    ├── preferences (Office 應用程式喜好設定的相關數據，由 Microsoft 提供)
    └── Thunder (Thunder 加速開放平臺相關文件)
```

通常 Office Tool Plus 會自動下載缺失的元件，並自動更新至最新版本。

如有部分元件遺失或無法自動下載，建議您重新下載 Office Tool Plus 以解決問題。
