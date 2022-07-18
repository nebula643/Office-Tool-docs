# 部署问题

## 支持终止和 Microsoft 365 应用

Microsoft 365 应用不再支持 Windows 7 和 Windows 8 (包括 8.1 和 Server 操作系统)。微软强烈建议您迁移到受支持的操作系统。

如果你仍然想在你的 PC 上安装 Microsoft 365 应用，请使用 ***当前通道*** 作为部署时的通道。如果你不能在 Windows 8 或 Windows 8.1 中 安装 Microsoft 365 应用，请将安装模块从 Office 部署工具更改为 Office Tool Plus.

若要获取更多信息请访问:

- [Windows 7 支持终止和 Microsoft 365 应用](https://docs.microsoft.com/zh-cn/deployoffice/endofsupport/windows-7-support).
- [Windows 8 支持终止和 Microsoft 365 应用](https://docs.microsoft.com/zh-cn/deployoffice/endofsupport/windows-8-support).
- [Windows 8.1 支持终止和 Microsoft 365 应用](https://docs.microsoft.com/zh-cn/deployoffice/endofsupport/windows-81-support).
- [Windows Server 支持终止和 Microsoft 365 应用](https://docs.microsoft.com/zh-cn/deployoffice/endofsupport/windows-server-support).

::: warning 注意
即使你更改安装模块，你也无法在 Windows 7 中安装 Office 2019/2021.
:::

## This product can't be installed on the selected update channel

如果您已经下载了 Office 安装文件，请确保安装文件的通道和你所使用的通道匹配，你可以像这样进行检查：

![Check channel](/assets/img/zh-cn/check-channels.png)

如果通道不匹配，请删除已经下载了的安装包，并重新下载。或者更改产品，使其与目标通道匹配。

如果通道匹配，请确保您已经在开始部署 Office 前[清除激活信息](/zh-cn/activate/#清除激活状态)。

---

如果你没有使用本地安装文件，请确保您已经在开始部署 Office 前[清除激活信息](/zh-cn/activate/#清除激活状态)。通常来讲，这种事情不会发生在修改现有安装的过程中，多数出现在新安装产品的时候。