# Managing a Nearby Sharing Rule
Source: https://help.zscaler.com/zia/managing-nearby-share-rule
PDF: https://help.zscaler.com/pdf/com/en/1525326.pdf

Nearby Sharing allows users to transfer files such as photos, videos, documents, and links between endpoints and nearby devices that have the Nearby Sharing feature enabled. Administrators can set up policy rules for Nearby Sharing to fully block file transfers to nearby devices, based on criteria such as users, department, endpoint, user's risk profile, or device trust level. The supported nearby sharing methods include:
- Windows: File transfer over Bluetooth, Nearby Share, and Phone Link.
- macOS: AirDrop, Universal Clipboard, iPhone Sync & Mirroring, and File transfer over Bluetooth.
When Bluetooth is disabled as part of nearby sharing blocking, it only applies to file transfer over Bluetooth. It does not apply to Bluetooth devices such as headphones, keyboards, mouses, etc., and does not block them.
The administrator can perform the following operations:
- [Add a Nearby Sharing Rule](#adding_nearby_sharing_rule)
- [Edit a Nearby Sharing Rule](#editing_nearby_sharing_rule)
- [Delete a Nearby Sharing Rule](#deleting_nearby_sharing_rule)
After the policy rules are set, they need to be activated for them to be enforced. To learn more, see [Activating Device Control Policy Rules](/zia/activating-device-control-policy-rules).
[]
- Go to **Analytics **> **Endpoint Data Scan** > **Device Control** > **Nearby Sharing**.
-
Click **Add Rule**.
The **Add Nearby Sharing Device Rule** window opens.
-
In the **Add Nearby Sharing Device Rule **window, specify settings:
- **Rule Name**: Enter a rule name for the device control policy.
- **Status**: Select to enable the rule. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Severity**: Select the severity of the violation from the drop-down menu (i.e., **High**, **Medium**, **Low**, or **Info**).
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. Rule evaluation stops at the first match.
- **Description**: Enter additional notes or information about the rule. The description cannot exceed 250 characters.
- **Criteria**:
- **Who**:
- **Users**: Choose **Any **to apply the rule to all users, or select one or more users to apply the rule to those users. You can also search one or more users to apply the rule to.
- **User Groups**: Choose **Any **to apply the rule to all user groups, or select one or more user groups to apply the rule to those user groups. You can also search one or more user groups to apply the rule to.
- **Departments**: Choose **Any **to apply the rule to all departments. You can also search for a specific department to apply the rule to.
- **What**:
- **Endpoint Name**: Choose **Any **to apply the rule to all endpoint devices. You can also search a specific endpoint device to apply the rule to.
- **Advanced**:
- **Device Trust Level**: Select the device trust level values (i.e., **High**, **Medium**, **Low**, or **Unknown**) to which the rule applies.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. A range of risk scores is grouped as a risk score level. By default, **Any **is selected. The following user risk score levels are available:
- **Low**: User risk scores ranging from 0 to 29.
- **Medium**: User risk scores ranging from 30 to 59.
- **High**: User risk scores ranging from 60 to 79.
- **Critical**: User risk scores ranging from 80 to 100.
- **Action**: Select an action (i.e., **Allow **or **Block**) for violation that matches the criteria in the rule.
[See Image.](#add_nearby_sharing)
- Click **Save **and [activate the change](/zia/activating-device-control-policy-rules).
[]
- Go to **Analytics **> **Endpoint Data Scan** > **Device Control** > **Nearby Sharing**.
-
Locate the nearby sharing rule in the list, then click the **Edit **icon.
The **Edit Nearby Sharing Device Rule** window opens.
-
In the **Edit Nearby Sharing Device Rule** window, edit the settings.
[See Image.](#edit_nearby_sharing_rule)
- Click **Save **and [activate the change](/zia/activating-device-control-policy-rules).
[]You can delete any rule by selecting the rule from the list and clicking the **Delete** icon.
![Nearby Sharing page in the Device Control tab showing the Delete Option](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/managing-nearby-share-rule/Delete_nearby_sharing.png)
You can edit the default nearby sharing device rule, but you cannot delete it.
![Adding Nearby Sharing Device Rule window and its parameters to set for the rule.](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/managing-nearby-share-rule/add_nearby_sharing_rule_new.png)
[]
![Edit Nearby Sharing Rule setting page.](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/managing-nearby-share-rule/edit_nearby_sharing_rule_new.png)
[]