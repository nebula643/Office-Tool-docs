# 激活命令

这些命令可以在命令行和命令框中使用，命令不区分大小写，按照顺序执行。

ospp *[options]*

使用 OSPP 命令时，你需要指定为 OSPP，然后再写参数，例如以下是一条简单的激活命令：

``` batch
ospp /insLicID ProPlus2021Volume /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /act
```

| 命令 | 说明 | 使用方法 |
| :-- | :-- | :-- |
| /insLicID *value* | 安装指定产品的 Office 许可证 | /insLicID ProPlus2021Volume |
| /inpkey:*value* | 安装指定的 Office 密钥 | /inpkey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX |
| /unpkey:*value* | 卸载指定的 Office 密钥 | /unpkey:XXXXX |
| /sethst:*value* | 设置 KMS 主机地址 | /sethst:kms.example.com |
| /setprt:*value* | 设置 KMS 主机端口，默认值: 1688 | /setprt:1688 |
| /act            | 激活 Office 客户端产品 | /act |
| /clAll          | 清除所有已安装的 Office 许可证和产品密钥 | /clAll |
| /clLicenses     | 清除所有已安装的 Office 许可证 | /clLicenses |
| /clKeys         | 清除所有已安装的 Office 产品密钥 | /clKeys |
| /dstatus        | 显示 Office 激活信息（仅在命令行中可用） | /dstatus |

::: warning 注意

若要使用 `/clAll`, `/clLicenses` 或 `/clKeys` 命令，请将这些命令写在首位，以便能够第一个执行；或分开执行，否则您安装的产品密钥或许可证会被清空。

:::
