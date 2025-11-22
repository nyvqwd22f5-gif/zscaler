# About SSL Inspection Policy
Source: https://help.zscaler.com/zia/about-ssl-inspection-policy
PDF: https://help.zscaler.com/pdf/com/en/1401846.pdf

[Watch a video about SSL Inspection Policy](https://fast.wistia.net/embed/iframe/asxajs13w9)
SSL Inspection policies are used to perform scanning of the SSL traffic based on the source and destination of the traffic.
The SSL Inspection policies provide the following benefits and enable you to:
- Simplify the deployment and ongoing operations of SSL Inspection.
- Address the compliance and operational environment requirements.
- Inspect traffic for malware and data loss.
- Allow, block, or restrict tenants.
Predefined Special Rules
Zscaler provides the following predefined special rules which you can enable or disable based on your requirements.
These rules are not editable and can only be implemented as is.
- **Zscaler-Recommended Exemptions rule**: Predefined rule to automatically exempt known destinations that cannot be SSL inspected. This rule is enabled by default.
- The Zscaler-recommended exemptions URL category contains a few dozen destinations that cannot be SSL inspected for various reasons, such as certificate pinning. This list also includes Zscaler-owned domains.
- To discover the traffic that is not getting SSL inspected due to this rule, you can search the weblogs using the SSL Policy Reason field for the reason *Not inspected because of Zscaler best practices*. The percentage of traffic that matches this rule is commonly very small and less than 1%.
- While it is recommended not to inspect these domains, you can always disable the rule with the Edit option. Alternatively, you can leave the rule enabled, but create higher order inspect rules if you want to inspect only specific domains outside the list.
- **O365 tenant restriction inspection rules**: Predefined rules to enable Office 365 Tenancy Restrictions for location and remote user traffic.
- **O365 One Click rule**: Predefined rule, controlled by the Microsoft-Recommended and Legacy Office 365 One Click setting.
- **UCaaS One Click rule**: Predefined rule, controlled by the UCaaS One Click configuration.
- []**Unauthorized Traffic Bypass for IoT Classifications rule**: Predefined rule to allow unauthorized traffic bypass SSL Inspection for IoT classifications in all IoT policy-enabled locations. This rule is disabled by default and cannot be deleted. You can modify the Rule Order, Admin Rank, Rule Status, Rule Label, and choose Evaluate Other Policies or Bypass Other Policies under Do Not Inspect Action for this rule and cannot edit other attributes. You can enable this rule to temporarily allow unauthorized traffic to bypass SSL Inspection, so that Zscaler AI/ML can classify devices.
About the SSL Inspection Policy Page
On the SSL Inspection Policy page (**Policy** > **SSL Inspection**), you can do the following:
- [Add an SSL Inspection rule](/unified/configuring-ssl-inspection-policy).
- View the recommended SSL Inspection policy.
[See image.](#recommended-ssl-inspection-policy)
- Select one of the following **View by** option to see the SSL Inspection rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-SSL)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-SSL)
- Search for an SSL Inspection rule.
- View a list of all SSL Inspection rules. For each SSL Inspection rule, you can view:
- **Rule Order**: The order of the rule.
- **Admin Rank**: The admin rank of the rule.
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria defined for the rule.
- **Action**: The action configured for the rule.
- **Label and Description**: The label and description of the policy rule, if available.
- Edit or duplicate an SSL Inspection rule.
- [Modify the table and its columns](/zia/using-tables).
- Go to the [Intermediate CA Certificates](/zia/about-intermediate-ca-certificates) page.
![SSL Inspection page](/downloads/tech-pubs-drafts/zia-draft-articles/about-ssl-inspection-policy-doc-53116/ssl-inspection-callout-final.png)
[]
![Recommended SSL Inspection Policy](/downloads/tech-pubs-drafts/zia-draft-articles/about-ssl-inspection-policy-doc-53327/ssl-inspection-recc-policy.png)
[]![SSL Inspection Policy Page with Rule Order view selected.](/downloads/zia/policies/ssl-inspection/about-ssl-inspection-policy/ZIA-SSL-Inspection-Policy-Page-Viewby-Rule-Order.png?1654766202)
[]![SSL Inspection Policy Page with Rule Label view selected.](/downloads/zia/policies/ssl-inspection/about-ssl-inspection-policy/zia-about-ssl-inspection-policy-rule-label.png)