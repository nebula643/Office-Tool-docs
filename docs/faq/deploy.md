# Deploy Questions

## Windows end of support and Microsoft 365 Apps

Microsoft 365 Apps may not install or run correctly on older systems. Microsoft strongly recommend you move to a supported operating system for better experience.

If you still want to install Microsoft 365 Apps on your PC, please use ***Current Channel*** as deploy channel. If you receive a message that your operating system is not supported when installing Microsoft 365 Apps, you can try changing the installation module from `Office Deployment Tool` to `Office Tool Plus` to skip the compatibility check.

For more information please visit:

- [Windows 7 end of support and Microsoft 365 Apps](https://docs.microsoft.com/en-us/deployoffice/endofsupport/windows-7-support).
- [Windows 8 end of support and Microsoft 365 Apps](https://docs.microsoft.com/en-us/deployoffice/endofsupport/windows-8-support).
- [Windows 8.1 end of support and Microsoft 365 Apps](https://docs.microsoft.com/en-us/deployoffice/endofsupport/windows-81-support).
- [Windows Server end of support and Microsoft 365 Apps](https://docs.microsoft.com/en-us/deployoffice/endofsupport/windows-server-support).

::: warning Notice
You can't install Office 2019/2021 on Windows 7 even you changed the installation module.
:::

## This product can't be installed on the selected update channel

If you have Office installation downladed, please make sure that the channel of Office installation is match the channel you are using. You can check them like that:

![Check channel](/assets/img/en-us/check-channels.png)

If they are not equals, please delete your installation packages, then re-download again. Or change the product to match the channel.

If they are equals, please make sure you have [clear activation](/activate/#clear-activation) before start deploy.

---

If you don't have Office installation downloaded, please make sure you have [clear activation](/activate/#clear-activation) before start deploy.
