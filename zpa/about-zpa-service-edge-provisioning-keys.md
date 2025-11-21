# About ZPA Private Service Edge Provisioning Keys
Source: https://help.zscaler.com/zpa/about-zpa-service-edge-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1484501.pdf

A provisioning key is a text string that is generated when you add a [new ZPA Private Service Edge](/zpa/configuring-service-edges). When [deploying a ZPA Private Service Edge](/zpa/about-deploying-service-edges), you are prompted to enter this key. The provisioning key functions like a credential for the ZPA Private Service Edge, enabling the ZPA cloud to verify the ZPA Private Service Edge's authenticity and complete the deployment process. Furthermore, each key is associated with a specific [ZPA Private Service Edge group](/zpa/about-zpa-service-edge-groups), so the key allows the ZPA cloud to identify the ZPA Private Service Edge group to which a ZPA Private Service Edge must be deployed.
Provisioning keys should be treated as secrets and properly protected because they can create a resource for a tenant. The provisioning key must also be secured and not transmitted or stored in clear text.
ZPA Private Service Edge provisioning keys provide the following benefits and enable you to:
- Deploy ZPA Private Service Edges into an associated Private Service Edge group.
- Limit the number of times a key can be used for deployment.
- View the current key utilization count.
- Edit the maximum number of key uses.
- Select the signing certificate used to enroll ZPA Private Service Edges certificates.
The following is a ZPA Private Service Edge provisioning key example:
1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==
The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Provisioning keys are designed to enable auto-scaling, so that you can easily deploy additional ZPA Private Service Edges and respond optimally to increases in required capacity. When you generate a provisioning key, you can specify the number of times a key can be used to deploy ZPA Private Service Edges.
ZPA tracks the number of times a key is used to deploy a ZPA Private Service Edge and displays it on the ZPA Private Service Edge Provisioning Keys page. When a key is used the maximum number of times, you cannot use it to deploy more ZPA Private Service Edges. However, you can always [edit the maximum number of times](/zpa/edit-service-edge-provisioning-key) a key can be used. You also have the option of associating multiple provisioning keys to a single ZPA Private Service Edge group.
About the Private Service Edge Provisioning Keys Page
On the Private Service Edge Provisioning Keys page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Provisioning Keys), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the Private Service Edge page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied.
- Expand all of the rows in the table to see more information about each provisioning key.
- View a list of all the provisioning keys. For each key, you can do the following:
- **Name**: The name of the Private Service Edge provisioning key. Expand the row and click the **Signing Certificate **to view the enrollment certificate for the provisioning key.
- **Maximum # of Private Service Edges**: The maximum number of ZPA Private Service Edges that can be deployed using the key.
- **Provisioning Key Utilization Count**: The number of times the provisioning key has been used.
- **Private Service Edge Group**: The ZPA Private Service Edge group associated with the key.
-
**Provisioning Key**: The key needed for [deploying a ZPA Private Service Edge](/zpa/about-deploying-service-edges).
This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [configuring ZPA Private Service Edges](/zpa/configuring-service-edges).
- [Modify the columns displayed in the table.](/zpa/using-tables)
-
Copy the provisioning key to your clipboard.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring ZPA Private Service Edges](/zpa/configuring-service-edges). If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same Private Service Edge.
If the **Provisioning Key Utilization Count** is reached, you cannot copy the key. A **Warning **icon appears next to the disabled **Copy **icon. You can [edit the key](/zpa/editing-a-zpa-private-service-edge-provisioning-key) to raise the limit.
[See image.](#img-warningicon)
- [Edit provisioning key details.](/zpa/edit-service-edge-provisioning-key)
-
Delete a provisioning key.
Provisioning keys that are managed by Zscaler are read only and cannot be edited or deleted.
-
Download the provisioning key to your system in a file format.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring ZPA Private Service Edges](/zpa/configuring-service-edges).
- Display more rows or a different page of the table.
- Go to the [Private Service Edges](/zpa/about-zpa-service-edges#AbourSvcEdgePage) page to add new ZPA Private Service Edges or manage existing ZPA Private Service Edges.
- Go to the [Private Service Edge Groups](/zpa/about-zpa-service-edge-groups#AboutSvcEdgeGroup) page to manage your ZPA Private Service Edge groups.
![Private Service Edge Provisioning Keys page in the ZPA Admin Portal](/downloads/zpa/private-service-edge-management/private-service-edge-provisioning-keys/about-zpa-service-edge-provisioning-keys/zpa-about-pse-provision-key-w-steps_1.png)
[]![Disabled Copy icon and Warning icon on the App Connector Provisioning Keys page](/downloads/zpa/private-service-edge-management/private-service-edge-provisioning-keys/about-zpa-service-edge-provisioning-keys/zpa-disablecopyicon-warningicon_0.png)