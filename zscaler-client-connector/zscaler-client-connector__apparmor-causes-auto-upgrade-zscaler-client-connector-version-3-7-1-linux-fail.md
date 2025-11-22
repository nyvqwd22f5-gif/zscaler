# AppArmor Causes Auto-Upgrade to Zscaler Client Connector version 3.7.1 for Linux to Fail
Source: https://help.zscaler.com/zscaler-client-connector/apparmor-causes-auto-upgrade-zscaler-client-connector-version-3-7-1-linux-fail
PDF: https://help.zscaler.com/pdf/com/en/1509276.pdf

Some endpoint devices cannot upgrade to Zscaler Client Connector version 3.7.1 for Linux because of an AppArmor conflict when accessing `openssl.cnf` by the OpenSSL service.
To resolve this issue, run the following script to update the ZSAUpdater AppArmor profile by adding the read permission to `openssl.cnf`:
This issue will be fixed in a future release.
- Open the ZSAUpdater AppArmor policy file `sudo vi /etc/apparmor.d/opt.zscaler.bin.zsupdater`.
- Insert the policy into the file `/etc/ssl/openssl.cnf r,`.
- Save and close the file.
- Refresh the AppArmor policies for the ZSAUpdater by using the command `sudo apparmor_parser -r /etc/apparmor.d/opt.zscaler.bin.zsupdater`.