# Advanced settings

::: warning Warning
Do not change any settings if you can't understand, or your installation may be failed.
:::

## Basic settings

You can provide a description of configuration for documentation. Markdown is supported on Office Tool Plus, and the content will be displayed before deploying Office.

## Installation settings

### Fallback language

When you don't add any languages, the Office installer will try to match the system language. You can specify a fallback language to install Office when a matched language is not supported by Office or can not be found in the local source.

### Version

The latest available version of Office is installed by default.

If you need to install a historical version of Office, you can click the Refresh button on the right to get all available versions of Office. Or you can get the historical version from [Microsoft docs](https://docs.microsoft.com/en-us/officeupdates/update-history-microsoft365-apps-by-date).

If you have downloaded Office installations, the versions of all Office installations under the corresponding channel are displayed here.

### Source path

By default, the Office deployment tool fetches the Office installation files from the Office CDN. If you have the Office installation, you should select the file in the [Installation files manage](/deploy/basic-settings.html#installation-files-manage) instead of writing the path here.

If you are using SMB to share Office installation, you can write the SMB path here, and you should also specify the version of Office.

When using an existing installation, you should also make sure that the channel corresponds to the Office installation.

**In download mode, this property is used to define where to save the files.**

## Application preferences

> Application preferences are data provided by Microsoft, these texts are machine translated and may contain some grammatical errors.

The function allow you defines application preferences for Office Apps, including VBA Macro notifications, default file locations, and default file format.

You can apply new application preferences to client computers that already have Office installed. After you have set the values of preferences, click *Applying preferences for Office applications* in the *View XML code* submenu.

![Apply settings](/assets/img/en-us/apply-preferences.png)

The app preferences are applied to all existing users of the device and any new users added to the device in the future. If you apply application preferences when Office apps are running, the preferences will be applied when Office is next restarted.

## Other options

The other options are described in detail in the [Microsoft docs](https://docs.microsoft.com/en-us/deployoffice/office-deployment-tool-configuration-options), they are used in the same way.
