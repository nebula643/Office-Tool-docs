# Deploy Commands

These commands can be used on command box and the command line. The commands are not case-sensitive. If a command argument contains spaces, use "" (double quotes) to include them.

``` batch
deploy params
```

For example the following is a simple deploy command:

``` batch
deploy /add O365ProPlusRetail_en-us
```

| Command | Instruction |  |
| :-- | :-- | :-- |
| /add *values[]* | Add one or more products. | values: productID_languages, **productID is a required parameter**. See the [example](deploy.md#deploying-office-examples) for how to use it. |
| /Product_ID.exclapps *values* | Set up excluded applications for specific product. | `Product_ID` is set according to the productID in the `/add` parameter. See the [example](deploy.md#deploying-office-examples) for how to use it. |
| /Product_ID.mak *values* | Set MAK for specific product. | `Product_ID` is set according to the productID in the `/add` parameter. See the [example](deploy.md#deploying-office-examples) for how to use it. |
| /rm *values[]* | Uninstall products. | values: productID_languages, usage same as `/add`. |
| /rmall | Uninstall all products. |  |
| /rmmsi | Uninstall all Office MSI products. |  |
| /channel *value* | Set update channel. | *value*: channel ID, default value is `Current`. [More info](/deploy/settings/basic.md#update-channel) |
| /edition *value* | Set architecture. | *value*: `32` or `64`, default value is `32`. |
| /migratearch | Migrate architecture. |  |
| /ver *value* | Set Office version. | *value*: Office version number. |
| /srcpath *value* | Set source path. | *value*: Local or SMB path. |
| /fallback | Fallback to Office CDN when language packs are not found locally. | *value*: `true` or `false`. Default value is `true`. |
| /display *value* | Set whether to display the Office installation screen. | *value*: `true`: visible, `false`: hidden. Default value is `true`. |
| /acpteula | Accept the EULA on behalf of the user. |  |
| /enableupdates | Set Office update state. | *value*: `true`: enbale, `false`: disable. |
| /updatepath | Set Office update download path. | *value*: Local or SMB path. |
| /module *value* | Set installation module. | *value*: `0`: Office Deployment Tool, `1`: Office Tool Plus. Default value is `0`. |
| /dlfirst | Download first, then deploy. |  |
| /shortcuts | Create desktop shortcuts. |  |

## Deploying Office Examples

指定多个应用程序或语言时，你需要使用「英文逗号」将其隔开，例如 `Access,Lync` 或 `en-us,en-us`

如果需要添加语言包或者校对工具，请使用 `LanguagePack` 或 `ProofingTools` 作为产品 ID，卸载同理。

部署 Office 2021 专业增强版 - 批量版，简体中文，排除 Access, Outlook, OneNote，可以这样写：

``` batch
deploy /add ProPlus2021Volume_en-us /ProPlus2021Volume.ExclApps Access,Outlook,OneNote /channel PerpetualVL2021
```

使用本地源部署 Office 时，你需要设置 `/srcpath` 和 `/ver` 参数。如果安装 64 位的 Office，还需设置 `/edition` 参数：

``` batch
deploy /add O365ProPlusRetail_en-us /O365ProPlusRetail.ExclApps Access,Outlook,OneNote /edition 64 /srcpath "D:\Test\Office Tool" /ver 16.0.xxxxx.xxxxx
```

To set a MAK for a volume product, you can write this:

``` batch
deploy /add ProPlus2021Volume_en-us /ProPlus2021Volume.ExclApps Access,Outlook,OneNote /ProPlus2021Volume.MAK XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /channel PerpetualVL2021
```

Too add multiple products, you can write this:

``` batch
deploy /add ProPlus2021Volume_en-us|VisioPro2021Volume_en-us /ProPlus2021Volume.ExclApps Access,Outlook,OneNote,OneDrive,Groove /VisioPro2021Volume.ExclApps OneDrive,Groove /channel PerpetualVL2021
```

To uninstall a product, you can write this:

``` batch
deploy /rm ProPlus2021Volume
```

To uninstall multiple products, you can write this:

``` batch
deploy /rm ProPlus2021Volume|VisioPro2021Volume
```

To uninstall language pack, you can write this:

``` batch
deploy /rm LanguagePack_ja-jp
```
