# Resolving Auto-Update Issues for Zscaler Client Connector Linux 1.2
Source: https://help.zscaler.com/zscaler-client-connector/resolving-auto-update-issues-zscaler-client-connector-linux-1.2
PDF: https://help.zscaler.com/pdf/com/en/1385866.pdf

Prior to upgrading to version 1.2 for Linux, Zscaler Client Connector for Linux 1.1 needs an adjustment in order to address an issue with auto-updates for Ubuntu users. Until these changes are made, an auto-update to Linux 1.2 will not work.
Complete the following to resolve the issue:
- Download the zip file from [https://d32a6ru7mhaq0c.cloudfront.net/zcc-update-apparmor-from-1-1-0.zip](https://d32a6ru7mhaq0c.cloudfront.net/zcc-update-apparmor-from-1-1-0.zip).
- Unzip the file and keep all the artifacts in a single directory.
- Verify the md5sum of all the files match the following:
- 5e1f1cf4d4c165efd4b16917c6549b98 opt.zscaler.bin.zsaservice
- 8f450c77fe66af442a0c6b992ede494b opt.zscaler.bin.zstunnel
- 511370b72d7b2420ac09070b9ae2574a opt.zscaler.bin.zsupdater
- Run the zcc-update-apparmor-config.sh script with sudo permission:
sudo ./zcc-update-apparmor-config.sh
The script will use the other files to update the application.