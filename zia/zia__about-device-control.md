# About Device Control
Source: https://help.zscaler.com/zia/about-device-control
PDF: https://help.zscaler.com/pdf/com/en/1515211.pdf

Zscaler Device Control involves managing and regulating the access and usage of devices such as removable storage (e.g., USB drives, external hard drives), printers and nearby sharing devices within an organization. By using device control, organizations can minimize the risk of data exfiltration by blocking unauthorized users from accessing these devices. Implementing device control policy rules is crucial to enhancing security, maintaining productivity, and ensuring compliance.
Device Control provides the following benefits and enables you to:
- Intercept as soon as the device is plugged into the endpoint, even before data is exfiltrated, thereby preventing sensitive information from leaving the network.
- Control which device can be used and by whom.
You can set device control policy rules for the following types of devices:
- Removable Storage Devices
- Printers
- Nearby Sharing
Device Control Policy Enforcement
Administrators can define and set up device control policy rules (which differ from the endpoint DLP rules) for the usage of devices based on rule criteria, such as user, department, endpoint, device, etc. Device Control includes a default rule that administrators can customize by modifying its action, severity, description, and end user notifications. The default rules cannot be deleted, but they can be edited. When the default rule is disabled, no other rules are enforced.
Administrators can also edit or delete device control policy rules to align with their specific use cases or requirements. To learn more, see [Managing a Removable Storage Rule](/zia/adding-editing-deleting-removable-storage-rule), [Managing a Printer Rule](/zia/adding-editing-deleting-printer-rule), and [Managing a Nearby Sharing Rule](/zia/managing-nearby-share-rule).
The Device Control policy rules are evaluated as follows:
- Rules are evaluated in sequential order, starting from rule order 1.
- If a rule matches, the policy is enforced based on that rule.
- If no rules match, the default rule is applied.
About the Device Control Page
On the Device Control page (Analytics > Endpoint Data Scan > Device Control), you can do the following:
- Select Removable Storage, Printers, or Nearby Sharing. By default, the Removable Storage page is displayed.
- Add a rule. To learn more, see [Managing a Removable Storage Rule](/zia/adding-editing-deleting-removable-storage-rule), [Managing a Printer Rule](/zia/adding-editing-deleting-printer-rule), and [Managing a Nearby Sharing Rule](/zia/managing-nearby-share-rule).
- View the list of device control rules on the respective page.
- **Rule Order**: The policy rule order number. It reflects the rule’s place in the order. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on). If no rule matches, then the default rule applies.
- **Rule Name**: The policy rule name.
- **Criteria**: The policy rule's criteria (i.e., **Users**, **Departments**, **Endpoint Name**, **Removable Storage**, **Device Trust Level**, **User Risk Profile**, etc).
- **Status**: The policy rule's status (enabled or disabled). An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Severity**: The severity assigned to the policy rule (i.e., **High**, **Medium**, **Low**, or **Information**).
- **Action**: The action taken when the policy rule is triggered (i.e., **Allow**, **Block**, or **Read-Only**).
- Customize columns: Rearrange the columns and search for column names on the page.
![This image shows the Device Control Page](/downloads/zia/policies/endpoint-data-loss-prevention/endpoint-data-scan/device-control/about-device-control/Device_Control_page.png)