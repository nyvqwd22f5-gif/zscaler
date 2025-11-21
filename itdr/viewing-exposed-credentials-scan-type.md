# Viewing Exposed Credentials by Scan Type
Source: https://help.zscaler.com/itdr/viewing-exposed-credentials-scan-type
PDF: https://help.zscaler.com/pdf/com/en/1531719.pdf

The All Exposures page lists the total number of exposed endpoint credentials for each exposure or scan type. You can filter this list based on a [scan](/itdr/configuring-endpoint-credential-exposure-scan) date. You can drill down to a specific exposure or scan type to view details, such as system name, identities, username, privilege escalation paths, etc. As a remediation action, you can clean up the exposed credentials for some exposure or scan types. Cleaning up risky credentials reduces the phase attack surface available to an adversary.
The following table lists the details of exposure or scan types for which the endpoints are scanned. For each exposure type, the table also indicates if the Cleanup Credentials feature is supported or not.
| **Exposure or Scan Type** | **Description** | **Cleanup Credential** |
| ------------------------- | --------------- | ---------------------- |
| Modifiable Service Binaries | Checks if service binaries are modifiable and could allow privilege escalation | Not supported |
| GPO Saved Passwords | Analyzes GPO files to look for reversibly encrypted credentials | Not supported |
| Unquoted Service Paths | Analyzes all Windows service configurations for unquoted paths that can be exploited to escalate privileges | Not supported |
| Cached Domain Logon Credentials | Analyzes cached domain credentials to find administrative sessions | Supported |
| AWS Credentials | Analyzes permanent AWS API keys stored in the default location | Supported |
| Saved VNC Passwords | Analyzes saved VNC connection strings across commonly used VNC applications (e.g., TigerVNC) | Supported |
| Sensitive Data Files | Checks files for exposed sensitive data | Not supported |
| Windows OOBE Priv Esc | Checks for non-administrative users having write access to the Windows' Unattended installation files | Not supported |
| Saved Windows Credentials | Analyzes the different types of credentials stored in the Windows Credential Manager | Supported |
| Saved Browser Credentials | Analyzes URLs and credentials stored in encrypted local databases of commonly used browsers | Not supported |
| Admin AutoLogon Settings | Analyzes AutoLogon registry settings that allow an administrative account to log in automatically | Supported |
| Database Connections | Analyzes saved database connection strings across commonly used database applications (e.g., pgAdmin) | Supported |
| Unmanaged Local Admins | Checks if accounts are local (non-domain), part of the local administrators group, and have a security identifier (SID) ending with a number other than 500 | Not supported |
| Windows OOBE Files | Analyzes Windows' Unattended installation files for credentials and insecure ACLs | Not supported |
| Elevated MSI Install Settings | Analyzes the registry to check settings that allow installation of MSI files in the elevated context | Not supported |
| Overly Permissive Administrative Memberships | Checks the local administrator groups for membership from overly permissive identities (e.g., Everyone, Authenticated Users, Domain Users, etc.) | Not supported |
| WDigest Settings | Checks the registry for settings that allow storage of plain text passwords in a reversibly encrypted form in the LSASS | Not supported |
| Modifiable PATH Variables | Checks if the path in the users' PATH variable is writable or modifiable and could allow adversaries to run under the users' context | Not supported |
| Modifiable MSI UninstallString | Checks if the UninstallString attribute of installed applications is modifiable and could allow code execution and possible privilege escalation when the application is uninstalled | Not supported |
| Azure Credentials | Analyzes different types of Azure credentials stored in the default location | Supported |
| Google Cloud Credentials | Analyzes different types of GCP credentials stored in the default location | Supported |
| SSH Keys | Analyzes private SSH keys without a passphrase on the file system | Not supported |
| LSA Protections | Checks the registry keys to confirm if Local Security Authority (LSA) protection is enabled | Not supported |
To view the details of the exposed credential for a specific exposure or scan type:
- Go to **ITDR** > **Dashboard** > **Endpoint Credential Exposure**.
-
Select the **All Exposures** tab.
The page lists the following information for each exposure or scan type:
- **Scan Type**: The name of the exposure or scan type.
- **Total**: The total number of exposed credentials.
- **Cleaned Up**: The total number of credentials that are cleaned up.
- **Available to cleanup**: The Cleanup Credential feature support status. A checkmark indicates that the feature is supported, and an **X** mark indicates that the feature is not supported.
[See image.](#itdr-exposed-credential-total)
-
Select a date from the **As of Date** calendar to view the exposed credential details on that scan date.
[See image.](#itdr-select-scan-date)
-
Double-click an exposure or scan type.
The details of the exposed credentials for that particular exposure or scan type are displayed in the table format.
[See image](#itdr-view-exposed-credential-issues)
- If the cleanup credential feature is supported for the exposure or scan type, you can select credentials and click **Cleanup Credentials** to clear or clean them up.
- You can click the **Actions** menu to [copy specific columns from the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [credentials as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
-
You can click an identity to view the [affected identity details](/itdr/viewing-affected-active-directory-user-account-details).
[See image.](#itdr-exposed-credential-identity)
[]![View all exposed credentials by exposure type](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-endpoint-credential-exposure-issues/itdr-all-exposure-types-as-of-date-5.png)
[]![Select a scan date](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-endpoint-credential-exposure-issues/itdr-all-exposure-select-date-4.png)
[]![View exposed credential details by scan type](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-endpoint-credential-exposure-issues/itdr-all-exposed-credentials-by-scan-type-3.png)
[]![Clean up credentials or view identity details](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-endpoint-credential-exposure-issues/itdr-all-exposure-types-cleanup-identity-3.png)