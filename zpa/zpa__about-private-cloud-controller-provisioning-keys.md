# About Private Cloud Controller Provisioning Keys
Source: https://help.zscaler.com/zpa/about-private-cloud-controller-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1507086.pdf

The provisioning key is a text string that is generated when you add a new Private Cloud Controller. When deploying a Private Cloud Controller, you are prompted to enter this key. The provisioning key functions like an ID for the Private Cloud Controller, enabling the ZPA cloud to verify the Private Cloud Controller's authenticity and complete the deployment process. Furthermore, each key is associated with a specific Private Cloud Controller group, so the key allows the ZPA cloud to identify the Private Cloud Controller group to which a Private Cloud Controller must be deployed.
Provisioning keys should be treated as secrets and properly protected because they can create a resource for a tenant. The provisioning key must also be secured and not transmitted or stored in clear text.
Private Cloud Controller provisioning keys provide the following benefits and enable you to:
- Deploy Private Cloud Controllers into an associated Private Cloud Controller group.
- Limit the number of times a key can be used for deployment.
- View the current key utilization count.
- Edit the maximum number of key uses.
- Select the signing certificate used to enroll Private Cloud Controller certificates.
The following is an example of a Private Cloud Controller provisioning key example:
`1|api.test.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==`
Provisioning keys are designed to enable auto-scaling so that you can easily deploy additional Private Cloud Controllers and respond optimally to increases in required capacity. When you generate a provisioning key, you can specify the number of times a key can be used to deploy Private Cloud Controllers.
ZPA tracks the number of times a key is used to deploy a Private Cloud Controller and displays it on the Private Cloud Controller Provisioning Keys page. When a key is used the maximum number of times, you cannot use it to deploy more Private Cloud Controllers. However, you can always edit the maximum number of times a key can be used. You also have the option of associating multiple provisioning keys to a single Private Cloud Controller group.
About the Private Cloud Controller Provisioning Keys Page
On the Private Cloud Controller Provisioning Keys page (Configuration & Control > Business Continuity > Business Continuity Management > Private Cloud Controller Provisioning Keys), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Private Cloud Controller Provisioning Keys page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied.
- Expand all the rows in the table to see more information about each provisioning key.
- View a list of all provisioning keys. For each key, you can see:
- **Name**: The name of the key.
- **Maximum # of Private Cloud Controllers**: The maximum number of Private Cloud Controllers that can be deployed using the key.
- **Provisioning Key Utilization Count**: The number of times the provisioning key has been used.
-
**Provisioning Key**: The key needed for deploying a Private Cloud Controller.
This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Private Cloud Controller](/zpa/configuring-private-cloud-controllers)s.
- **Private Cloud Controller Group**: The Private Cloud Controller group associated with the key.
-
Copy the provisioning key to your clipboard.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when configuring Private Cloud Controller. If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same Private Cloud Controller.
If the **Provisioning Key Utilization Count** is reached, you cannot copy the key. A **Warning** icon appears next to the disabled **Copy **icon. You can edit the key to raise the limit.
When a provisioning key is incorrectly copied, the following error appears in your Private Cloud Controller console when it tries to enroll:
`notice:Checking Enrollment
notice:No valid certificate. Attempting to enroll
notice:Enroll: Connecting to api.test.com via co2br.prod.zpath.net.
error:Login request failed - http status(401) nonce(<3|api.private.zscaler.com|0/Z6lDT...>) fingerprint(<oXaN4RRiMc...>)
notice:Certificate enrollment failed. `
- [Edit the provisioning key details.](/zpa/editing-private-cloud-controller-provisioning-keys)
-
Delete a provisioning key.
If a provisioning key is configured using Zscaler Deception or is managed by Zscaler, then the edit and delete options are unavailable.
-
Download the provisioning key to your system in a text file format.
This icon isn't available if you disabled the **View or Export Provisioning Key After Creation** option when when [configuring Private Cloud Controller](/zpa/configuring-private-cloud-controllers)s.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Private Cloud Controllers](/zpa/about-private-cloud-controllers) page to add new Private Cloud Controllers or manage existing Private Cloud Controllers.
- Go to the [Private Cloud Controller Groups](/zpa/about-private-cloud-controller-groups) page to view and manage your Private Cloud Controller groups.
- Go to the [Private Clouds](/zpa/about-private-clouds) page to add new Private Clouds or manage existing Private Clouds.
- Go to the [Settings](/zpa/configuring-business-continuity-settings) page to configure the Business Continuity settings.
![Viewing and Managing Private Cloud Controller Provisioning Keys ](/downloads/zpa/business-continuity-management/private-cloud-controller-provisioning-keys/about-private-cloud-controller-provisioning-keys/zpa-private-cloud-controller-provisioning-keys_0.png)