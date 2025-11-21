# Stopping an Ongoing Scan for an Active Directory Domain
Source: https://help.zscaler.com/itdr/stopping-ongoing-scan-active-directory-domain
PDF: https://help.zscaler.com/pdf/com/en/1531642.pdf

After you [configure an Active Directory (AD) for scanning](/itdr/scanning-active-directory) and a scan is in progress, you can stop the scan. When you want to update Zscaler ITDR software, or configure ITDR or your AD domain for any changes, you can temporarily stop an ongoing or scheduled scan. Until you start the scan, no further scans run even at the scheduled frequencies.
To stop an ongoing scan:
- Go to **ITDR** > **Manage** > **Active Directory Posture**.
-
Locate the AD domain with the scan that you want to stop, and click the **Stop **icon.
[See image.](#deception-itdr-scan-disable-ongoing)
-
In the confirmation window, click **OK**.
A confirmation message appears indicating that the scan is stopped. The scan is stopped until you start it again.
Click the **Start** icon to start the scan.
[See image.](#deception-itdr-scan-enable-ongoing)
[]![Stop an ongoing scan](/downloads/itdr/itdr/active-directory-posture-scan/stopping-ongoing-scan/itdr-ad-posture-pause-icon.png)
[]![Start an AD scan](/downloads/itdr/itdr/active-directory-posture-scan/stopping-ongoing-scan/itdr-ad-posture-play-icon.png)