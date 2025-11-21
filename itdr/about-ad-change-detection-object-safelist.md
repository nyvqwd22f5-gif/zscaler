# About the AD Change Detection Object Safelist
Source: https://help.zscaler.com/itdr/about-ad-change-detection-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531799.pdf

If you enable change detection for your Active Directory (AD) domain, Zscaler ITDR continuously monitors the AD domain for any malicious changes that could potentially introduce a new identity and privilege escalation risk. These changes are available to view on the [Change Detection dashboard](/itdr/about-entra-id-change-detection-dashboard). You can review these changes to confirm that they are not a risk and mark them as safe by moving them to the object safelist.
The AD Change Detection Object Safelist provides the following benefits and enables you to:
- View the list of AD objects that don't pose a risk and are marked safe.
- Ensure that the risk score on the AD dashboard reflects the actual risk.
About the AD Change Detection Object Safelist Page
On the AD Change Detection Object Safelist page (ITDR > Settings > AD Change Detection Object Safelist), you can do the following:
- Select an AD domain from the **Result for** drop-down menu.
- View the list of objects that are marked safe. For each object, you can view:
- **Name**: The name of the user associated with the issue.
- **Associated Issue**: The issue associated with the object.
- **Created On**: The date when the change detection was added to the safelist.
- **Created By**: The name of the user who added the change detection to the safelist.
- **Reason**: The reason why the change detection was added to the safelist.
- **Expiry**: The date when the object is deleted from the safelist.
- [Edit or delete an object from the safelist.](/itdr/editing-or-deleting-object-ad-change-detection-object-safelist)
![Entra ID Posture Safelist Page](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-object-safelist/about-ad-change-detection-object-safelist/itdr-about-ad-object-safelist.png)