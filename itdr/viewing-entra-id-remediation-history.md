# Viewing Entra ID Remediation History
Source: https://help.zscaler.com/itdr/viewing-entra-id-remediation-history
PDF: https://help.zscaler.com/pdf/com/en/1531844.pdf

After you [run remediation actions for the risky Entra ID identities](/itdr/running-remediation-actions-microsoft-entra-id-issues), you can view the remediation history or log details for further analysis. The logs provide details such as remediation action details, impacted identity, timestamp, remediation status, etc.
To view the Entra ID remediation history:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID Posture** dashboard, select an Entra ID tenant from the **Result for** drop-down menu.
[See image.](#itdr-entra-id-remediation-history-select-tenant-image)
The scan result for the Entra ID tenant appears.
-
Click **View Remediation History**.
The remediation history for the selected Entra ID tenant opens. You can view the following details:
- **Action**: The remediation action. This column can be filtered to display specific remediation actions.
- **Affected Identity**: The details of the affected or risky identity.
- **Date**: The date and time when the remediation action was run.
- **Result**: The result of the remediation action, indicating whether it was successful or unsuccessful. A green check mark indicates passed status, a red **X** indicates failed status. You can filter this column to view specific statuses.
- **Failure Reason**: The reason for the remediation failure.
- **Details**: Click the **View** icon to view additional details of the remediation action.
[See image.](#itdr-entra-id-remediation-action-history-details-image)
[]![Select an Entra ID tenant](/downloads/itdr/dashboard/entra-id/viewing-entra-id-remediation-history/itdr-entra-id-post-scan-remediation.png)
[]![View Entra ID remediation history details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-remediation-history/itdr-entra-id-view-remediation-history-view-details.png)