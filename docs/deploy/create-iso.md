# Create Office ISO

Creating Office ISO files allows you to share Office with others, or use it for multiple installations.

For a better experience, please make sure you always download the latest version of Office Tool Plus which `includes runtime`.

We recommend that you update your Office ISO once a month, in line with the Office update frequency.

Anyway, it's suggested to test the ISO file by yourself when finished creating.

::: tip Tip
Using the version of Office Tool Plus which includes runtime allows you to run without the .NET Desktop Runtime installed, which is very helpful for multiple installations.
:::

## Create Office ISO with default configuration

Open Office Tool Plus, on deploy page, change deployment mode to `Create ISO file`, also check `Download first, then deploy`.

Add products as you want, such as Office Pro Plus 2021 - Volume License.

Add languages as you want, if not, you need to connected to Internet when installing Office.

Change other settings if needed.

**To verify the Office installation, check "Verify Office installations files after download." on "Download settings"**.

::: tip Tip
If you want to download Office for another version of Windows, for example, to download Office on Windows 10 for Windows 7, change *Download Settings - UA* to the corresponding system version.
:::

Click "start deploy".

The Office ISO created using this method contains the default configuration and asks the user to start the Office installation when opening Office Tool Plus.

After mounted the Office ISO, you can find the "Install now" option in the context menu of the CD-ROM. This operation will start installation immediately.

## Create Office ISO without configuration

Open Office Tool Plus, on deploy page, change deployment mode to `Download`.

Add products as you want, such as Office Pro Plus 2021 - Volume License.

Add languages as you want, if not, you need to connected to Internet when installing Office.

Change other settings if needed.

**To verify the Office installation, check "Verify Office installations files after download." on "Download settings"**.

::: tip Tip
If you want to download Office for another version of Windows, for example, to download Office on Windows 10 for Windows 7, change *Download Settings - UA* to the corresponding system version.
:::

Click "start deploy".

When finished downloading, press F5 to clear all configurations, also you can "refresh" on the submenu of "view XML code". After that, all products and languages should be clear.

Finally change deployment mode to `Create ISO file`, then start deploy.
