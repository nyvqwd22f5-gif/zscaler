# About the Entra ID Change Detection Object Safelist
Source: https://help.zscaler.com/itdr/about-entra-id-change-detection-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531796.pdf

After you [connect an Entra ID tenant](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) to the Zscaler ITDR Admin Portal, ITDR continuously monitors the Entra ID tenant for any malicious changes that could potentially introduce a new identity and privilege escalation risk. These changes are available to view on the [Entra ID Change Detection dashboard](/itdr/about-entra-id-change-detection-dashboard). You can review these changes to confirm that they are not a risk and mark them as safe by moving them to the object safelist if the changes are associated with a `principal_id`.
The Entra ID Change Detection Object Safelist provides the following benefits and enables you to:
- View the list of Entra ID objects that don't pose a risk and are marked safe.
- Ensure that the risk score on the Entra ID dashboard reflects the actual risk.
About the Entra ID Change Detection Object Safelist Page
On the Entra ID Change Detection Object Safelist page (ITDR > Settings > Entra ID Change Detection Object Safelist), you can do the following:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- View the list of objects that are marked safe. For each object, you can view:
- **Name**: The name of the user associated with the issue.
- **Associated Issue**: The issue associated with the object.
- **Created On**: The date when the change detection was added to the safelist.
- **Created By**: The name of the user who added the change detection to the safelist.
- **Reason**: The reason why the change detection was added to the safelist.
- **Expiry**: The date when the object is deleted from the safelist.
- [Edit or delete an object from the safelist](/itdr/editing-or-deleting-object-entra-id-change-detection-object-safelist).
![Entra ID Posture Safelist Page](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-object-safelist/about-entra-id-change-detection-object-safelist/itdr-about-entraid-cd-object-safelisting.png)