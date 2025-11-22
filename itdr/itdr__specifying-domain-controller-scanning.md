# Specifying a Domain Controller for Scanning
Source: https://help.zscaler.com/itdr/specifying-domain-controller-scanning
PDF: https://help.zscaler.com/pdf/com/en/1531644.pdf

After you [configure an Active Directory (AD) domain for scanning](/itdr/scanning-active-directory), you can specify a domain controller or an LDAP server to be used for scanning. Domain Controller (DC) is a server responsible for security authentication requests through LDAP. You can connect your AD domain to Zscaler ITDR through a DC server or an LDAP authentication.
To specify a DC or LDAP server for scanning:
- Go to **ITDR** > **Manage** > **Active Directory Posture**.
-
Locate the AD domain that you want to configure, and click the **Edit** icon.
[See image.](#deception-itdr-specify-dc-scan-edit-icon)
-
In the **Scan Agents Details** window, for **Logon Server**, specify the DC or LDAP server to use for scanning.
[See image.](#deception-itdr-specify-dc-scan-config)
- Click **Submit**.
[]![Edit an AD scan](/downloads/itdr/itdr/active-directory-posture-scan/specifying-domain-controller-scanning/itdr-ad-posture-edit-icon.png)
[]![Specify a domain controller or LDAP server for scanning](/downloads/itdr/itdr/active-directory-posture-scan/specifying-domain-controller-scanning/itdr-specify-dc-3.png)