# Remediating Entra ID Identities
Source: https://help.zscaler.com/itdr/remediating-entra-id-identities
PDF: https://help.zscaler.com/pdf/com/en/1531843.pdf

You can remediate Entra ID identities directly from the Zscaler ITDR Admin Portal. Remediating risky identities improves the security posture of the Entra ID tenant. You can run remediate a specific or multiple identities (in bulk).
The following remediation actions can be run from the ITDR Admin Portal. ITDR runs these remediation actions in the background via single or multiple API calls to the Entra ID tenant.
| **Remediation Action Name** | **Action Description** | **Bulk Remediation Supported?** |
| --------------------------- | ---------------------- | ------------------------------- |
| Disable User | Changes the `accountEnabled` attribute of the Entra ID identity to `false`. | Yes |
| Revoke Session | Revokes Entra ID active user sessions to ensure any potentially compromised sessions are terminated. This remediation action doesn’t revoke guest user sessions. | Yes |
| Enforce MFA | Creates a conditional access policy in the Entra ID tenant that enforces users to use multi-factor authentication (MFA) for all applications. The conditional policy is created for the first user only. Subsequent users are appended to the existing policy. The policy ID is saved in the Entra ID tenant’s database. Run this remediation action with caution on administrative accounts to avoid locking yourself out of the account. | Yes |
| Enforce phishing-resistant MFA | Creates a conditional access policy in the Entra ID tenant that enforces users to use MFA for all applications. FIDO2 keys or similar authentication methods are used. The conditional policy is created for the first user only. Subsequent users are appended to the existing policy. The policy ID is saved in the Entra ID tenant’s database. You can run this remediation action on global admin-level users only. Also, run this remediation action with caution on administrative accounts to avoid locking yourself out of the account. | Yes |
| Remove Active Role Assignment | Removes one or more role assignments from the active user. This remediation action is available for a specific identity only. You cannot run this remediation action on multiple identities (bulk). | No |
| Remove Group Membership | Removes one or more group memberships. You cannot run this remediation action on a group with dynamic memberships. This remediation action is available for a specific identity only. You cannot run this remediation action on multiple identities (bulk). | No |
To run remediation actions for Entra ID issues:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
- On the **Entra ID Posture** dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-entra-id-remediation-action-select-tenant-image)
The scan result for the Entra ID tenant appears.
- Do one of the following:
- [Remediate a specific Entra ID identity.](#itdr-entra-id-remediation-specific-identity)
- [Remediate multiple Entra ID identities.](#itdr-entra-id-remediation-multiple-identity)
-
In the confirmation window, click **OK**.
The remediation is applied successfully.
You can [view the remediation logs or history](/itdr/viewing-entra-id-remediation-history) for further analysis.
-
[]Under **Top 10 Identities**, click a risky identity.
[See image.](#itdr-entra-id-remediation-action-top-10-risky-identities-image)
-
On the **Summary** tab, click **Actions**, and then select an appropriate remediation action. For example, select **Remove Active Role Assignment**.
[See image.](#itdr-entra-id-remediation-action-select-remediation-image)
-
Select a role.
[See image.](#itdr-entra-id-remediation-save-role-image)
- Click **Save**.
- []Do one of the following:
-
Under **Detailed Findings and Recommendations**, click an issue.
[See image.](#itdr-entra-id-remediation-detailed-find-recomm-image)
- Under **Top 10 Identities:**
-
Click an identity.
[See image.](#itdr-entra-id-remediation-top-10-risky-identity-select-image)
- Select the **Posture** tab.
[See image.](#itdr-entra-id-remediation-posture-tab-image)
- Scroll down to the **Who is affected?** table, and then select more than one risky identity.
- Click **Remediation**, and then select an appropriate remediation action. For example, select **Enforce MFA**.
[See image.](#itdr-entra-id-remediation-who-is-affected)
[]![Select an Entra ID tenant and scan timestamp](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-id-post-scan-domain-date-without-options.png)
[]![Click an identity ](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-top-10-identities.png)
[]![Select a remediation action for a specific identity](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-summary-select-action.png)
[]![Save remediation](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-summary-save-remediation.png)
[]![Select an Entra ID issue](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-detailed-findings-recomm.png)
[]![Select a risky identity](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-top-10-identities.png)
[]![Select the Posture tab](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-iid-remediation-identity-posture.png)
[]![Select a remediation action](/downloads/itdr/dashboard/entra-id/running-remediation-actions-microsoft-entra-id-issues/itdr-entra-id-remediation-identity-who-is-affected-action-1.png)