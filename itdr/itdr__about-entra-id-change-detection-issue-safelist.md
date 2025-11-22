# About the Entra ID Change Detection Issue Safelist
Source: https://help.zscaler.com/itdr/about-entra-id-change-detection-issue-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531771.pdf

After you [connect an Entra ID tenant](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal), Zscaler ITDR continuously monitors the Entra ID tenant for any malicious changes being made that could potentially introduce a new identity and privilege escalation risk. These changes are available to view on the [Entra ID Change Detection dashboard](/itdr/about-entra-id-change-detection-dashboard). You can review these change detection issues to confirm that they are not a risk and mark them as safe. For example, if you mark the Privileged Accounts issue as safe, then all issues related to Privileged Accounts are removed from the Entra ID Change Detection page for the selected Entra ID tenant.
The Entra ID Change Detection Issue Safelist provides the following benefits and enables you to:
- Ensure 24/7 monitoring for any malicious changes occurring in Entra ID.
- Mitigate risk by investigating malicious changes and changing configurations or permissions to reduce attack paths.
About the Entra ID Change Detection Issue Safelist Page
On the Entra ID Change Detection Issue Safelist page (ITDR > Settings > Entra ID Change Detection Issue Safelist), you can do the following:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- View the list of issues that are marked safe. For each issue, you can view:
- **Name**: The name of the change detection issue.
- **Created On**: The date when the change detection issue was added to the safelist.
- **Created By**: The name of the user who added the change detection issue to the safelist.
- **Reason**: The reason why the change detection issue was added to the safelist.
- [Delete an issue from the safelist.](/itdr/deleting-issue-entra-id-change-detection-safelist)
![A screenshot capturing the Entra ID Posture Safelist Page](/downloads/itdr/safelist/entra-id-safelist/entra-id-change-detection-safelist/about-entra-id-change-detection-safelist/itdr-about-change-detection-safelist_0.png)