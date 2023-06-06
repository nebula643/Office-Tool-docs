# 部署问题

## Windows 支持终止和 Microsoft 365 应用

Microsoft 365 应用可能无法在老旧的系统上安装或运行。微软强烈建议您迁移到受支持的操作系统以便获得更好的使用体验。

如果你仍然想在你的 PC 上安装 Microsoft 365 应用，请使用 ***当前通道*** 作为部署时的通道。如果你在安装 Microsoft 365 应用时收到操作系统不受支持的提示，你可以尝试将安装模块从 `Office 部署工具`更改为 `Office Tool Plus` 以跳过操作系统兼容性检查。

获取更多信息请访问:

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