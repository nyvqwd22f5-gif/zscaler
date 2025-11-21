# Remediating Active Directory Identities
Source: https://help.zscaler.com/itdr/remediating-active-directory-identities
PDF: https://help.zscaler.com/pdf/com/en/1531875.pdf

You can remediate Active Directory (AD) identities directly from the Zscaler ITDR Admin Portal. Remediating risky AD identities improves the security posture of the AD domain. You can remediate a specific or multiple AD identities (in bulk).
Before taking remediation actions against risky AD identities, you must [configure a server agent](/itdr/enabling-remediation-server-agent). The server agent runs these remediation actions in the background via single or multiple API calls.
The following remediation actions can be taken from the ITDR Admin Portal:
| **Remediation Action Name** | **Action Description** | **Bulk Remediation Supported?** |
| --------------------------- | ---------------------- | ------------------------------- |
| Disable User | Disables the AD user account. | Yes |
| Enable User | Enables the AD user account. | Yes |
| Reset Password | Enforces a password change on the next login for the AD user account. | Yes |
| Revoke Group Membership | Removes the AD user account from a specific group. Only users from the static privilege group can be removed. If a user is not a member of the specified group or if the specified group does not exist, no remediation action is taken. | No |
To run remediation actions for AD identities:
- Go to **ITDR** > **Active Directory Posture**.
- On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-ad-rem-action-scan-timestamp-image)
The scan result for the AD domain appears.
- Do one of the following:
- [Remediate a specific AD identity.](#itdr-ad-remediation-action-single-identity-section)
- [Remediate multiple AD identities.](#itdr-ad-remediation-action-bulk-identities-section)
If there are any pending remediations for an identity, and you try to run the same or any other remediations, a warning message appears. You can either click **Resubmit** to proceed with the request or click **Close** to exit.
[See image.](#itdr-rem-action-pend-warn)
You can view the [remediation logs or history](/itdr/viewing-ad-remediation-history) for further analysis.
You can take remediation actions on AD identities for which [active changes are detected](/itdr/running-remediations-active-directory-change-detection-dashboard) or [identities that have compromised or weak passwords](/itdr/viewing-password-analysis-details-remediate-issues).
- []Do one of the following:
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#itdr-rem-action-find-recomm-single-image)
- Scroll down to the **Who is affected?** table.
- Select a specific AD identity and click the **Remediate** icon.
-
Select an appropriate remediation action. For example, select **Revoke Group Membership**.
[See image.](#itdr-rem-action-who-aff-rem-single-id-image)
-
In the **Remove Group Membership **window, select the AD groups from which you want to remove the user.
[See image.](#itdr-ad-rem-action-select-group-image)
-
Click **Save**.
The remediation is applied successfully.
-
Under **Top 10 Users & Computers**, click an AD identity.
[See image.](#itdr-ad-rem-action-top-10-ad-id-image)
- On the **Summary** tab, click **Actions**.
-
Select an appropriate remediation action. For example, select **Reset Password**.
[See image.](#itdr-ad-rem-action-select-remediation-image)
-
In the confirmation window, click **OK**.
The remediation is applied successfully.
- []Do one of the following:
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#itdr-ad-rem-action-select-ad-issue-bulk-image)
- Under** Top 10 Users & Computers**:
-
Click an AD identity.
[See image.](#itdr-ad-rem-action-select-ad-identity-bulk-image)
-
Select the **Posture** tab.
[See image.](#itdr-ad=rem-action-posture-tab-image)
- Scroll down to the **Who is affected?** table, and then select more than one AD identity.
- Click **Remediations**, and then select an appropriate remediation action. For example, select **Reset Password**.
[See image.](#itdr-rem-action-who-aff-rem-bulk-id-image)
-
In the confirmation window, click **OK**.
The remediation is applied successfully.
[]![Select an AD scan domain and timestamp](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-scan-timestamp.png)
[]![Select an AD issue](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-findings-recomm.png)
[]![Select a remediation action](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-who-is-affected-single-2.png)
[]![Click a risky AD identity](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-top-10-ad-id.png)
[]![Select a remediation action](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-summary-action-1.png)
[]![Select the AD groups](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-remove-groups.png)
[]![Select an AD issue](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-findings-recomm.png)
[]![Select an AD identity](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-top-10-ad-id.png)
[]![Select posture tab](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-posture-tab.png)
[]![Select a remediation action](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-who-is-affected-bulk-1.png)
[]![View pending remediation warning](/downloads/itdr/dashboard/active-directory/running-remediation-actions-ad-identities/itdr-ad-remediation-action-warning-pending-rem.png)