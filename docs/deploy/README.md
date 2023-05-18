# Deploy Office

When deploying Office, installation and uninstallation can occur simultaneously, so you can combine multiple steps without having to perform them separately.

## Online installation

Open Office Tool Plus, go to deploy page, do the folowing things:

- Add product.
- Add language.

You may need to configure these options:

- Architecture: [Click here for more information](/deploy/configuration-options.html#architecture).
- Channel: If you want to install Office 2019/2021 Volume License products, you need to change channel to Office 2019/2021 Perpetual Enterprise. For more information please [see the details](/deploy/configuration-options.html#channels).

When everything is done, you can start deploy now. The Office installer will only download required files and install Office from Office CDN. Internet connection required, but may consume less data traffic. After installation, the installer will clean up the cache.

## Offline installation

Do the following things:

- If you are using the Office ISO created by Office Tool Plus, mount it or unpack it, open Office Tool Plus in the ISO, then deploy Office as online installation.
- If you have Office image (iso) downloaded from other site, mount it or unpack it, then "Select file" on "Installation files management". Finally deploy Office as online installation.
- If you have not yet downloaded the Office installation, check "Download first, then deploy" on "Deploy settings". Finally deploy Office as online installation. This may consume more data traffic. After installation, the installation files will store on ***Office Tool\Office*** folder.

::: tip Note
When you are using offline installation, the Office installation package determines which version of Office you can install.
:::

## Modifying products or languages

Add products or languages that you want, click *Uninstall* for which you want to uninstall now.

If everything is ok, click *Start deploy* to confirm.

## Modifying applications

![Modify Applications](/docs/assets/img/en-us/modify-applications.png)

Check applications that you want to install. Uncheck applications that you want to uninstall.

Keep others that you don't want to change.

Start deploy.

If the applications does not have the items you want, such as Access, add a new product and select Access.

## Upgrade Office

![Upgrade Office](/docs/assets/img/en-us/upgrade-product.png)

Download Office installation from another PC, then make an ISO or copy the files to the client, add the same products as installed products, finally start deploy.

## Migration architecture

Office Tool Plus supports changing Office from 32-bit to 64-bit (or 64-bit to 32-bit) automatically.

First change the architecture to the one you want. If you want to migrate to 64-bit Office, select 64-bit now.

![Migrate Office](/docs/assets/img/en-us/migrate-office.png)

Check *Advanced settings - upgrade options - migrate architecture*, then start deploy.

The installer will first uninstall your Office and then install the 64-bit Office.
