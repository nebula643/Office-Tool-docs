# Activation Questions

## The Software Licensing Service reported that license consumption failed

Error code: 0xC004E015

Solution

---

Automatic operation: Rebuild activation token, you can find the option in the Toolbox page. Then retry to activate Office.

---

Manual operation: Stop `Software Protection` service, delete dat files on `C:\Windows\System32\spp\store\2.0` (on Windows Insider, the folder name is store_test). Then retry to activate Office.

After installed Office licenses, wait three minutes, then continue your operation.

**If the problem is not resolved, you may need to try again.**

## The Software Licensing Service reported that a token in the Token Store contains an invalid hash

Error code: 0x8004E108

Solution is same as the previous item.

## The data is invalid (0x8007000D)

Make sure:

- Your system time is correct.
- The KMS host you are using is working fine. [How to test?](/others/toolbox.html#check-kms-status)

Then do the following things:

- Reset Software Protection service, you can find the option on toolbox page.
- Set KMS host and port, the default port is 1688.
- Try to activate again.
