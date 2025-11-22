# Managing ZSDK Private Service Edge Provisioning Keys
Source: https://help.zscaler.com/zsdk/managing-zsdk-private-service-edge-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1525711.pdf

Each ZSDK Private Service Edge provisioning key allows you to set a maximum limit for its usage for a Private Service Edge group. You can also configure the signing certificate.
Each provisioning key is created while you create a Private Service Edge. After the provisioning key is created, you must then assign it to a Private Service Edge group.
To manage your provisioning keys, you can:
- [Create a provisioning key to assign to a Private Service Edge group.](/zsdk/managing-zsdk-private-service-edges#CreateProvisioningKey)
- [Edit a provisioning key.](#edit)
- [Delete a provisioning key.](#delete)
Considerations & Limitations
When configuring a provisioning key:
- You can have up to 100 provisioning keys. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations#privateserviceedge).
- If the Provisioning Key Utilization Count is reached, you cannot copy the key. A Warning icon appears next to the disabled Copy icon. You can [edit the key](#reached_edit) to raise the limit.
- Each provisioning key is unique to each Private Service Edge group.
[][]
On the Private Service Edge Provisioning Keys page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Provisioning Keys):
- Click the **Edit** icon on the Private Service Edge provisioning key that you want to modify.
-
In the **Edit Private Service Edge Provisioning Key** window, you can modify the following:
- **Name**: Enter the name of the provisioning key. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
This name is automatically assigned as a prefix to the name of each Private Service Edge enrolled with it. This means that all Private Service Edges in a given Private Service Edge group use the same prefix in their name. To help distinguish between the different Private Service Edges in a group, each Private Service Edge also has a number automatically added to their name upon being enrolled. This number signifies that it is the nth Private Service Edge to be enrolled with the key. For example, if you enter `AWS Oregon` as a provisioning key name in this step, the first Private Service Edge you enroll with this key is named `AWS Oregon-1`. The next Private Service Edge you enroll with the same key is named `AWS Oregon-2`, and so on.
- **Maximum Reuse of Provisioning Key**: Enter the maximum number of instances where this key can be used to enroll a Private Service Edge. After adding the Private Service Edge, this number can be modified.
- **Signing Certificate**: The signing certificate (i.e., [enrollment (CA) certificate](/zpa/about-enrollment-ca-certificates)) for this provisioning key. For example, if your certificate expires, you might need to select a new certificate. All Private Service Edges deployed with this key have their certificates signed with this signing certificate.
[See image.](#img_edit)
- Click **Save**.
[]
![Edit Private Service Edge provisioning key to modify configuration fields](/downloads/zsdk/private-service-edge/maintaining-zsdk-private-service-edge-provisioning-keys/ZSDK-ProvisioningKeys-Edit.png)
[]
On the Private Service Edge Provisioning Keys page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Provisioning Keys):
- Click the **Delete** icon.
-
In the **Deletion** window, click **Delete**.
![Confirm the deletion of the provisioning key](/downloads/zsdk/private-service-edge/maintaining-zsdk-private-service-edge-provisioning-keys/ZSDK-ProvisioningKeys-delete.png)
- A confirmation window pops up briefly to describe the deleted provisioning key on the **Private Service Edge Provisioning Keys** page.