# Configuring the Data at Rest Scanning DLP Policy without Content Inspection
Source: https://help.zscaler.com/unified/configuring-data-rest-scanning-dlp-policy-without-content-inspection
PDF: https://help.zscaler.com/pdf/com/en/1529721.pdf

To enable this feature for your organization, contact Zscaler Support.
The SaaS Security Data at Rest Scanning [Data Loss Prevention (DLP)](/unified/about-data-rest-scanning-dlp) policy allows you to create rules to discover and protect sensitive data at rest in sanctioned SaaS applications. When you configure a SaaS Security Data at Rest Scanning DLP rule without content inspection, you do not use Zscaler DLP engines to detect data. Instead, the Zscaler service functions as a filter, only forwarding content based on specific criteria. To learn about configuring SaaS Security Data at Rest Scanning DLP rules with content inspection, see [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/unified/configuring-data-rest-scanning-dlp-policy-content-inspection).
To inspect content based on a configured policy rule's specifications, you must add it to a scan schedule. The Zscaler service does not inspect content until you configure a scan. To learn more, see [About SaaS Security Scan Configuration](/unified/about-saas-security-api-scan-configuration).
To configure the Data at Rest Scanning DLP policy:
- Go to **Policies **>** Data Protection **>** Policy **>** Out-of-Band CASB**.
- On the **Data Loss Prevention** tab, choose one of the following SaaS application types from the drop-down menu:
- [Collaboration](#collaboration)
- [CRM](#crm)
- [Email](#email)
- [File Sharing](#filesharing)
- [Gen AI](#GenAI)
- [ITSM](#ITSM)
- [Public Cloud Storage](#publiccloudstorage)
- [Source Code Repository](#sourcecoderepository)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]To add a DLP rule for collaboration applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
-
**SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule. You can also search for application tenants.
For Microsoft Teams, Slack, and Webex Teams, keywords within a file are detected irrespective of the character length. However, there is a restriction for terms searched in a message or chat to 8 bytes, below which the term or string is not detected by the DLP action.
- **Components**: The components that the Zscaler service inspects for sensitive data. Choose **Any** to inspect all components, or choose to only inspect **Attachments** or **Messages**.
- **Senders**: The users who sent the attachments or messages containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: The groups of the users who sent the attachments or messages containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Departments**: The departments of the users who sent the attachments or messages containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Content Location**: The location for the content that the Zscaler service inspects for sensitive data. Choose **Any** to inspect all content locations or choose a content location.
- **Domains**: This field only appears when you select **Shared Channels** for **Content Location**. Enter the domain for the external organization sharing the channel and then click **Add Items**. If you want to add multiple domains, separate the domains with commas.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Choose the action the rule takes upon detecting content that matches the criteria. The number of actions available depends on the selected SaaS Application Tenant.
- **Notify Users Only**: The rule notifies the users about the incident.
- For Slack, the custom Slack bot notifies the users.
- For Microsoft Teams, the Microsoft Teams bot notifies the users.
- For Webex Teams, the custom Webex Teams bot notifies the users.
- **Quarantine**: (Slack, Webex Teams) Select this option to quarantine sensitive messages and files. When you select this option, the **Tombstone Template** drop-down menu appears.
- **Remove**: For Zoom, the Zscaler service deletes the sensitive messages and files (attachments).
- **Report Incident Only**: The rule reports the incident only.
- **Tombstone Template**: (Slack, Webex Teams) If you select **Quarantine** as the **Action** for sensitive content, you must select a tombstone template from the drop-down menu. The quarantine action creates a tombstone message that end users see in Slack or Webex Teams. After a message or file has been quarantined, admins can use the SaaS Security Assets Report (Analytics > Internet & SaaS > Analytics > SaaS Security > Assets) to review and remove the quarantined content. To learn more, see [About Quarantine Tombstone File Templates](/unified/about-quarantine-tombstone-file-templates) and [Understanding the Assets Report: Assets with Incidents](/unified/understanding-assets-report-assets-with-incidents).
-
**Severity**: Select a severity level (i.e., **High**,** Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]To add a DLP rule for CRM applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
- **SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule. You can also search for application tenants.
- **Components**: The components that the Zscaler service inspects for sensitive data. Choose **Any** to inspect all components, or choose to only inspect **Attachments in Objects** or **Chatter Messages**.
- **Owners**: The users who own the objects containing sensitive data or sent the Chatter messages containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: The groups of the users who own the objects containing sensitive data or sent the Chatter messages containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Departments**: The departments of the users who own the objects containing sensitive data or sent the Chatter messages containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Collaboration Scope**: The collaboration scopes and permissions for SaaS tenant files that contain sensitive data. Select **Any** to apply the rule to files with all collaboration levels, or select any number of the following collaboration scopes and specify the permissions (**View**, **Edit**) for each scope:
- **External Collaborators**: Files that are shared with specific collaborators outside of your organization.
- **External Link**: Files with shareable links that allow anyone outside your organization to find the files and have access.
- **Internal Collaborators**: Files that are shared with specific collaborators or are discoverable within your organization.
- **Internal Link**: Files with shareable links that allow anyone within your organization to find the files and have access.
- **Private**: Files that are only accessible to the owner.
- **Object Type**: Choose **Any** to inspect all object types or choose an object type.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Select the action the rule takes upon detecting content that matches the criteria.
- **Change to Read Only for All Collaborators**: The rule reports the incident and changes the file’s collaboration scope for all collaborators to read only.
- **Change to Read Only for External Collaborators**: The rule reports the incident and changes the file’s collaboration scope for external collaborators to read only.
- **Change to Read Only for Internal Collaborators**: The rule reports the incident and changes the file’s collaboration scope for internal collaborators to read only.
-
**Quarantine**: The Zscaler service quarantines suspicious files.
When you choose this action, the **Quarantine Location** field appears. Enter a location to move all the quarantined files and take necessary actions by either deleting or restoring the data.
- **Remove**: The Zscaler service deletes the file.
- **Remove External Collaborators and Shareable Link**: The rule reports the incident and removes all of the file’s external collaborators and any shareable links.
- **Remove Internal Collaborators and Shareable Link**: The rule reports the incident and removes all internal collaborators and any shareable links.
- **Remove Public Shareable Link**: The rule reports the incident and removes the file’s public shareable link. Existing collaborators are unaffected.
- **Remove Sharing**: The rule reports the incident and removes all of the file’s collaborators and any shareable links.
- **Report Incident Only**: The rule reports the incident only and makes no changes to the file’s collaboration scope.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- **Tombstone Template**: Select a tombstone template from the drop-down menu. The quarantine action creates a tombstone file template in the quarantine location and adds the description from the tombstone template created on the Quarantine page (Policies > Common Configuration > Out-of-Band CASB > Tombstone Template). To learn more, see [About Quarantine Tombstone File Templates](/unified/about-quarantine-tombstone-file-templates).
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]To add a DLP rule for email applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
- Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
-
**SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule. You can also search for application tenants.
For each DLP rule you create, you can only add tenants from the same SaaS application provider. For example, you have a tenant for Gmail and a tenant for Exchange. You can only create a rule for the Gmail tenant and a rule for the Exchange tenant. You cannot create one rule for both the Gmail tenant and Exchange tenant.
- **Components**: This field cannot be changed. The Zscaler service inspects the body, attachments, and subject for emails containing sensitive data.
- **Senders**: The users who sent the emails containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Recipients**: This field cannot be changed. This rule only applies when at least one email recipient is from outside your organization, and that recipient is not an external trusted user or is not using an external trusted domain. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- **Groups**: The groups of the users who sent the emails containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Departments**: The departments of the users sent emails containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
-
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Select the action the rule takes upon detecting content that matches the criteria.
-
**Apply Email Tag**: The rule reports the incident and applies an email tag to it.
When you choose this action, the **Label Name** field appears. From this drop-down menu, you can choose an email label you want the rule to apply to the emails. The Zscaler service automatically creates an email category or an email label in the users’ email accounts if it hasn’t been already created.
[See image.](#email-label-cab-dlp)
- **Report Incident Only**: The rule reports the incident only.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]![The Apply Email Tag action enables you to select the Email Label to apply to the rule.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-dlp-policy/ZIA-SaaS-Security-API-Email-Tagging-ContentInspection.png)
[]To add a DLP rule for file sharing applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
-
**SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule. You can also search for application tenants.
For each DLP rule you create, you can only add tenants from the same SaaS application provider. For example, you have a tenant for SharePoint and a tenant for OneDrive. You can only create a rule for the SharePoint tenant and a rule for the OneDrive tenant. You cannot create one rule for both the SharePoint tenant and OneDrive tenant.
- **Sites**: Select **Any **to apply the rule to all sites, or select up to 1,024 sites from the list.
- **Site Groups**: You can choose to either include or exclude up to 256 site groups from the policy.
- **Sites **and **Site Groups** are mutually exclusive fields. You can choose only one of these criteria to configure your policy.
- The **Site Groups** field is currently available only for the SharePoint tenant.
- **Groups**: The groups of the users who own the files containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Collaboration Scope**: The collaboration scopes and permissions for SaaS tenant files that contain sensitive data. Select **Any** to apply the rule to files with all collaboration levels, or select any number of the following collaboration scopes and specify the permissions (**View**, **Edit**) for each scope:
- **External Collaborators**: Files that are shared with specific collaborators outside of your organization.
- **External Link**: Files with shareable links that allow anyone outside your organization to find the files and have access.
- **Internal Collaborators**: Files that are shared with specific collaborators or are discoverable within your organization.
- **Internal Link**: Files with shareable links that allow anyone within your organization to find the files and have access.
- **Private**: Files that are only accessible to the owner.
- **No. of Internal Collaborators**: Select the number of internal collaborators for files that are shared with specific collaborators or are discoverable within your organization. Select **None** for no collaborators or select a range of collaborators to apply the scope to.
-
**No. of External Collaborators**: Select the number of external collaborators for files that are shared with specific collaborators outside of your organization. Select **None** for no collaborators or select a range of collaborators to apply the scope to.
- Currently, if a user is in two different groups, the system counts them as two separate users.
- This feature is available for SharePoint, OneDrive, and Google Drive.
- **Owners**: The users who own the files containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Departments**: The departments of the users who own the files containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **File Types**: Select files types to which you want to apply the rule. You can select any number of file types and also search for file types.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Choose the action the rule takes upon detecting content that matches the criteria. The number of actions available depends on the selected SaaS Application Tenant.
- **Admin Quarantine**: This action is only applicable for Google Drive, OneDrive, and SharePoint tenants. The rule quarantines the sensitive files to a specific location that the admin chooses while onboarding the tenant.
-
**Apply MIP Label**: This action is only applicable for OneDrive and SharePoint tenants. The rule reports the incident and applies the chosen classification label to the file.
When you choose this action, the** Apply Classification Label **field appears. From this drop-down menu, you can choose the classification label you want the rule to apply to files. The Zscaler service collects the active labels from the list of all authorized MIP labels.
[See image.](#mip-label-saas-security-api-dlp)
To see this action, you must choose from the list of OneDrive and SharePoint tenants. This action is only applicable for Microsoft Excel, Microsoft Word, and PDF file types.
-
**Apply Box Classification Label**: This action is only applicable for Box tenants with [Box Shield](https://www.box.com/shield) enabled. The rule reports the incident and applies the chosen Box classification label to the file.
When you choose this action, the** Apply Classification Label **field appears. From this drop-down menu, you can choose the Box classification label you want the rule to apply to files. The Zscaler service collects these labels when you [onboard the Box tenant](/unified/adding-saas-application-tenants). Deleted labels appear with a strikethrough line in the drop-down menu and cannot be applied to a rule.
[See image.](#Box-Classification-Label-section)
To see this action, you must choose a single Box tenant with defined classification labels from the **SaaS Application Tenant** drop-down menu. This action is unavailable if you choose a tenant without defined labels or select multiple Box tenants.
-
**Apply Google Drive Label**: This action is only applicable for Google Drive tenants. The rule reports the incident and applies the chosen Google Drive label to the file.
When you choose this action, the** Apply Classification Label **field appears. From this drop-down menu, you can choose the Google Drive classification label you want the rule to apply to files. The Zscaler service collects these labels when you [onboard the Google Drive tenant](/unified/adding-saas-application-tenants). Deleted labels appear with a strikethrough line in the drop-down menu and cannot be applied to a rule.
[See image.](#Google-Drive-Label-section)
- To see this action, you must choose a single Google Drive tenant with defined labels from the SaaS Application Tenant drop-down menu. This action is unavailable if you choose a tenant without defined labels or select multiple Google Drive tenants.
- Before you can use labels in a Google Drive tenant that you have already onboarded, you must reauthorize the tenant so that Zscaler can identify all available labels. To learn more, see [About SaaS Application Tenants](/unified/about-saas-application-tenants).
-
**Apply Atlassian Classification Label:** This action is only applicable to Confluence tenants. The rule reports the incident and applies the chosen Atlassian label to the file.
When you choose this action, the **Apply Classification Label** field appears. From this drop-down menu, you can choose the Atlassian Classification label you want the rule to apply to files. Deleted labels appear with a strikethrough line in the drop-down menu and cannot be applied to a rule.
[See image.](#apply-attlassian-classification-label)
- To see this action, you must choose a tenant with defined labels from the **SaaS Application Tenant** drop-down menu. This action is not available if you choose a tenant without defined labels or if you select multiple tenants.
- Before you can use Atlassian Classification labels that you have already onboarded, you must reauthorize the tenant so that Zscaler can identify all available labels. To learn more, see [About SaaS Application Tenants](/unified/about-saas-application-tenants).
- **Change to Read Only for All Collaborators**: The rule reports the incident and changes the file’s collaboration scope for all collaborators to read only.
- **Change to Read Only for External Collaborators**: The rule reports the incident and changes the file’s collaboration scope for external collaborators to read only.
- **Change to Read Only for Internal Collaborators**: The rule reports the incident and changes the file’s collaboration scope for internal collaborators to read only.
- **Move to Restricted Folder**: For Confluence, the rule reports the incident and moves all the scanned files (pages, blogs, and attachments) to a restricted page under the user's personal space.
- **Quarantine to User Root Folder**: The rule reports the incident and quarantines sensitive content to a user's root folder. When you select this option, the **Tombstone Template** drop-down menu appears.
- **Remove**: For Confluence, the rule reports the incident and removes all the attachments from the pages and blogs of the space.
- **Remove All Collaborators**: The rule reports the incident and removes all of the file’s external and internal collaborators.
- **Remove External Collaborators**: The rule reports the incident and removes all of the file’s external collaborators.
- **Remove External Collaborators and Shareable Link**: The rule reports the incident and removes all of the file’s external collaborators and any shareable links.
- **Remove Internal Collaborators and Shareable Link**: The rule reports the incident and removes all internal collaborators and any shareable links.
- **Remove Internal Shareable Link**: The rule reports the incident and removes the file’s internal shareable link. Existing collaborators are unaffected.
- **Remove Public Shareable Link**: The rule reports the incident and removes the file’s public shareable link. Existing collaborators are unaffected.
- **Remove Sharing**: The rule reports the incident and removes all of the file’s collaborators and any shareable links.
- **Report Incident Only**: The rule reports the incident only and makes no changes to the file’s collaboration scope.
-
**Watermark the Document**: The rule uses the specified watermark profile to add a watermark, as well as optional headers and footers to supported file types that contain sensitive information.
On Confluence tenants, the Zscaler service applies watermarks only on files that are attached to Confluence pages, not on the Confluence pages themselves.
- [File types supported for watermarking](#filesharing-watermark)
- **Versioning**: If you select **Watermark the Document** as the **Action** for sensitive content, you can select **Retain Existing Versioning** to treat the watermarked file as a new version of the existing file on the SaaS provider, or you can select **Delete Existing Versioning** to treat the watermarked file as a completely new file on the SaaS provider.
- **Watermark Profile**: If you select **Watermark the Document** as the **Action** for sensitive content, you can select a watermark profile from the drop-down menu. You can also search for watermark profiles.
- **Update to Not Discoverable Externally**: The rule reports the incident and changes the file’s collaboration scope to prevent it from being discoverable through public search engines.
- **Update to Not Discoverable for All**: The rule reports the incident and changes the file’s collaboration scope to prevent it from being discoverable through public search engines or within your organization.
- **Update to Not Discoverable Internally**: The rule reports the incident and changes the file’s collaboration scope to prevent it from being discoverable within your organization.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- **Email Recipient Domain Profiles**: If you select **Remove External Collaborators** for the action, you can then select the desired domain profiles and whether you want to **Include** or **Exclude** them from the action.
- **Tombstone Template**: Select a tombstone template from the drop-down menu. The quarantine action creates a tombstone file template in the original location and adds the description from the tombstone template created on the Quarantine page (Policies > Common Configuration > Out-of-Band CASB > Tombstone Template). To learn more, see [About Quarantine Tombstone File Templates](/unified/about-quarantine-tombstone-file-templates).
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]
- PDF (.pdf)
- Rich Text (.rtf)
- Microsoft Excel (.xls, .xlt, .xlsm, .xltm, .xlsx, .xltx)
- Microsoft Word (.doc, .dot, .docm, .dotm, .docx, .dotx)
- Microsoft PowerPoint (.pps, .ppt, .pot, .pptm, .ppsm, .potm, .pptx, .ppsx, .potm, .potx)
- Open Document (.odt)
- Archive (.tar, .zip)
The Zscaler service adds watermarks only to supported file types within archive files; all other file types remain unchanged.
- Visio (.vdx, .vsdm, .vssm, .vss, .vstm, .vtx, .vsdx, .vstx, .vssx, .vsx, .vsd)
- Images (.bmp, .gif, .jp2, .jpg, .jpeg, .tiff, .tif, .webp, .png)
[]![Screenshot of Box Classification Label section in SaaS Tenant Application page](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-dlp-policy/ZIA-saas-application-tenant-box-tenant-classification-labels.png?1682541640)
[]![Screenshot of Google Drive Label section in SaaS Tenant Application page](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-dlp-policy/ZIA-saas-application-tenant-google-drive-tenant-classification-labels-section.png?1682539901)
[]![Apply Atlassian Label to SaaS Security DLP Rule](/downloads/zia/configuring-saas-security-api-dlp-policy/apply-atlassian-label.png)
[]![The Apply MIP Label action enables you to select the MIP Label to apply the rule to the tenant.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-dlp-policy/ZIA-Apply-MIP-Labels-ContentMatching.png)
[]The scanning exceptions for generative AI:
- Includes attachments uploaded via Custom GPT and predefined GPT but does not include DLP and malware scans, as the download URL is unavailable and there is no policy action
- Includes Eicar files, but there is no policy action as the download URL is unavailable
- Excludes the scanning of text fields such as Description, Instructions, Name, or Conversation Starters
- Excludes the scanning of malware content present in the prompt of a conversation
To add a DLP rule for generative AI applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
- **SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule.
- **Owners**: The users who own the objects containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Departments**: The departments of the users own the objects containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **Components**: The components that the Zscaler service inspects for sensitive data. Choose **Any** to inspect all components, or choose to only inspect **Attachments** or **Messages**.
- **Groups**: The groups of the users own the objects containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: This field cannot be changed. The Zscaler service reports the incident only.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]To add a DLP rule for ITSM applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
- **SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule.
- **Owners**: The users who own the objects containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Departments**: The departments of the users own the objects containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Components**: The components that the Zscaler service inspects for sensitive data. Choose **Any** to inspect all components, or choose to only inspect **Attachments** or **Objects**.
- **Groups**: The groups of the users own the objects containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Collaboration Scope**: The collaboration scopes and permissions for SaaS tenant files that contain sensitive data. Select **Any** to apply the rule to files with all collaboration levels, or select any number of the following collaboration scopes and specify the permissions (**View**, **Edit**) for each scope:
- **External Collaborators**: Files that are shared with specific collaborators outside of your organization.
- **External Link**: Files with shareable links that allow anyone outside your organization to find the files and have access.
- **Internal Collaborators**: Files that are shared with specific collaborators or are discoverable within your organization.
- **Internal Link**: Files with shareable links that allow anyone within your organization to find the files and have access.
- **Private**: Files that are only accessible to the owner.
-
**Object Type**: Choose **Any** to inspect all object types or choose an object type.
If the object type you want to select is not listed, you can edit the ServiceNow tenant and add more object types. To learn more, see [Adding Object Types for ServiceNow Tenants](/unified/adding-object-types-servicenow-tenants).
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Select the action the rule takes upon detecting content that matches the criteria:
-
**Quarantine**:** **The Zscaler service quarantines suspicious files.
When you choose this action, the **Quarantine Location** field appears. Enter a location to move all the quarantined files and take the necessary actions by either deleting or restoring the data.
- **Remove**:** **The Zscaler service removes suspicious files.
- **Report Incident Only**: The Zscaler service reports the incident only.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- **Tombstone Template**: Select a tombstone template from the drop-down menu. The quarantine action creates a tombstone file template in the quarantine location and adds the description from the tombstone template created on the Quarantine page (Policies > Common Configuration > Out-of-Band CASB > Tombstone Template). To learn more, see [About Quarantine Tombstone File Templates](/unified/about-quarantine-tombstone-file-templates).
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
[]To add a DLP rule for public cloud storage applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
- **SaaS Application Tenant**: Choose the [SaaS application tenant](/unified/about-saas-application-tenants) to which you want to apply the rule.
- **Buckets**: This is only applicable for Amazon S3 and Google Cloud Platform tenants. Select the buckets for the Zscaler service to inspect for sensitive data. You can select up to 1K buckets. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#internet-saas#Rules).
- **Collaboration Scope**: The collaboration scopes and permissions for SaaS tenant files that contain sensitive data. Select **Any** to apply the rule to files with all collaboration levels, or select any number of the following collaboration scopes and specify the permissions (**View**, **Edit**) for each scope:
- **External Collaborators**: Files that are shared with specific collaborators outside of your organization.
- **External Link**: Files with shareable links that allow anyone outside your organization to find the files and have access.
- **Internal Collaborators**: Files that are shared with specific collaborators or are discoverable within your organization.
- **Internal Link**: Files with shareable links that allow anyone within your organization to find the files and have access.
- **Private**: Files that are only accessible to the owner.
-
**Bucket Owner**: This is only applicable for Amazon S3 and Google Cloud Platform tenants. Choose a user to inspect their buckets for sensitive data. When you choose a user, their buckets are available in the Buckets field.
Before you can select buckets or choose a bucket owner, you must have saved this rule and [created a scan schedule](/unified/configuring-saas-security-api-scan-schedules). To learn more, see [Understanding the Data at Rest Scanning Policy](/unified/understanding-data-rest-scanning-policy).
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **Blob Containers**: This is only applicable for Microsoft Azure tenants. Select the blob containers for the Zscaler service to inspect for sensitive data. You can select up to 1K blob containers. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#internet-saas#Rules).
-
**Blob Container Owner**: This is only applicable for Microsoft Azure tenants. Choose a user to inspect their blob containers for sensitive data. When you choose a user, their blob containers are available in the Blob Containers field.
Before you can select blob containers or choose a blob container owner, you must have saved this rule and [created a scan schedule](/unified/configuring-saas-security-api-scan-schedules). To learn more, see [Understanding the Data at Rest Scanning Policy](/unified/understanding-data-rest-scanning-policy).
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: Choose the action the rule takes upon detecting content that matches the criteria. The number of actions available depends on the selected SaaS Application Tenant.
- **Change to Read Only for All Collaborators**: The rule reports the incident and changes the file’s collaboration scope for all collaborators to read only.
- **Change to Read Only for External Collaborators**: The rule reports the incident and changes the file’s collaboration scope for external collaborators to read only.
- **Change to Read Only for Internal Collaborators**: The rule reports the incident and changes the file’s collaboration scope for internal collaborators to read only.
- **Remove All Collaborators**: The rule reports the incident and removes all of the file’s external and internal collaborators.
- **Remove External Collaborators and Shareable Link**: The rule reports the incident and removes all of the file’s external collaborators and any shareable links.
- **Remove Internal Collaborators and Shareable Link**: The rule reports the incident and removes all internal collaborators and any shareable links.
- **Remove Public Shareable Link**: The rule reports the incident and removes the bucket’s public shareable link. Existing collaborators are unaffected.
- **Remove Sharing**: The rule reports the incident and removes all of the file’s collaborators and any shareable links.
- **Report Incident Only**: The rule reports the incident only and makes no changes to the bucket’s collaboration scope.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
[]To add a DLP rule for source code repository applications:
-
Click **Add DLP Rule**.
The **Add DLP Rule** window appears.
- Enter the rule attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Ranking](/unified/about-admin-rank), then the assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0–7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the DLP rule.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order; the service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels.](/unified/about-rule-labels)
-
Define the criteria:
- **Content Matching**: Select **None** to use the Zscaler service as a filter, only flagging content based on the criteria you specify. Selecting **None** means that Zscaler DLP Engines are not used to inspect content.
- **SaaS Application Tenant**: Select the [SaaS application tenants](/unified/about-saas-application-tenants) to which you want to apply the rule. You can also search for application tenants.
- **Buckets**: This is only applicable for GitLab tenants. Select the buckets for the Zscaler service to inspect for sensitive data. You can select up to 32 buckets.
-
**Bucket Owner**: This is only applicable for GitLab tenants. Choose a user to inspect their buckets for sensitive data. When you choose a user, their buckets are available in the **Buckets **field.
Before you can select buckets or choose a bucket owner, you must have saved this rule and [created a scan schedule](/unified/configuring-saas-security-api-scan-schedules). To learn more, see [Understanding the Data at Rest Scanning Policy](/unified/understanding-data-rest-scanning-policy).
- **Editors**: The users who own the files containing sensitive data. Select **Any** to apply the rule to all [users](/unified/about-internet-saas-users), or select up to 4 users under General Users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: The groups of the users who own the files containing sensitive data. Select **Any** to apply the rule to all [groups](/unified/about-internet-saas-groups), or select up to 8 groups. You can search for groups or click the **Add** icon to add a new group.
- **Departments**: The departments of the users who own the files containing sensitive data. Select **Any** to apply the rule to all [departments](/unified/about-departments-internet-saas), or select up to 8 departments. You can search for departments or click the **Add** icon to add a new department.
- **File Types**: From the drop-down menu, choose the file types for the rule. The rule you create applies only to content within the file types you specify.
- **File Type**: Select files types to which you want to apply the rule. You can select any number of file types and also search for file types.
- **Collaboration Scope**: The collaboration scopes and permissions for SaaS tenant files that contain sensitive data. Select **Any** to apply the rule to files with all collaboration levels, or select any number of the following collaboration scopes and specify the permissions (**View**, **Edit**) for each scope:
- **External Collaborators**: Files that are shared with specific collaborators outside of your organization.
- **External Link**: Files with shareable links that allow anyone outside your organization to find the files and have access.
- **Internal Collaborators**: Files that are shared with specific collaborators or are discoverable within your organization.
- **Internal Link**: Files with shareable links that allow anyone within your organization to find the files and have access.
- **Private**: Files that are only accessible to the owner.
- **Trusted Users**: Specify the trusted users (i.e., users with email addresses outside your organization) for the rule. If you specify trusted users for the rule, you cannot also specify trusted domains. The Zscaler service treats trusted users the same as internal users. So if your company uses contractors with email addresses that are different from your company domain, you can add the contractors as trusted users so that the Zscaler service treats them as internal users in your company domain. Trusted users are configured as recipient profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- **Trusted Domains**: Specify the trusted domains (i.e., domains outside your organization) for the rule. If you specify trusted domains for the rule, you cannot also specify trusted users. The Zscaler service treats added domains the same as internal domains. For example, suppose your organization's domain is safemarch.com and your company acquires another company that uses the domain example.com. In that case, you can add example.com as a trusted domain, and the Zscaler service treats email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. Trusted domains are configured as domain profiles in the email profiles for your organization. To learn more, see [About Email Profiles](/unified/about-email-profiles).
- If a file matches all rule criteria *and* the trusted users or trusted domains set for the rule, then the Zscaler service does not consider a transaction to be a rule violation and does not take action on the file.
- If you previously used a domain profile or recipient profile when onboarding a SaaS application tenant, the domain profile or recipient profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because the domain profile or recipient profile is already considered internal. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
- (Optional) Define the DLP Incident Receiver:
- If you don't have a third-party DLP solution or don't want to forward content, leave the **Zscaler Incident Receiver **field as **None**.
-
If you want to forward the transactions captured by this policy rule to an on-premises DLP incident receiver, select the applicable **Zscaler Incident Receiver** from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
Ensure that in your third-party DLP solution, you've configured a rule that detects the same data type as the rule you configure here. For example, if you configure a Zscaler DLP rule blocking credit card data, you must also configure a rule in your third-party solution blocking credit card data.
Otherwise, the information Zscaler sends to your solution regarding a particular rule violation does not appear in your on-premises solution's dashboard. However, the rules do not need to correspond exactly. You don't need to ensure that other criteria for the rules, beyond the data type, correspond. For example, if a Zscaler DLP rule blocks credit card numbers going to a specific URL category, the rule in your on-premises DLP solution must also block credit card numbers, but needn't match the URL category criteria.
- If you want to forward the incidents that this policy rule captured to your public cloud, such as Amazon S3, Microsoft Azure, or Google Cloud Platform, select the **Cloud-to-Cloud Forwarding** option. When you select this option, the tenant option appears. Choose a **Tenant **and a **Cloud-to-Cloud Forwarding Configuration** from their respective drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the action:
- **Action**: This field cannot be changed. The Zscaler service reports the incident only.
-
**Severity**: Select a severity level (i.e., **High**, **Medium**, **Low**, or **Information**) for the incidents that match this rule.
The Information level allows you to track low-risk incidents that must be observed.
- (Optional) Configure the email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- For **Auditor Type**, select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- If the auditor is from a hosted database, select or search for the auditor.
- If the auditor is external, enter the auditor’s email address.
- Select a **Notification Template**, if you [configured one](/unified/configuring-dlp-notification-templates). You can also search for a notification template or click the **Add** icon to add a new notification template.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.