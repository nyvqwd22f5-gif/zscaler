# Managing a Printer Rule
Source: https://help.zscaler.com/zia/managing-printer-rule
PDF: https://help.zscaler.com/pdf/com/en/1515411.pdf

Administrators can define and set up policy rules for device usage based on the rule's criteria (i.e., Users, Departments, Endpoint Name, Printers, Device Trust Level, User Risk Profile, etc.) The administrator can perform the following operations:
- [Add a Printer Rule](#adding_printer_rule)
- [Edit a Printer Rule](#editing_printer_rule)
- [Delete a Printer Rule](#deleting_printer_rule)
After the policy rules are set, they need to be activated for them to be enforced. To learn more, see [Activating Device Control Policy Rules](/zia/activating-device-control-policy-rules).
[]
- Go to **Analytics **> **Endpoint Data Scan** > **Device Control** >** Printer**.
-
Click **Add Rule**.
The **Add Printer Rule** window opens.
-
Specify settings for the printer rule.
- **Rule Name**: Enter a rule name for the printer rule.
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
- **Printers**: Select **Any **or a specific printer from the drop-down menu. You can search for printers. You can also do the following:
-
**Add New Printer**: Add a printer to the current rule.
[See Image.](#add_new_printer_img)
- **Advanced**:
- **Device Trust Level**: Select the device trust level values (i.e., **High**, **Medium**, **Low**, or **Unknown**) to which the rule applies.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. A range of risk scores is grouped as a risk score level. By default, **Any **is selected. The following user risk score levels are available:
- **Low**: User risk scores ranging from 0 to 29.
- **Medium**: User risk scores ranging from 30 to 59.
- **High**: User risk scores ranging from 60 to 79.
- **Critical**: User risk scores ranging from 80 to 100.
- **Action**: Select an action (i.e., **Allow **or **Block**) for violation that matches the criteria in the rule.
- **End User Notification**: Select whether to **Show **or **Hide **a notification about the violation on the endpoint. This option is applicable when choosing the **Block **action.
[See Image.](#add_printer_rule_img)
- Click **Save** and [activate the change](/zia/activating-device-control-policy-rules).
[]
- Go to **Analytics **> **Endpoint Data Scan** > **Device Control** > **Printer**.
-
Locate the printer rule in the list, then click the **Edit **icon.
The **Edit Printer Rule** window opens.
-
Edit the settings for the selected rule as required.
[See Image.](#edit_printer_rule_img)
- Click **Save **and [activate the change](/zia/activating-device-control-policy-rules).
[]You can delete any rule by selecting the rule from the list and clicking the **Delete** icon.
![This image shows the Deleting Printer Rules](/downloads/zia/policies/endpoint-data-loss-prevention/about-inventory/Deleting_printer_rules.png)
You can edit the default printer rule, but you cannot delete it.
[]![This image shows the Add Printer Rule window](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/managing-printer-rule/add_printer_rule_new.png)
![This image shows the Edit Printer Rule window](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/managing-printer-rule/edit_printer_rule_new.png)
[]
![This image shows the Add New Printer to the rule window](/downloads/zia/policies/endpoint-data-loss-prevention/about-inventory/Add_new_printer.png)
[]