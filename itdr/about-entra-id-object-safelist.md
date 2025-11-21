# About the Entra ID Object Safelist
Source: https://help.zscaler.com/itdr/about-entra-id-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531768.pdf

After you [scan](/itdr/triggering-demand-scan-entra-id) an Entra ID tenant, the issues are listed under the [Focus Areas](/itdr/viewing-entra-id-focus-area-details) section on the [Entra ID dashboard](/itdr/about-entra-id-dashboard). On the Focus Areas page for an Entra ID issue, you can view the list of Entra ID objects (users and service principals) that are vulnerable to attack. You can review these objects to confirm that they are not a risk and mark them as safe by adding them to the safelist.
Adding objects to the safelist impacts the unified risk score on the [Entra ID dashboard](/itdr/about-entra-id-dashboard).
The Entra ID Object Safelist provides the following benefits and enables you to:
- View the list of Entra ID objects that don't pose a risk and are marked safe.
- Ensure that the risk score on the [Entra ID dashboard](/itdr/about-entra-id-dashboard) reflects the actual risk.
About the Entra ID Object Safelist Page
On the Entra ID Object Safelist page (ITDR > Settings > Entra ID Object Safelist), you can do the following:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- View the list of objects that are marked safe. For each object, you can view:
- **Name**: The issue name.
- **Type**: The object type (user or service principal).
- **Associated Issue**: The issue the object is associated with.
- **Created On**: The date when the object was added to the safelist.
- **Created By**: The name of the user who added the object to the safelist.
- **Reason**: The reason why the object was added to the safelist.
- [Delete an object from the safelist.](/itdr/deleting-object-entra-id-object-safelist)
![A screenshot of Entra ID Object safelist page](/downloads/itdr/safelist/entra-id-safelist/entra-id-obejct-safelist/about-entra-id-object-safelist/itdr-about-entra-id-object-safelist_1.png)