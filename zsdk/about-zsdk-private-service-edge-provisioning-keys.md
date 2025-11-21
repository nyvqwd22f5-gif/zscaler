# About ZSDK Private Service Edge Provisioning Keys
Source: https://help.zscaler.com/zsdk/about-zsdk-private-service-edge-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1524976.pdf

A provisioning key is a text string that is generated when you add a new ZSDK Private Service Edge. When deploying a Private Service Edge, you are prompted to enter this provisioning key, which functions as an ID for the Private Service Edge. This identification functionality allows the ZSDK cloud to verify the Private Service Edge's authenticity and complete the deployment process. Each key is associated with a specific Private Service Edge group and identifies the group to which Private Service Edge must deploy.
Private Service Edge provisioning keys provide the following benefits and enable you to:
- Deploy Private Service Edges into an associated Private Service Edge group.
- Limit the number of times a key is used for deployment.
- View the current key utilization count.
- Edit the maximum number of key uses.
- Edit the signing certificate used to enroll Private Service Edge certificates.
Provisioning keys can deploy additional Private Service Edges and respond optimally to increased capacity for auto-scaling. When you generate a provisioning key, you specify the number of times it can be used to deploy Private Service Edges. ZSDK tracks the number of times a key is used to deploy a Private Service Edge and displays the number on the Private Service Edge Provisioning Keys page. After a key is used the maximum number of times, you can edit the maximum number of times a key is used or associate multiple provisioning keys to a single Private Service Edge group.
About the Private Service Edge Provisioning Keys Page
On the Private Service Edge Provisioning Keys page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Provisioning Keys), you can do the following:
- Filter actions to view which information you want displayed.
- View which filters are applied.
- Hide the filters bar.
- Filter the information that appears in the table. By default, no filters are applied.
- Refresh the page to reflect the most current information.
- Expand one row or all rows in the table to see signing certificate information about each key. Clicking the signing certificate allows you to [edit its information](/zpa/editing-enrollment-ca-certificates).
- View a list of all provisioning keys. For each key, you see:
- **Name**: The name of the Private Service Edge provisioning key.
- **Maximum # of Private Service Edges**: The maximum number of Private Service Edges that can be deployed using the key.
- **Provisioning Key Utilization Count**: The number of times the provisioning key has been used.
- **Private Service Edge Group**: The Private Service Edge group associated with the key.
- **Provisioning Key**: The key needed for deploying a Private Service Edge. You can copy the provisioning key.
- Modify the columns displayed in the table.
- [Edit the provisioning key.](/zsdk/managing-zsdk-private-service-edge-provisioning-keys#edit)
- [Delete the provisioning key.](/zsdk/managing-zsdk-private-service-edge-provisioning-keys#delete)
- Download the provisioning key in a TXT format.
- Configure the number of rows for the table.
- Move between pages of provisioning keys.
- Go to one of the following pages:
- [Private Service Edges](/zsdk/about-zsdk-private-service-edges): Add new Private Service Edges or manage existing ones.
- [Private Service Edge Groups](/zsdk/about-zsdk-private-service-edge-groups): Manage Private Service Edge groups.
![View your ZSDK Private Service Edge provisioning keys](/downloads/zsdk/private-service-edge/about-zsdk-private-service-edge-provisioning-keys/ZSDK-About-Private-Service-Edge-Provisioning-Keys-2.png)