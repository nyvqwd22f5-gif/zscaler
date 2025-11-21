#  End-of-Support for the Client Certificate Posture Check and Device Admin for Samsung Android Devices
Source: https://help.zscaler.com/eos-eol/end-support-client-certificate-posture-check-and-device-admin-samsung-android-devices
PDF: https://help.zscaler.com/pdf/com/en/1462086.pdf

Zscaler Client Connector version 1.13 and later for Android ends support for the Client Certificate posture check on Samsung Android devices.
With the release of Zscaler Client Connector version 1.13 for Android, Device Admin support will be removed for new installations. Upgrades of previous releases will include Device Admin until the release of Zscaler Client Connector version 1.14 for Android, which will no longer support Device Admin for new installs and upgrades. The installation parameter `enableKnox` will also be removed with the release of Zscaler Client Connector version 1.14 for Android.
While you can continue to use Device Admin and the Client Certificate posture check until you log out of Zscaler Client Connector after upgrading to Zscaler Client Connector version 1.13 for Android, Zscaler recommends you remove the Client Certificate posture check for Android in the Zscaler Client Connector Portal.
Next Steps
If you are currently using the Client Certificate posture check for your Samsung Android devices, adjust your Zscaler Private Access (ZPA) access policy to remove these checks, so that new installs of Zscaler Client Connector version 1.13 and later for Android and upgrades to Zscaler Client Connector version 1.14 for Android don't break ZPA policy access on Android.
Announcement date: August 9, 2023