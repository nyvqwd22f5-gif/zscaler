# Cleaning Up Exposed Endpoint Credentials
Source: https://help.zscaler.com/itdr/cleaning-exposed-endpoint-credentials
PDF: https://help.zscaler.com/pdf/com/en/1531793.pdf

[Watch a video on Endpoint Credential Exposure.](https://fast.wistia.net/embed/iframe/rfq1kuvn5v)
Exposed credentials on the endpoint are a critical source of risk. This enables adversaries to escalate privileges and access sensitive data and applications. Zscaler ITDR [scans](/itdr/about-endpoint-credential-exposure-scan) the endpoints and provides visibility into exposed endpoint credentials. You can investigate these credentials and, as a remediation action, clear or clean them up from the endpoints, thereby reducing the compromise phase attack surface available to an adversary.
Currently, ITDR supports credential cleanup for the following exposure or scan types only:
- Saved Windows Credentials
- Cached Domain Logon Credentials
- AWS Credentials
- Azure Credentials
- Google Cloud Credentials
- Database Connections
- Saved VNC Passwords
- Admin AutoLogon Settings
When you select an exposed credential for a cleanup, it's first queued for cleanup. The [agent](/itdr/about-endpoint-settings) fetches the updated policy by checking the queue in the Zscaler ITDR Admin Portal and applies the cleanup process to the endpoints or AD identities that are selected. The Cleanup Status column tracks the state of the cleanup process.
To clean up exposed credentials from endpoints:
- Go to **ITDR** > **Dashboard** > **Endpoint Credential Exposure**.
-
Select the **All Exposures** tab.
The page lists all exposure or scan types.
[See image.](#itdr-cleanup-ec-all-exposure-types)
-
Double-click an exposure or scan type for which the cleanup feature is supported (e.g., **AWS Credentials**). The exposure or scan types that support credential cleanup have a checkmark in the **Available to cleanup** column. The rest of the exposure types that don't support this feature have an **X** mark.
[See image.](#itdr-cleanup-ec-double-click)
The exposed credentials are displayed.
-
Select the credentials available for cleanup (the **Cleanup Status** column shows **Can be cleaned**), and click **Cleanup Credentials**.
[See image.](#itdr-cleanup-ec-select-credentials)
-
In the confirmation window, click **OK**.
The selected credentials are queued for cleanup. If the cleanup process is successful, the credentials are cleared from the endpoints.
-
Select **Show Cleaned Credentials** to view the list of credentials that were successfully cleaned up.
[See image.](#itdr-ec-cleanup-success)
If the cleanup process has failed, the **Cleanup Status** column shows **Failed**. You can see the reason for the failure.
[]![View all exposure types](/downloads/itdr/dashboard/endpoint-credential-exposure/cleaning-exposed-endpoint-credentials/itdr-cleanup-ec-all-scan-types-3.png)
[]![Double-click a scan type](/downloads/itdr/dashboard/endpoint-credential-exposure/cleaning-exposed-endpoint-credentials/itdr-cleanup-ec-all-double-click-scan-type-3.png)
[]![Select credentials for clean up](/downloads/itdr/dashboard/endpoint-credential-exposure/cleaning-exposed-endpoint-credentials/itdr-cleanup-ec-all-select-credential-for-cleanup-4.png)
[]![Cleanup successful](/downloads/itdr/dashboard/endpoint-credential-exposure/cleaning-exposed-endpoint-credentials/itdr-cleanup-ec-credentials-success-2.png)