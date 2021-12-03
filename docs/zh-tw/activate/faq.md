# FAQ

## The Software Licensing Service reported that license consumption failed.

Error code: 0xC004E015

### Solution

Automatic operation: Repair Office activation, you can find the option in the Toolbox page. Then retry to activate Office.

---

Manual operation: Stop `Software Protection` service, delete three dat files on `C:\Windows\System32\spp\store_test\2.0` (There is a hidden file). Then retry to activate Office.

After installed Office licenses, wait three minutes. Then continue your operation.

**If the problem is not resolved, you may need to try again.**
