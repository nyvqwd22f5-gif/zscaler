# Viewing Active Directory Remediation History
Source: https://help.zscaler.com/itdr/viewing-ad-remediation-history
PDF: https://help.zscaler.com/pdf/com/en/1531879.pdf

After [you run remediation actions for the Active Directory (AD) identities](/itdr/running-remediation-actions-ad-identities), you can view the remediation history or log details for further analysis. The logs provide details such as remediation action details, impacted identity, timestamp, remediation status, etc.
To view the AD remediation history:
- Go to **ITDR** > **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard, select an AD domain from the **Result for** drop-down menu.
[See image.](#itdr-ad-rem-log-select-domain-view-rem)
The scan result for the AD domain appears.
-
Click **View Remediation History**.
The remediation history for the selected AD domain opens. You can view the following details:
- **Remediation Action**: The remediation action.
- **User Principal Name**: The user principal name of the AD user account.
- **Username**: The username of the AD user account.
-
**Message**: A message that explains the remediation action.
If the server agent doesn't run the remediation action within 24 hours, this column displays a timed-out message and the **Status** column is set to **Failed**.
- **Status**: The status (**Success**, **Failed**, **Enforcing**, or **Pending**) of the remediation action. You can filter this column to view specific statuses.
- **Run Timestamp**: The date and time when the remediation action was run.
- **Actions**: Click the **View** icon to view additional details of the remediation action such as request timestamp, status, failure reason, etc.
[See image.](#itdr-ad-rem-view-log-details)
[]![Select an AD domain](/downloads/itdr/dashboard/active-directory/viewing-ad-remediation-history/itdr-ad-rem-view-logs-ad-scan-timestamp.png)
[]![View AD remediation logs](/downloads/itdr/dashboard/active-directory/viewing-ad-remediation-history/itdr-ad-rem-view-logs-details-2.png)