# About the Active Directory Object Safelist
Source: https://help.zscaler.com/itdr/about-active-directory-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531670.pdf

After you [scan an Active Directory (AD) domain](/itdr/scanning-active-directory), the issues are listed under the Focus Area section on the [Identity Posture](/itdr/about-identity-posture-dashboard) dashboard. On the [Focus Area](/itdr/viewing-focus-area-details) page for an Active Directory (AD) issue, you can view the list of AD objects (user accounts and computers) that are vulnerable to attack. You can review these AD objects to confirm that they are not a risk and mark them as safe by adding them to the safelist.
Adding objects to the safelist impacts the unified risk score on the [Identity Posture](/itdr/about-identity-posture-dashboard) dashboard.
Active Directory Object safelist provides the following benefits and enables you to:
- View the list of AD objects that doesn't pose a risk and are marked safe.
- Reduce the unified risk score on the [Identity Posture](/itdr/about-identity-posture-dashboard).
About the Active Directory Object Safelist Page
On the Active Directory Object Safelist (ITDR > Settings > Active Directory Object Safelist) page, you can do the following:
- Select an AD domain from the **Result for** drop-down menu.
- View the list of objects that are marked safe. For each object, you can view:
- **Name**: The issue name.
- **Type**: The object type (AD user or computer).
- **Associated Issue**: The issue the object is associated with.
- **Created On**: The date when the object was added to the safelist.
- **Created By**: The name of the user who added the object to the safelist.
- **Reason**: The reason why the object was added to the safelist.
- [Delete an object from the safelist.](/itdr/deleting-issue-active-directory-posture-safelist)
![A screenshot capturing the Active Directory Object Safelist page](/downloads/itdr/safelist/active-directory-object-safelist/about-active-directory-object-safelist/itdr-ad-object-safelist-page.png)