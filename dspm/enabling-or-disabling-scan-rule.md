# Enabling or Disabling a Scan Rule
Source: https://help.zscaler.com/dspm/enabling-or-disabling-scan-rule
PDF: https://help.zscaler.com/pdf/com/en/1474761.pdf

After you [configure the scan rule](/dspm/about-scan-settings) for a resource, you must enable the scan rule to initiate the scan as per the schedule.
Enabling or Disabling a Scan Rule
To enable or disable a scan rule:
- Go to **Administration** > **Scan Settings**.
- Select the **Scan Rules** tab.
-
For the scan rule you want to change the status, click the **Scan Enable/Disable** toggle in that rule’s row.
- **Enabled**: The scan rule is enabled and runs as scheduled.
- **Disabled**: The scan rule is disabled and stops the run as scheduled.
[See image.](#ds-enabletoggle)
-
Read the confirmation message that appears, then click **Enable** or **Disable** to apply the changes.
[See image.](#ds-confirm-enable)
The scan rule is enabled or disabled per its status.
- When you disable a scan rule, any full scans that are currently in progress are completed, but subsequent incremental scans are disabled.
- To stop the full scan immediately, you need to first stop the scan from the **Actions** menu on the [Scan Settings page](/dspm/about-scan-settings).
[]![Scan rule details window with an annotation around the scan status.](/downloads/dspm/scan-settings/managing-scan-settings/enabling-or-disabling-scan/ds-scan-rule-status-change.png)
[]![Confirmation window to enable the scan rule](/downloads/dspm/scan-settings/managing-scan-settings/enabling-or-disabling-scan/ds-scan-rule-status-confirm.png)