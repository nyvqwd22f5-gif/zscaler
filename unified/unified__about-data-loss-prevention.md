# About Data Loss Prevention
Source: https://help.zscaler.com/unified/about-data-loss-prevention
PDF: https://help.zscaler.com/pdf/com/en/1492931.pdf

[]Corporate data can be leaked in different ways (i.e., through web mail, cloud storage, social media, and a variety of other applications). You can use the Zscaler DLP policy to protect your organization from data loss.
If your organization has a third-party DLP solution, Zscaler can forward information about transactions that trigger DLP policies to your third-party solution. Zscaler uses secure Internet Content Adaptation Protocol (ICAP) to do this. However, the Zscaler service does not take ICAP responses from your DLP solution. Zscaler only monitors or blocks content according to the policy you configure, then forwards information about transactions so that your organization can take any necessary remediation steps.
Data loss prevention provides the following benefits and enables you to:
- Use Zscaler DLP policy to monitor and prevent the leakage of sensitive data.
- Use Zscaler custom and predefined DLP engines to detect and take action on sensitive data.
- Forward information about transactions that trigger DLP policies to your third-party DLP solution.
The following are the different types of DLP policy rules you can configure. Your policy can use one or more of these options simultaneously.
- [Monitor or block data using Zscaler DLP engines](#option1)
- [Monitor or block data using Zscaler DLP engines, then forward information to a third-party DLP solution](#opt2)
- [Monitor or block data based on specific criteria, then forward information to a third-party DLP solution](#opt3)
- [Monitor or block data based on data size](/unified/monitoring-or-blocking-outbound-content-data-size) to leverage Zscaler's DLP policy without scanning for specific data within the content.
To see how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement). To learn more about Endpoint DLP, see [About Endpoint Data Loss Prevention (DLP)](/unified/about-endpoint-data-loss-prevention).
About the Data Loss Prevention Page
The appearance of the Data Loss Prevention page varies slightly, depending on whether Evaluate All Rules mode is enabled in your organization. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
On the Data Loss Prevention page (Policies > Data Protection > Policy > Inline Controls > Data Loss Prevention), you can do the following:
- Add and [configure a DLP policy rule](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
- Select one of the following **View by** options to see the DLP policy rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#all-rules-dlp)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#all-rules-label-dlp)
- Search for a DLP policy rule.
- View a list of all configured DLP policy rules and exception rules that were configured for your organization. Exception rules are child rules that allow you to exclude specific users or groups in your organization that need to perform tasks as part of a necessary workflow that might otherwise violate inline DLP policy. For policy rules and exception rules, you can see:
-
**Rule Order**: The policy rule's order number.
Rule order is not enforced for parent rules when the Zscaler service is configured to evaluate all rules. Exception rule evaluation stops at the first match, and an exception replaces a parent rule upon match. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
- **Rule Name**: The name of the rule. You can sort this column.
- **Criteria**: The rule's criteria (i.e., DLP Engines, URL Categories, Protocols, etc.)
- **Action**: Displays whether the rule is enabled or disabled.
- **Label and Description**: The label and description of the rule, if available.
-
Expand to show the list of exception rules associated with a parent rule.
Parent rules and exception rules apply only when Evaluate All Rules mode is enabled. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/unified/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
- [Modify the table and its columns](/unified/using-tables).
- Add an exception rule to a parent rule (Evaluate All Rules Mode only).
- Edit, duplicate, or delete a rule.
![Data Loss Prevention page with Evaluate All Rules mode enabled](/downloads/unified/policies/internet-saas/data-protection/data-loss-prevention/about-data-loss-prevention/ZIA-DLP-Policy-Page-EvalAllRules.png)
[]With this option, Zscaler:
- Scans content with Zscaler DLP engines for specific data.
- Allows or blocks the transaction.
- (Optional) Sends your auditor a notification.
The following is an illustration of the process that occurs when you block data using Zscaler DLP engines. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection).
![Blocking data with Zscaler DLP engines Diagram](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/about-data-loss-prevention-dlp/zia-dlp-zscaler-engine.png)
[]With this option, Zscaler:
- Scans content with Zscaler DLP engines for specific data.
- Allows or blocks the transaction.
- (Optional) Sends your auditor a notification.
- Sends the following information about the violation to your third-party DLP solution via secure ICAP:
- Client IP and username of users attempting to send data (via ICAP X-headers).
- A copy of the HTTP POST request that contains the relevant file or content (if content is from HTTP Form data or a text file). The host URL that the user was sending content to is also included here.
The following is an illustration of the process that occurs when you block data using Zscaler DLP engines and forward information to your third-party DLP solution. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection).
![Zscaler DLP Engines Third-Party Diagram](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/about-data-loss-prevention-dlp/zia-dlp-third-party.png)
[]With this option, Zscaler does not use its DLP engines. Instead, the service does the following:
- Detects content that meets the criteria you select (for example, destination URL category or file type).
- Allows or blocks the content.
- (Optional) Sends your auditor a notification.
- Sends the following information about the violation to your third-party DLP solution via secure ICAP:
- Client IP and username of users attempting to send data (via ICAP X-headers).
- A copy of the HTTP POST request that contains the relevant file or content (if content is from HTTP Form data or a text file). The host URL that the user was sending content to is also included here.
The following is an illustration of the process that takes place when you configure DLP policies for this option. To learn more, see [Configuring DLP Policy Rules without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection).
![DLP Policies Solutions Diagram](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/about-data-loss-prevention-dlp/zia-dlp-third-party-content.png)
[]![Screenshot of Data Loss Prevention Page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/about-data-loss-prevention/ZIA-DLP-Policy-Page-Viewby-Rule-Order-Eval-All-Rule-Mode.png)
[]![Screenshot of Data Loss Prevention Page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/about-data-loss-prevention/ZIA-DLP-Policy-Page-Viewby-Rule-Label-Eval-All-Rule-Mode.png)