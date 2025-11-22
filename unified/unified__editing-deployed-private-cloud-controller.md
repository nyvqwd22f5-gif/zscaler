# Editing a Deployed Private Cloud Controller
Source: https://help.zscaler.com/unified/editing-deployed-private-cloud-controller
PDF: https://help.zscaler.com/pdf/com/en/1528671.pdf

To edit a deployed Private Cloud Controller:
- Go to **Infrastructure** > **Private Access **> **Business Continuity** > **Private Cloud Controllers**.
-
In the table, locate the Private Cloud Controller you want to modify and click the **Edit** icon.
Private Cloud Controllers that are managed by Zscaler are read only and cannot be edited.
The **Edit Private Cloud Controller** page appears.
- On the **Edit Private Cloud Controller **page, you can only modify the following fields:
- **Name**: The name of the Private Cloud Controller. When provisioning a new Private Cloud Controller, the provisioning key's name is automatically assigned as a prefix for the name of each Private Cloud Controller enrolled with it. Meaning that all Private Cloud Controllers in a given Private Cloud Controller group use the same prefix in its name. To help distinguish between the different Private Cloud Controllers in a group, each Private Cloud Controller also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth Private Cloud Controller to be enrolled with the key.
If you edit the Private Cloud Controller name, be sure to keep the prefix followed by the number that indicates that this is the nth Private Cloud Controller that is deployed with its key (e.g., "Amazon EC2 AMI based Private Cloud Controllers key - Oregon-1"). Also, the name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: The description for the Private Cloud Controller.
- **Status**: Enable or disable the Private Cloud Controller.
![Editing a Private Cloud Controller](/downloads/zpa/editing-a-deployed-private-cloud-controller/zpa-edit-private-cloud-controller.jpg)
- Click **Save**.
If you want to completely replace a deployed Private Cloud Controller, you must delete the configuration and then re-enroll it. However, you can apply the new Private Cloud Controller provisioning key to the virtual machine (VM) image you already deployed by replacing the old key.