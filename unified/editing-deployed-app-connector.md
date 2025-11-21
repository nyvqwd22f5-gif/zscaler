# Editing a Deployed App Connector
Source: https://help.zscaler.com/unified/editing-deployed-app-connector
PDF: https://help.zscaler.com/pdf/com/en/1496036.pdf

To edit a deployed App Connector:
- Go to the **App Connectors** page (Infrastructure > Private Access > Component > App Connectors).
-
In the table, locate the App Connector you want to modify and click the **Edit** icon.
App Connectors that are managed by Zscaler are read only and cannot be edited.
The **Edit App Connector** window appears.
- In the **Edit App Connector **window, you can only modify the following fields:
- **Name**: The name of the App Connector. When [provisioning a new App Connector](/unified/configuring-app-connectors), the provisioning key's name is automatically assigned as a prefix for the name of each App Connector enrolled with it. Meaning that all App Connectors in a given App Connector group will use the same prefix in its name. To help distinguish between the different App Connectors in a group, each App Connector also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth App Connector to be enrolled with the key.
If you edit the App Connector name, be sure to keep the prefix followed by the number that indicates that this is the nth App Connector to have been deployed with its key (e.g., "Amazon EC2 AMI based connectors key - Oregon-1" in the image below). Also, the name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: The description for the App Connector.
- **Status**: Enable or disable the App Connector.
![Editing an App Connector](/downloads/zpa/app-connector-management/app-connectors/editing-a-deployed-app-connector/zpa-edit-app-connector-window.png)
- Click **Save**.
If you want to completely replace a [deployed App Connector](/unified/about-deploying-app-connectors), you must delete the configuration and then re-enroll it. However, you can apply the new App Connector provisioning key to the virtual machine (VM) image you already deployed by [replacing the old key](/unified/managing-deployed-app-connectors#ReplaceProvisioningKey).