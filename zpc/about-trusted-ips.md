# About Trusted IPs
Source: https://help.zscaler.com/zpc/about-trusted-ips
PDF: https://help.zscaler.com/pdf/com/en/1466856.pdf

ZPC offers a robust trusted IP management feature that enables you to create and upload a list of trusted IP addresses used by your organization to access the public environment. This ensures that only essential components (assets or identities) from your cloud infrastructure are exposed to the broad internet. ZPC excludes these trusted IPs when examining assets or identities that are publicly exposed and eliminates false alerts generated for IPs.
Trusted IP addresses in ZPC aid in identifying public exposure scenarios within your public cloud infrastructure. The trusted IPs help distinguish between exposure that serves a legitimate business purpose and exposure that poses a security risk.
Only the Super Admin role can access, edit, or delete the trusted IPs.
The Trusted IP Management feature provides the following benefits and enables you to:
- Identify the public exposure scenarios within your public cloud infrastructure.
- Ensure that only essential components from your cloud infrastructure are exposed to the broad internet.
- Differentiate public exposure to understand the exposure that serves a business purpose and exposure that poses a security risk.
- Eliminate false alerts and minimize the alert clutter on your trusted public exposure configurations.
About the Trusted IP Management Page
On the Trusted IP Management page (Administration > Trusted IP List), you can do the following:
- Filter the trusted IP list. To learn more, see [Using Filters](/zpc/using-filters).
- [Add a trusted IP list](/zpc/adding-trusted-ips).
- Search for specific data. Click the Information icon (![Information icon](/downloads/zpc/administration/about-trusted-ips/zpc-info-icon.png)
) to see the columns that can be searched.
- View the list of Trusted IP addresses. For each Trusted IP address list, you can see the following details:
-
**Name**: The name of the trusted IP list. Click to view additional details of the trusted IP list, and download, edit, or delete the IP list.
[See image.](#actions)
- **Scope**: The cloud resource (All accounts, Accounts, Business Units) associated with the trusted IP list.
- **Created**: The timestamp for when the trusted IP list was created.
- **Last Updated**: The timestamp for when the trusted IP list was last updated.
- **Updated By**: The ZPC administrator username who last updated the trusted IP list.
- [Modify the table and its columns](/zpc/using-tables).
- [Download, edit, or delete a trusted IP list](/zpc/managing-trusted-ips).
![View the Trusted IP Management page](/downloads/zpc/administration/about-trusted-ips/zpc_trusted_IP_List_page.png)
[]![View Additional Details of Trusted IP](/downloads/zpc/administration/about-trusted-ips/zpc-trusted-ip-actions.png)