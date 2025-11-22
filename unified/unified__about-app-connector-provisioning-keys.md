# About App Connector Provisioning Keys
Source: https://help.zscaler.com/unified/about-app-connector-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1496081.pdf

The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
The provisioning key is a text string that is generated when you [add a new App Connector](/unified/configuring-app-connectors). When [deploying an App Connector](/unified/about-deploying-app-connectors), you are prompted to enter this key. The provisioning key functions like an ID for the App Connector, enabling the cloud to verify the App Connector's authenticity and complete the deployment process. Furthermore, each key is associated to a specific [App Connector group](/unified/about-app-connector-groups), so the key allows the cloud to identify the App Connector group to which an App Connector must be deployed.
Provisioning keys should be treated as secrets and properly protected because they can create a resource for a tenant. The provisioning key must also be secured and not transmitted or stored in clear text.
App Connector provisioning keys provide the following benefits and enable you to:
- Deploy App Connectors into an associated App Connector group.
- Limit the number of times a key can be used for deployment.
- View the current key utilization count.
- Edit the maximum number of key uses.
- Select the signing certificate used to enroll App Connector certificates.
The following is an example of an App Connector provisioning key:
1|api.private.zscaler.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==
Provisioning keys are designed to enable auto-scaling so that you can easily deploy additional App Connectors and respond optimally to increases in required capacity. When you generate a provisioning key, you can specify the number of times a key can be used to deploy App Connectors.
The number of times a key is used to deploy an App Connector is tracked and displayed on the App Connector Provisioning Keys page. When a key is used the maximum number of times, you cannot use it to deploy more App Connectors. However, you can always [edit the maximum number of times](/unified/editing-app-connector-provisioning-keys) a key can be used. You also have the option of associating multiple provisioning keys to a single App Connector group.
About the App Connector Provisioning Keys Page
On the App Connector Provisioning Keys page (Infrastructure > Private Access > Component > App Connector Keys), you can do the following:
- Expand all of the rows in the table to see more information about each provisioning key.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all the provisioning keys. For each key, you can see the following:
- **Name**: The name of the key. Expand the row to view the **Signing Certificate **for the provisioning key.
- **Maximum # Of App Connector**: The maximum number of App Connectors that can be deployed using the key.
- **Provisioning Key Utilization Count**: The number of times the provisioning key has been used.
- **App Connector Group**: The App Connector group associated with the key.
- **Provisioning Key**: The key needed for [deploying an App Connector](/unified/about-deploying-app-connectors).
This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [configuring App Connectors](/unified/configuring-app-connectors).
- Copy the **Provisioning Key** to your clipboard.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring App Connectors](/unified/configuring-app-connectors). If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same App Connector.
If the Provisioning Key Utilization Count is reached, you cannot copy the key. A Warning icon appears next to the disabled Copy icon. You can [edit the key](/unified/editing-app-connector-provisioning-keys) to raise the limit.
[See image.](#img-warningicon)
When a provisioning key is incorrectly copied, the following error appears in your App Connector console when it tries to enroll:
notice:Checking Enrollment
notice:No valid certificate. Attempting to enroll
notice:Enroll: Connecting to api.private.zscaler.com via co2br.prod.zpath.net.
error:Login request failed - http status(401) nonce(<3|api.private.zscaler.com|0/Z6lDT...>) fingerprint(<oXaN4RRiMc...>)
notice:Certificate enrollment failed.
- [Edit provisioning key details](/unified/editing-app-connector-provisioning-keys).
- Delete a provisioning key.
If a provisioning key is configured using Zscaler Deception, then the edit and delete options are unavailable.
[See image.](#DeceptionAppConnectorPkey)
-
Download the provisioning key to your system in a file format.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [configuring App Connectors](/unified/configuring-app-connectors).
**![App Connector Provisioning Keys page within the Admin Portal](/downloads/unified/networking/private-applications/app-connector-management/app-connector-provisioning-keys/about-app-connector-provisioning-keys/app-connector-keys-page.png)
**
[]![Disabled Copy icon and Warning icon on the App Connector Provisioning Keys page](/downloads/zpa/app-connector-management/app-connector-provisioning-keys/about-app-connector-provisioning-keys/zpa-disablecopyicon-warningicon.png)
[]![Deception App Connector provisioning key](/downloads/zpa/app-connector-management/app-connector-provisioning-keys/about-connector-provisioning-keys/zpa-deception-integration-appConnectorPkey.png)