# About Outbound Email Policy
Source: https://help.zscaler.com/zia/about-outbound-email-policy
PDF: https://help.zscaler.com/pdf/com/en/1492691.pdf

The Zscaler Outbound Email Policy lets you use the same Zscaler Data Loss Prevention (DLP) policy tools that you use across other channels to protect your organization from data loss in outbound emails sent to external domains. You can use Zscaler custom and predefined DLP engines to detect sensitive data, allow or block user activities, or to add custom headers to emails that trigger an outbound email policy rule. If you don't use Zscaler DLP engines, the service functions instead as a filter, only flagging content based on specific criteria. To learn more, see [Step-by-Step Configuration Guide for Zscaler Outbound Email DLP](/zia/step-step-configuration-guide-zscaler-outbound-email-dlp).
The Zscaler Outbound Email Policy provides the following benefits and enables you to:
- Use Zscaler DLP tools and policies to monitor and prevent the leakage of sensitive data in outbound emails sent to external domains.
- Use Zscaler custom and predefined DLP engines to detect and take action on sensitive data.
- Use the Zscaler service as a filter to flag content based on specific criteria.
About the Outbound Email Policy Page
On the Outbound Email Policy page (Policy > Outbound Email Policy), you can do the following:
- [Add an Outbound Email Policy rule](/zia/configuring-outbound-email-policy-rules).
- Sort the list of policy rules by Rule Order or Rule Label.
- Search for an outbound email policy rule.
- View a list of all outbound email policy rules configured for your organization. For outbound policy rules, you can see:
- **Rule Order**: The rule order number for policy rules and exception rules. Outbound email policy rules are evaluated in ascending numerical order. You can sort this column.
- **Rule Name**: The policy rule's name. You can sort this column.
- **Criteria**: The policy rule's criteria (i.e., **DLP Engines**, **Device Groups**, **Departments**, etc.)
- **Action**: The action taken when the rule is triggered (i.e., **Allow**, **Block**, or **Custom Header Insertion**).
- **Label and Description**: The label and description of the rule, if available.
- **Exceptions**: The number of exceptions associated with a parent rule. To see the policy rule's exceptions, expand the rule order in the first column. You can sort this column.
- **Status**: The policy rule's status (i.e., **Enabled **or **Disabled**).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit, duplicate, or delete a policy rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal). You can also add [an exception rule](/zia/configuring-outbound-email-policy-rules).
![Tasks on the Outbound Email Policy Page](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Page.png)