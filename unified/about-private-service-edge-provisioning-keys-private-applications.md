# About Private Service Edge Provisioning Keys for Private Applications
Source: https://help.zscaler.com/unified/about-private-service-edge-provisioning-keys-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496551.pdf

The provisioning key is a text string that is generated when you add a [new Private Service Edge](/unified/configuring-private-service-edges-private-applications). When [deploying a Private Service Edge](/unified/about-deploying-private-service-edges-private-applications), you are prompted to enter this key. The provisioning key functions like an ID for the Private Service Edge, enabling the cloud to verify the Private Service Edge's authenticity and complete the deployment process. Furthermore, each key is associated to a specific [Private Service Edge group](/zpa/about-zpa-service-edge-groups), so the key allows the cloud to identify the Private Service Edge group to which a Private Service Edge must be deployed.
Private Service Edges provisioning keys provide the following benefits and enable you to:
- Deploy Private Service Edges into an associated Private Service Edge group.
- Limit the number of times a key can be used for deployment.
- View the current key utilization count.
- Edit the maximum number of key uses.
- Select the signing certificate used to enroll Private Service Edges certificates.
The following is a Private Service Edge provisioning key example:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==
Provisioning keys are designed to enable auto-scaling, so that you can easily deploy additional Private Service Edges and respond optimally to increases in required capacity. When you generate a provisioning key, you can specify the number of times a key can be used to deploy Private Service Edges.
The number of times a key is used to deploy a Private Service Edge is tracked and displayed on the Private Service Edge Provisioning Keys page. When a key is used the maximum number of times, you cannot use it to deploy more Private Service Edges. However, you can always [edit the maximum number of times](/unified/editing-private-service-edge-provisioning-key-private-applications) a key can be used. You also have the option of associating multiple provisioning keys to a single Private Service Edge group.
About the Private Service Edge Provisioning Keys Page
On the Private Service Edge Provisioning Keys page (Infrastructure > Private Access > Component > Service Edge Keys), you can do the following:
- Expand all of the rows in the table to see more information about each provisioning key.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all the provisioning keys. For each key, you can see the following:
- **Name**: The name of the Private Service Edge provisioning key. Expand the row and click the **Signing Certificate **to view the enrollment certificate for the provisioning key.
- **Maximum # Of Private Service Edges**: The maximum number of Private Service Edges that can be deployed using the key.
- **Provisioning Key Utilization Count**: The number of times the provisioning key has been used.
- **Private Service Edges Group**: The Private Service Edge group associated to the key.
- **Provisioning Key**: The key needed for [deploying a Private Service Edge for Private Applications](/unified/about-deploying-private-service-edges-private-applications).
This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Private Service Edges for Private Applications](/unified/configuring-private-service-edges-private-applications).
- [Edit provisioning key details.](/unified/editing-private-service-edge-provisioning-key-private-applications)
-
Delete a provisioning key.
Provisioning keys that are managed by Zscaler are read only and cannot be edited or deleted.
- Copy the **Provisioning Key** to your clipboard.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Private Service Edges for Private Applications](/unified/configuring-private-service-edges-private-applications). If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same Private Service Edge.
If the Provisioning Key Utilization Count is reached, you cannot copy the key. A Warning icon appears next to the disabled Copy icon. You can [edit the key](/zpa/about-connectorprovisioning/edit) to raise the limit.
[See image.](#img-warningicon)
-
Download the provisioning key to your system in a file format.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Private Service Edges for Private Applications](/unified/configuring-private-service-edges-private-applications).
![Private Service Edge Provisioning Keys page in the ZPA Admin Portal](/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge-provisioning-keys/about-private-service-edge-provisioning-keys-private-applications/private-service-edge-provisioning-keys-page.jpg)
[]![Disabled Copy icon and Warning icon on the App Connector Provisioning Keys page](/downloads/zpa/about-zpa-service-edge-provisioning-keys/zpa-disablecopyicon-warningicon.png)