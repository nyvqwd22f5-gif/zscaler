# Configuring Scan and LDAP Connection Timeout
Source: https://help.zscaler.com/itdr/configuring-scan-and-ldap-connection-timeout
PDF: https://help.zscaler.com/pdf/com/en/1531643.pdf

After you [configure an Active Directory (AD) domain for scanning](/itdr/scanning-active-directory), you can configure the scan and LDAP connection timeout. Timeouts are essential for performance as they help to prevent system resources from being used by long-running or unresponsive processes. By default, the scan timeout is 30 minutes and LDAP connection timeout is 5 minutes.
Zscaler recommends keeping the default values for better performance.
To configure the scan and LDAP connection timeout:
- Go to **ITDR** > **Manage** > **Active Directory Posture**.
-
Locate the AD domain for which you want to configure the timeout, and click the **Edit **icon.
[See image.](#deception-itdr-scan-timeout-edit-icon)
-
In the **Scan Agents Details** window:
- **Scan Timeout**: Enter the scan timeout in minutes.
- **Connection Timeout**: Enter the LDAP connection time in minutes.
[See image.](#deception-itdr-scan-timeout-config)
-
Click **Submit**.
The scan and LDAP connection timeout are configured for the selected AD domain.
[]![Edit an AD scan](/downloads/itdr/itdr/active-directory-posture-scan/configuring-scan-and-ldap-connection-timeout/itdr-ad-posture-edit-icon.png)
[]![Configure LDAP and scan timeout](/downloads/itdr/itdr/active-directory-posture-scan/configuring-scan-and-ldap-connection-timeout/itdr-ad-scan-timeout-config-3.png)