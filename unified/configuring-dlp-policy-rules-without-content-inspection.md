# Configuring DLP Policy Rules without Content Inspection
Source: https://help.zscaler.com/zia/configuring-dlp-policy-rules-without-content-inspection
PDF: https://help.zscaler.com/pdf/com/en/1400126.pdf

This article does not apply to organizations with Evaluate All Rules mode enabled. To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
When you configure a Rule Without Content Inspection policy, you do not use Zscaler Data Loss Prevention (DLP) engines to detect data. Instead, Zscaler detects content based on criteria you specify, then sends information about that content to your organization's third-party DLP solution.
To configure a DLP policy rule without content inspection:
- [1. Configure DLP notification templates](/zia/how-do-i-configure-dlp-notifications) if you want to email notifications to your organization's auditor when your users' transactions violate DLP policy rules.
- [2. (Optional) Configure ICAP receivers](/zia/adding-icap-receiver) if you want to forward information about transactions that violate DLP policy to your third-party solution. Skip this step if you don't have a third-party DLP solution or if you don't want to forward content.
- [3. (Optional) Configure a Zscaler Incident Receiver](/zia/about-zscaler-incident-receiver) to forward information about content that triggers an outbound email policy rule to your Incident Receiver via secure Internet Content Adaptation Protocol (ICAP). Zscaler does not take ICAP responses from your Incident Receiver; instead, the service only monitors or blocks content according to the policy you configure, then forwards information about activities so that your organization can take necessary remediation steps.
- [4. (Optional) Configure Cloud-to-Cloud Incident Forwarding](/zia/configure-dlp-cloud-cloud-incident-forwarding) to send metadata and evidence about transactions that violate a DLP policy rule directly to your public cloud storage without deploying appliances.
- [5. Define your policy rules.](#Add)
[]
- Go to **Policy **>** Data Loss Prevention**.
- Click **Add DLP Rule**.
- In the **Add DLP Rule** window:
- Enter the following **DLP Rule** attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [admin ranking](/zia/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/what-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule or use the default name.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
- Define the following **Criteria**:
-
**Content Matching**: Select **None** to use a third-party DLP solution instead of Zscaler DLP engines to inspect content. In this scenario, the Zscaler service does not scan the content with its DLP engines but functions as a filter, only forwarding content based on specific criteria.
[See image.](#without-content-inspection)
- **Source IP Groups**: Select **Any** to apply the rule to all [source IP groups](/zia/about-source-ip-groups), or select any number of source IP groups. You can also search for source IP groups or click the **Add** icon to add a new [source IP group](/zia/configuring-source-ip-groups).
- **URL Categories**:** **Select **Any** to apply the rule to all [URL categories](/zia/about-url-categories), or select any number of URL categories. You can search for URL categories or click the **Add** icon to create a new URL category. With this option, you can have Zscaler forward content being sent to specific URL categories (for example, content going to websites in the Adult Material URL category).
You can also select [custom TLD categories](/zia/about-tld-categories) from this field.
- **Cloud Applications**:** **Select **Any** to apply the rule to all cloud applications, or select any number of cloud applications. You can also search for applications. With this option, you can have Zscaler forward content being sent to specific cloud applications (e.g., Facebook).
By default, this field displays the first 100 cloud applications. The subsequent 100 cloud applications are displayed when you select **Click to see more** following the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
The DLP policy applies AND logic to the URL Categories and Cloud Applications fields when inspecting your organization's traffic. In order for a DLP rule to trigger, the Zscaler service must detect the rule’s selected URL categories and cloud applications in a transaction.
- **Email Recipient Domain Profiles** (Gmail and Outlook): Choose **Include** to apply the rule only to the selected [domain profiles](/zia/about-domain-profiles), or choose **Exclude** to apply the rule to all other domain profiles and not selected domain profiles. You can select up to 8 domain profiles, and you can search for domain profiles.
- **Cloud Application Instances**: Select the cloud application instances to which the rule applies. You can select a maximum of 8 instances per rule.
The cloud application instance appears only if its parent application is selected as the cloud application.
-
**ZPA Application Segment:** Select **Any** to apply the rule to all [Zscaler Private Access (ZPA) application segments](/zpa/configuring-application-segments), or select up to 255 ZPA application segments. You can also search for ZPA application segments. The list displays only those ZPA application segments that have the [Source IP Anchor](/zia/understanding-source-ip-anchoring)** **option enabled.
If you select the** Inspect App Segments** option from the list, then the configured rule applies to all the ZPA application segments paired to your ZIA tenant. This option is only available if the **SIPA App Segments** subscription is enabled for your organization.
[See image.](#zpa-application-segment-image)
- **Outbound Data**:** **Choose **Select File Types **if you want to select the file types the rule applies to, or **All **if you want the rule to apply to all outbound data, regardless of file type.
-
**File Type**:** **This is only applicable if you choose **Select File Types**.** **Select the file types you want the rule to apply to. You can select any number of file types and also search for file types. You can also select [custom file types](/zia/configuring-custom-file-types) you have previously configured.
Zscaler-defined file types are considered before custom file types and custom files inside archives are not detected.
- **Minimum Data Size**:** **Enter the data size a file must exceed in order for the rule to apply. For example, if you enter 100, the rule applies only if a file exceeds 100 KB. The default minimum data size, 0 KB, means that the rule applies to files of any size.
- **Users**: You can specify how the DLP rule applies to your [users](/zia/about-users).
- Choose **Include** to apply the rule to selected users and no other users. From the drop-down menu, choose **Any** to apply the rule to all users or select up to 32 users.
- Choose **Exclude** to apply the rule to all other users and not selected users. You can select up to 256 users.
When selecting users, you can search for users or click the **Add** icon to add a new user. If you’ve enabled the [Policy for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic), you can also select special users to apply this rule to all unauthenticated users or select specific types of unauthenticated users.
- **Groups**:** **You can specify how the DLP rule applies to your [groups](/zia/about-groups).
- Choose **Include** to apply the rule to selected groups and no other groups. From the drop-down menu, choose **Any** to apply the rule to all groups or select up to 32 groups.
- Choose **Exclude** to apply the rule to all other groups and not selected groups. You can select up to 256 groups.
When selecting groups, you can search for groups or click the **Add** icon to add a new group.
- **Departments**:** **You can specify how the DLP rule applies to your [departments](/zia/about-departments).
- Choose **Include** to apply the rule to selected departments and no other departments. From the drop-down menu, choose **Any** to apply the rule to all departments or select up to 32 departments.
- Choose **Exclude** to apply the rule to all other departments and not selected departments. You can select up to 256 departments.
When selecting departments, you can search for groups or click the **Add** icon to add a new department. If you’ve enabled the [Policy for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic), you can also select special departments to apply this rule to all unauthenticated transactions.
Any rule that applies to [unauthenticated traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic) must apply to all groups and departments. So, if you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, select **Any **from the drop-down menus for **Groups** and **Departments**.
The DLP policy applies OR logic to the Users, Groups, and Departments fields when inspecting your organization’s traffic. In order for the DLP rule to trigger, the Zscaler service must detect at least one of the rule’s selected users, groups, or departments.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value ignores this criterion in the policy evaluation.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
-
**Locations**: Select **Any** to apply the rule to all [locations](/zia/about-locations), or select up to 32 locations. You can also search for a location or click the **Add **icon to add a new location.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/zia/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Time**: Select **Always** to apply this rule to all [time intervals](/zia/about-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add **icon to add a new time interval.
- **Protocols**: Select the protocols to which the rule applies.
- **HTTP**: Data transactions and file uploads from HTTP websites.
- **HTTPS**: Data transactions and file uploads from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: Data transactions and file uploads from native FTP servers.
- **WebSocket**: Data transactions from WebSocket websites.
- **WebSocket SSL/TLS**: Data transactions from WebSocket websites encrypted by SSL/TLS.
The WebSocket protocol is supported only for the Microsoft Copilot application.
- **Workload Groups**: Select up to 8 workload groups for which you want to apply the rule. You can also search for a workload group. Selecting **None** ignores workload groups when the policy is evaluated. To learn more, see [About Workload Groups](/zia/about-workload-groups).
- (Optional) Configure the **DLP Incident Receiver **settings:
- **ICAP**: Select the applicable ICAP receiver from the drop-down menu. You must [configure ICAP receivers](/zia/adding-icap-receiver) to complete this step.
- **Zscaler Incident Receiver**: Select the applicable Zscaler Incident Receiver from the drop-down menu. You must configure your [Zscaler Incident Receivers](/zia/configuring-zscaler-incident-receiver) to complete this step.
- **Cloud-to-Cloud Forwarding**: Select the applicable **Tenant** and **Cloud-to-Cloud Forwarding Configuration** from the drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/zia/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
Ensure that in your third-party DLP solution, you have configured a policy rule that detects the same file type as the rule you configure here. For example, if you configure an External DLP Engine rule that specifies PDFs for file type criteria, you must also configure a rule in your third-party solution that specifies PDFs as a file type criterion.
Otherwise, the information that the Zscaler service sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. The rules do not need to correspond exactly in other criteria. For example, an External DLP Engine rule blocks PDFs going to a specific URL category. The rule in your on-premises DLP solution must also block PDFs, but need not specify the same URL category.
- Select the **Action** for the rule:
- **Allow**: The service allows and logs the transaction.
- **Block**: The service blocks and logs the transaction.
- **Confirm: **Users can justify the transaction to continue, or cancel the transaction altogether; in both cases, the service logs the transaction accordingly. Admins can choose to display a default template or a custom template. To learn more, see [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates).
If the confirmation message times out without the end user taking action, the Zscaler service automatically cancels the transaction. To learn more, see [Configuring User Confirmation Notification Templates](/zia/configuring-user-confirmation-notification-templates).
- (Optional) Define the following **Notification** settings:
- Configure an email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- **Email Auditor Type**: Select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select or search for **Email Auditor i**f the auditor is from a hosted database.
- Select **Auditor Email Address** if the auditor is external, and enter the auditor’s email address.
- **Email Notification Template**: Select a [notification template](/zia/configuring-dlp-notification-templates) from the drop-down menu.
- Configure the End User Notification (EUN) for the rule. The type of EUN messages that appear on the endpoint depends on the **Action** configured for the rule.
- **End User Notification**: Select **Show** to show an EUN message on endpoints when content triggers the DLP policy rule, or select **Hide** if you don't want an EUN message to appear.
- **Custom Message**: Select **Default** to use the default EUN message configured for inline web DLP, or select a custom EUN message from the drop-down menu. You can also search for custom messages or click the **Add** icon to add a new custom message.
- (Optional) Enter a **Description**. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn how to use the Zscaler DLP engines to detect data and also forward information about the data to your third-party DLP solution, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-policy-using-zscaler-dlp-engines).
[]![Screenshot of Zscaler Internet Access (ZIA) Add DLP Rule Criteria with Content Matching set to none](/downloads/zia/policies/data-loss-prevention/configuring-dlp-policy-rules-without-content-inspection/select-none.png)
[]![Screenshot of Zscaler Internet Access (ZIA) Add DLP Rule with Click to See More in the Cloud Applications Field](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/configuring-dlp-policy-rules-without-content-inspection/ZIA-Add-DLP-Rule-See-More.png)
![Screenshot of the Inspect App Segments option for the ZPA Application Segment field](/downloads/zia/policies/data-loss-prevention/configuring-dlp-policy-rules-without-content-inspection/zia-configuring-dlp-rules-without-content-inspection-zpa-app-segments-inspect-app-segments-option.png)
[]