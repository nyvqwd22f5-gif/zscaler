# About Endpoint Data Loss Prevention
Source: https://help.zscaler.com/zia/about-endpoint-dlp
PDF: https://help.zscaler.com/pdf/com/en/1463226.pdf

[]You can use the Zscaler Endpoint Data Loss Prevention (DLP) policy to protect your organization from data loss on endpoints. Endpoint DLP policy complements [Zscaler DLP policy](/zia/about-data-loss-prevention) by extending the monitoring of sensitive data to the activities that end users take on endpoints (i.e., printing, saving to removable storage devices, saving to network shares, or uploading to personal cloud storage accounts).
You can use Zscaler custom and predefined DLP engines to detect sensitive data, allow or block user activities, and notify your organization's auditor when a user's activity on an endpoint triggers an Endpoint DLP rule. When you configure and activate Endpoint DLP policy in ZIA, endpoints automatically use Zscaler Client Connector to retrieve the policy from the Zscaler cloud. After that, the DLP policy is enforced and incidents are logged even if endpoints don't have a network connection.
To learn more, see [Step-by-Step Configuration Guide for Zscaler Endpoint DLP](/zia/step-by-step-endpoint-dlp).
Endpoint DLP policy provides the following benefits and allows you to:
- Monitor and prevent the leakage of sensitive data on endpoints (i.e., through printing, saving to removable storage devices, saving to network shares, or uploading to personal cloud storage accounts).
- Use Zscaler custom and predefined DLP engines to detect and take action on sensitive data.
- Monitor sensitive data and enforce Endpoint DLP rules even when an endpoint doesn't have a network connection.
About the Endpoint Data Loss Prevention Page
[]On the Endpoint Data Loss Prevention page (Policy > Endpoint Data Loss Prevention), you can do the following:
- Add and configure an [Endpoint DLP rule](/zia/configuring-endpoint-dlp-policy-rules).
- Select one of the following **View by** options to see the DLP policy rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in ascending order.
[See image.](#rule-order-dlp)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-dlp)
- Search for a DLP policy rule.
- View a list of all configured DLP policy rules for your organization. For policy rules, you can see the following:
- **Rule Order**: The policy rule's order number. DLP policy rules are evaluated in ascending numerical order. You can sort this column.
- **Channel**: The policy rule's resource channel (i.e., **Printing**, **Removable Storage Devices**, **Network Share**, and **Personal Cloud Storage**). You can sort this column.
- **Rule Status**: The policy rule's status (i.e., **Enabled** or **Disabled**). You can sort this column.
- **Exceptions**: The number of exceptions associated with the rule. To see the policy rule's exceptions, expand the rule in the first column. You can sort this column.
- **Rule Name**: The policy rule's name. You can sort this column.
- **Criteria**: The policy rule's criteria (i.e., DLP Engines, Device Groups, Departments, etc.)
- **Action**: The action taken when the rule is triggered (i.e., **Allow**, **Block**, or **Confirm**).
- **Severity**: The severity assigned to the rule (i.e., **High**, **Medium**, **Low**, or **Information**).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Expand to show the list of exception rules associated with a parent rule.
- [Edit, duplicate, or delete a DLP policy rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal). You can also add [an exception rule](/zia/configuring-endpoint-dlp-policy-rules).
![Endpoint Data Loss Prevention Page within the Admin Portal](/downloads/zia/policies/about-endpoint-data-loss-prevention/ZIA-endpoint-DLP-policy-page_MVP1.5.png)
[]![Screenshot of endpoint Data Loss Prevention Page with Rule Order view selected.](/downloads/zia/policies/about-endpoint-data-loss-prevention/ZIA-endpoint-DLP-policy-page-rule-order_MVP1.5.png)
[]![Screenshot of endpoint Data Loss Prevention Page with Rule Label view selected.](/downloads/zia/policies/about-endpoint-data-loss-prevention/ZIA-endpoint-DLP-policy-page-label-order_MVP1.5.png)