# Configuring Outbound Email Policy Rules
Source: https://help.zscaler.com/unified/configuring-outbound-email-policy-rules
PDF: https://help.zscaler.com/pdf/com/en/1503701.pdf

You can use Zscaler Outbound Email Policy to detect data, allow or block activities, and add custom headers when content in an email sent to an external domain triggers an outbound email policy rule. You can also create exception rules, which are child rules that allow you to exclude specific users or groups in your organization that must perform tasks as part of a necessary workflow that might otherwise violate outbound email policy.
When content triggers outbound email policy rules, the Zscaler service adds headers to those emails and sends them back to your email server for enforcement. Depending on how outbound email policy rules are configured, the headers instruct your email server to take a default action (i.e., allow or block content), or an action mapped to a custom header configured on the server.
To learn more, see [Configuring Microsoft Exchange for Zscaler Outbound Email DLP](/unified/configuring-microsoft-exchange-zscaler-outbound-email-dlp) and [Configuring Gmail for Zscaler Outbound Email DLP](/unified/configuring-gmail-zscaler-outbound-email-dlp).
If your organization uses a [Zscaler Incident Receiver](/unified/about-zscaler-incident-receiver), the service can forward information about content that triggers an outbound email policy rule to your Incident Receiver via secure Internet Content Adaptation Protocol (ICAP). However, Zscaler does not take ICAP responses from your Incident Receiver; instead, the service only monitors or blocks content according to the policy you configure, then forwards information about activities so that your organization can take necessary remediation steps.
To configure an Outbound Email Policy rule:
- [1. Review configuration steps.](/unified/step-step-configuration-guide-zscaler-outbound-email-dlp) Use the step-by-step guide to familiarize yourself with Zscaler Data Loss Prevention (DLP), and as a roadmap for setting up your outbound email policy.
- [2. Configure DLP dictionaries and engines, if necessary.](/unified/about-dlp-dictionaries) Use DLP dictionaries and engines as they are or modify them to suit your needs. You can also create custom dictionaries or engines. Skip this step if you don't want to modify or create custom DLP dictionaries and engines.
- [3. (Optional) Configure a Zscaler Incident Receiver](/unified/about-zscaler-incident-receiver) to forward information about content that triggers an outbound email policy rule to your Incident Receiver via secure Internet Content Adaptation Protocol (ICAP). Zscaler does not take ICAP responses from your Incident Receiver; instead, the service only monitors or blocks content according to the policy you configure, then forwards information about activities so that your organization can take necessary remediation steps.
- [4. (Optional) Configure Cloud-to-Cloud Incident Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to send metadata and evidence about transactions that violate a DLP policy rule directly to your public cloud storage without deploying appliances.
- [5. Define your policy rules.](#Rules)
- [(Optional) 5. Define exception rules.](#ExceptionRules)
[]
- Go to **Policies **>** Data Protection **>** Policy** >** Outbound Email Controls **> **Data Loss Prevention**.
- Click **Add DLP Rule**.
- In the **Add DLP Rule** window:
- Enter the following **DLP Rule** attributes:
- **Rule Order**: All parent rules are evaluated. If multiple rules match, the rule with the most restrictive action and highest rule order is applied. Exception rule evaluation stops at the first match, and an exception replaces a parent rule upon match.
- **Rule Name**: Enter a unique name for the DLP rule or use the default name.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a [rule label](/unified/about-rule-labels) to associate it with the rule. You can also search for rule labels.
- **Severity**: Select the severity of the violation from the drop-down menu (i.e., **High**, **Medium**, **Low**, or **Information**).
- Define the following **Criteria**:
- **Content Matching**: Select **Select DLP Engines** to select up to 4 engines. You can also search for DLP engines. If you select **None**, then the Zscaler service doesn't use DLP engines to scan the content; instead, the service functions as a filter, only flagging content based on the criteria you specify.
- **Content Locations**: Specify where the Zscaler service should look for sensitive data (i.e., **Email Attachments, Email Body,** or **Email Subject**).
- **File Type**: From the drop-down menu, choose the file types for the rule. The list of available file types changes based on whether you're using DLP engines for content inspection. You can create policy rules that apply only to content being sent via specific file types. Zscaler DLP engines can scan files of up to 100 MB. For an archived file, the size of individual files when decompressed can also be a maximum of 100 MB.
- **Users**: You can specify how the policy rule applies to your [users](/unified/about-users). Select **Any **to apply the rules to all users or select up to 32 users. You can also search for users.
- **Groups**:** **You can specify how the policy rule applies to your [groups](/unified/about-groups). Select **Any** to apply the rules to all groups or select up to 32 groups. You can also search for groups.
-
**Departments**:** **You can specify how the policy rule applies to your [departments](/unified/about-departments). Select **Any** to apply the rules to all departments or select up to 32 departments. You can also search for departments.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value i
-
**User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value ignores this criterion in the policy evaluation.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
- **Minimum Data Size (KB)**: Enter the minimum size requirement that data must meet before the policy rule applies. The default minimum data size, 0 KB, means there is no minimum data size requirement.
- **Email Recipient Domain Profiles**: Select up to 8 [domain profiles](/unified/about-email-profiles) to which this rule applies. You can also search for domain profiles.
- **Email Recipient Profiles**: Select up to 8 [recipient profiles](/unified/about-email-profiles) to which this rule applies. You can also search for recipient profiles.
- **Time**: Select **Always** to apply this rule to all [time intervals](/unified/about-time-intervals), or select up to two time intervals. You can also search for a time interval.
- (Optional) Configure the **DLP Incident Receiver **settings:
- **Zscaler Incident Receiver**: Select the applicable Zscaler Incident Receiver from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
- **Cloud-to-Cloud Forwarding**: Select the applicable **Tenant** and **Cloud-to-Cloud Forwarding Configuration** from the drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Select the **Action** for the rule:
- **Allow**: The Zscaler service includes the `X-Zscaler-Block:0` default header (where `0`=Allow) to allow the content on emails that trigger the outbound email policy rule. The email server uses the header for enforcement.
- **Block**: The Zscaler service includes the `X-Zscaler-Block:1` default header (where `1`=Block) to block the content on emails that trigger the outbound email policy rule. The email server uses the header for enforcement.
-
**Custom Header Insertion**: The service includes a custom header on emails that trigger the outbound email policy rule. Custom headers are designed to take an action that is mapped to the header on the email server. The **Custom Header **format must be `X-name:value`, where `0`=Allow and `1`=Block (e.g., `X-Zscaler-Quarantine:1`).
To learn more, see [Configuring Microsoft Exchange for Zscaler Outbound Email DLP](/unified/configuring-microsoft-exchange-zscaler-outbound-email-dlp) and [Configuring Gmail for Zscaler Outbound Email DLP](/unified/configuring-gmail-zscaler-outbound-email-dlp).
- (Optional) Define the following **Notification** settings:
- Configure an email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- **Auditor Type**: Select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- **Auditor**: If the auditor is from a hosted database, select or search for the auditor.
- **Auditor Email Address**: If the auditor is external, enter the auditor’s email address.
- **Notification Template**: Select a [notification template](/unified/configuring-dlp-notification-templates) from the drop-down menu.
- (Optional) For **Description**, enter additional notes or information about the rule. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
For example, if an outbound email policy rule using predefined Zscaler DLP engines is configured as shown in the following image, the Zscaler service blocks all email attachments that:
- Contain medical information
- Are any file type
- Are sent by HR Department members.
[See image.](#parent-rule-hipaa-violation)
The Zscaler service doesn't forward information to an Incident Receiver.
[]Exception rules allow you to exclude specific users or groups in your organization that need to perform tasks as part of a necessary workflow that might otherwise violate outbound email policy rules. You can add up to 32 exception rules to any outbound email policy parent rule. The exception rules automatically inherit the rule name from the parent rule, but you can customize other exception rule settings.
To define an exception rule:
- Go to **Policies **>** Data Protection **>** Policy** >** Outbound Email Controls **> **Data Loss Prevention**.
- Click **Add DLP Rule**.
- In the **Add DLP Rule** window:
- Enter the following **DLP Rule** attributes:
- **Rule Order**: All parent rules are evaluated. If multiple rules match, the rule with the most restrictive action and highest rule order is applied. Exception rule evaluation stops at the first match, and an exception replaces a parent rule upon match.
- **Rule Name**: This field is inherited from the parent rule and cannot be changed.
- **Exception Rule Name**: Enter a name for the exception rule.
- **Rule Status**: An enabled exception rule is actively enforced. A disabled exception rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next exception rule.
- **Rule Label**: Select a [rule label](/unified/about-rule-labels) to associate it with the exception rule. You can also search for rule labels.
- **Severity**: Select the severity of the violation from the drop-down menu (i.e., **High**, **Medium**, **Low**, or **Information**).
- Define the following **Criteria**:
- **Content Matching**: Select **Select DLP Engines** to select up to 4 engines. You can also search for DLP engines. If you select **None**, then the Zscaler service doesn't use DLP engines to scan the content; instead, the service functions as a filter, only flagging content based on the criteria you specify.
- **Content Locations**: Specify the where the Zscaler service should look for sensitive data (i.e., **Email Attachments, Email Body,** or **Email Subject**).
- **File Type**: From the drop-down menu, choose the file types for the exception rule. The list of available file types changes based on whether you're using DLP engines for content inspection. You can create policy rules that apply only to content being sent via specific file types. Zscaler DLP engines can scan files of up to 100 MB. For an archived file, the size of individual files when decompressed can also be a maximum of 100 MB.
- **Users**: You can specify how the policy rule applies to your [users](/unified/about-users). Select **Any **to apply the rules to all users or select up to 32 users. You can also search for users.
- **Groups**:** **You can specify how the policy rule applies to your [groups](/unified/about-groups). Select **Any** to apply the rules to all groups or select up to 32 groups. You can also search for groups.
-
**Departments**:** **You can specify how the policy rule applies to your [departments](/unified/about-departments). Select **Any** to apply the rules to all departments or select up to 32 departments. You can also search for departments.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value i
-
**User Risk Profile**: Select the user risk score levels to which the exception rule applies. Selecting no value ignores this criterion in the policy evaluation.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
- **Minimum Data Size (KB)**: Enter the minimum size requirement that data must meet before the exception rule applies. The default minimum data size, 0 KB, means there is no minimum data size requirement.
- **Email Recipient Domain Profiles**: Select up to 8 [domain profiles](/unified/about-email-profiles) to which this exception rule applies. You can also search for domain profiles.
- **Email Recipient Profiles**: Select up to 8 [recipient profiles](/unified/about-email-profiles) to which this exception rule applies. You can also search for recipient profiles.
- **Time**: Select **Always** to apply this rule to all [time intervals](/unified/about-time-intervals), or select up to two time intervals. You can also search for a time interval.
- (Optional) Configure the **DLP Incident Receiver **settings:
- **Zscaler Incident Receiver**: Select the applicable Zscaler Incident Receiver from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
- **Cloud-to-Cloud Forwarding**: Select the applicable **Tenant** and **Cloud-to-Cloud Forwarding Configuration** from the drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
-
Select the **Action** for the exception rule:
- **Allow**: The Zscaler service includes the `X-Zscaler-Block:0` default header (where `0`=Allow) to allow the content on emails that trigger the outbound email policy rule. The email server uses the header for enforcement.
- **Block**: The Zscaler service includes the `X-Zscaler-Block:1` default header (where `1`=Block) to block the content on emails that trigger the outbound email policy rule. The email server uses the header for enforcement.
- **Custom Header Insertion**: The service includes a custom header on emails that trigger the exception rule. Custom headers are designed to take an action that is mapped to the header on the email server. The **Custom Header **format must be `name:value`, where `0`=Allow and `1`=Block (e.g., `X-Zscaler-Quarantine:1`).
To learn more, see [Configuring Microsoft Exchange for Zscaler Outbound Email DLP](/unified/configuring-microsoft-exchange-zscaler-outbound-email-dlp) and [Configuring Gmail for Zscaler Outbound Email DLP](/unified/configuring-gmail-zscaler-outbound-email-dlp).
- (Optional) Define the following **Notification** settings:
- Configure an email notification for the exception rule. If you do not select an auditor and notification template, a notification is not sent for this exception rule.
- **Auditor Type**: Select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- **Auditor**: If the auditor is from a hosted database, select or search for the auditor.
- **Auditor Email Address**: If the auditor is external, enter the auditor’s email address.
- **Notification Template**: Select a [notification template](/unified/configuring-dlp-notification-templates) from the drop-down menu.
- (Optional) For **Description**, enter additional notes or information about the exception rule. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
For example, if an outbound email policy exception rule using predefined Zscaler DLP engines is configured as shown in the following image, the Zscaler service allows all email attachments that:
- Contain medical information
- Are any file type
- Are sent by the HR Director
[See image.](#exception-rule-hipaa-violation)
The Zscaler service doesn't forward information to an Incident Receiver.
[]![Screenshot of an Outbound Email Policy rule using predefined Zscaler DLP engines](/downloads/zia/policies/outbound-email-policy/ZIA-Example-Outbound-Email-Policy-rule_parent_No-email-notification.png)
[]![Screenshot of an Outbound Email Policy exception rule using predefined Zscaler DLP engines](/downloads/zia/policies/outbound-email-policy/ZIA-Example-Outbound-Email-Policy-rule_exception_No-email-notification.png)