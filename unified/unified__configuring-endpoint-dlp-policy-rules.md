# Configuring Endpoint DLP Policy Rules
Source: https://help.zscaler.com/unified/configuring-endpoint-dlp-policy-rules
PDF: https://help.zscaler.com/pdf/com/en/1493196.pdf

You can use Zscaler Endpoint Data Loss Prevention (DLP) to detect data, allow or block activities, require end users to confirm activities, protect files saved to removable storage devices, and notify your organization's auditor when a user's activity on an endpoint triggers an Endpoint DLP rule. If your organization uses a Zscaler Incident Receiver, the service can forward information about end user activities that trigger a DLP policy to your Incident Receiver via secure Internet Content Adaptation Protocol (ICAP). However, Zscaler does not take ICAP responses from your Incident Receiver; instead, the service only monitors or blocks content according to the policy you configure, then forwards information about activities so that your organization can take necessary remediation steps.
The Zscaler DLP engines support files up to 400 MB and can scan the first 100 MB of the extracted text. The maximum size also applies to files extracted from archive files.
To configure an Endpoint DLP policy rule:
- [1. Configure DLP dictionaries and engines, if necessary.](/unified/about-dlp-dictionaries) Use DLP dictionaries and engines as they are or modify them to suit your needs. You can also create custom dictionaries or engines. Skip this step if you don't want to modify or create custom DLP dictionaries and engines.
- [2. Configure DLP notification templates](/unified/configuring-dlp-notification-templates) if you want to send email notifications to your organization's auditor when your users' activities violate Endpoint DLP policy rules.
- [3. (Optional) Configure a Zscaler Incident Receiver](/unified/adding-zscaler-incident-receiver) to forward information about content that triggers an outbound email policy rule to your Incident Receiver via secure Internet Content Adaptation Protocol (ICAP). Zscaler does not take ICAP responses from your Incident Receiver; instead, the service only monitors or blocks content according to the policy you configure, then forwards information about activities so that your organization can take necessary remediation steps.
- [4. (Optional) Configure Cloud-to-Cloud Incident Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to send metadata and evidence about transactions that violate a DLP policy rule directly to your public cloud storage without deploying appliances.
- [4. Define your policy rules.](#Rules)
- [(Optional) 5. Define exception rules.](#ExceptionRules)
[]
- Go to **Policies **>** Data Protection **>** Policy **>** Endpoint Controls **>** Data Loss Prevention**.
- Click **Add DLP Rule**.
- In the **Add DLP Rule** window:
- Enter the following **DLP Rule** attributes:
- **Rule Name**: Enter a unique name for the DLP rule or use the default name.
- **Channel**: Select whether the rule applies to **Printing**, **Removable Storage**, **Network Share**, or **Personal Cloud Storage**.
To learn more, see [About DLP Resources](/unified/about-dlp-resources).
- **Printers**: This field appears only when the **Channel** is **Printing**. Select one or more printers from the drop-down menu, then click **Done**. You can also search for printers.
- **Printer Group**: This field appears only when the **Channel** is **Printing**. Select one or more network printers from the drop-down menu, then click **Done**. You can also search for printer groups.
- **Removable Storage Devices**: This field appears only when the **Channel** is **Removable Storage**. Select one or more removable storage device groups from the drop-down menu, then click **Done**. You can also search for removable storage devices.
- **Removable Storage Device Groups**: This field appears only when the **Channel** is **Removable Storage**. Select one or more removable storage devices from the drop-down menu, then click **Done**. You can also search for removable storage device groups.
- **Network Shares**: This field appears only when the **Channel** is **Network Share**. Select one or more network shares from the drop-down menu, then click **Done**. You can also search for network shares.
- **Network Share Group**: This field appears only when the **Channel** is **Network Share**. Select one or more network shares from the drop-down menu, then click **Done**. You can also search for network share groups.
- **Personal Clouds**: This field appears only when the **Channel** is **Personal Cloud Storage**. Select one or more personal cloud accounts from the drop-down menu, then click **Done**.
iCloud is supported only for macOS.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the Rule Order, the service skips it and moves to the next rule.
- **Severity**: Select the severity of the violation from the drop-down menu (i.e., **High**, **Medium**, **Low**, or **Information**).
- **Rule Order**: All parent rules are evaluated. If multiple rules match, the rule with the most restrictive action and highest rule order is applied. Exception rule evaluation stops at the first match, and an exception replaces a parent rule upon match.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
- **Description**: (Optional) Enter additional notes or information about the rule. The description cannot exceed 10,240 characters.
- Define the following **Criteria**:
- **Content Matching**: Choose **Select DLP Engines** to select up to 4 engines. You can also search for DLP engines. If you select **None**, then the Zscaler service doesn't use DLP engines to scan the content; instead, the service functions as a filter, only flagging content based on the criteria you specify.
- **File Type**: From the drop-down menu, choose the file types for the rule. The list of available file types changes based on whether you're using DLP engines for content inspection. You can create Endpoint DLP policy rules that apply only to content being sent via specific file types. Zscaler DLP engines can scan files of up to 100 MB. For an archived file, the size of individual files when decompressed can also be a maximum of 100 MB. You can also search for file types.
- **Groups**:** **You can specify how the Endpoint DLP rule applies to your [groups](/unified/about-groups). Select **Any** to apply the rules to all groups or select up to 32 groups. You can also search for groups.
-
**Users**: You can specify how the Endpoint DLP rule applies to your [users](/unified/about-users). Select **Any** to apply the rules to all groups or select up to 32 groups. You can also search for users.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
- **Minimum Data Size (KB)**: Enter the minimum size requirement that data must meet before the DLP rule applies. The default minimum data size, 0 KB, means there is no minimum data size requirement.
- **Departments**:** **You can specify how the DLP rule applies to your [departments](/unified/about-departments). Select **Any** to apply the rules to all departments or select up to 32 departments. You can also search for departments.
The DLP policy applies OR logic to the Users, Groups, and Departments fields when inspecting your organization’s traffic. In order for the DLP rule to trigger, the Zscaler service must detect at least one of the rule’s selected users, groups, or departments.
- **Devices**: From the drop-down menu, select one or more devices that the rule applies to. To include all devices, select **Any**. You can also search for devices.
- **Device Groups**: From the drop-down menu, select one or more device groups that the rule applies to. To include all device groups, select **Any**. You can also search for device groups.
- **Device Trust Level**: Select the necessary device trust levels (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**). The trust levels assigned to the devices are based on your [posture configurations](/unified/adding-internet-saas-posture-profiles) in Zscaler Client Connector. You can also search for device trust levels.
- **User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value ignores this criterion in the policy evaluation. You can also search for user risk profiles.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
- Select the **Action** for the rule:
- **Allow**: The service allows and logs the activity.
- **Block**: The service blocks and logs the activity.
For macOS, the **Block** action is supported for the **Removable Storage**, and **Personal Cloud Storage**, and **Network Share** channels. For the **Printing** channel, Zscaler monitors and reports policy violations.
- **Confirm**: The user can either justify the activity to continue, or cancel the activity altogether; in both cases, the Zscaler service logs the activity accordingly. Admins can choose to display a default template or a custom template. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
- **Protect**: This option appears only when the **Channel** is **Removable Storage**. When this setting is enabled, the Zscaler service applies encryption only to affected files, not to the removable storage device itself. After it is encrypted, the file can only be decrypted by members of the same organization who are running Endpoint DLP on their device.
- This functionality is designed to keep files that contain sensitive data within organizational boundaries, while allowing the use of removable storage devices. It is designed specifically for short-term file transfers and should not be used to encrypt files for long-term backup.
- The encryption applied by the Zscaler service does not require additional key management because the encryption key is unique to each organization.
- When a file that contains sensitive data is saved to a removable storage device, the Zscaler service saves only a separate encrypted (`.zenc`) file on the removable storage device. The Zscaler service does not alter the original file or file path.
- Users who receive the encrypted file via a removable storage device must right-click the file and select **Decrypt** to use the Zscaler service to decrypt the file. The Zscaler service saves and automatically opens the decrypted file in the following directory:
- **Windows**: `/ProgramData/Zscaler/ZDP/Decrypted Files/<username>/`
- **macOS**: `/Library/Application Support/Zscaler/ZDP/Decrypted Files/<username>/`
- If a file that contains sensitive data is saved to a removable storage device but does not have an original source path (i.e., the file is cut and pasted onto the removable storage device), then the Zscaler service saves the `.zenc` file to the removable storage device and saves a copy of the decrypted file in the following directory:
- **Windows**: `/ProgramData/Zscaler/ZDP/User Files/<username>/Lost and Found/`
- **macOS**: `/Library/Application Support/Zscaler/ZDP/User Files/<username>/Lost and Found/`
- (Optional) Configure the **DLP Incident Receiver **settings:
- **Zscaler Incident Receiver**: Select the applicable Zscaler Incident Receiver from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
- **Cloud-to-Cloud Forwarding**: Select the applicable **Tenant** and **Cloud-to-Cloud Forwarding Configuration** from the drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the following **Notification** settings:
- (Optional) Configure an email notification for the rule. If you do not select an auditor and notification template, a notification is not sent for this rule.
- **Email Auditor Type**: Select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- **Email Auditor**: If the auditor is from a hosted database, select or search for the auditor.
- **Auditor Email Address**: If the auditor is external, enter the auditor’s email address.
- **Email Notification Template**: Select a [notification template](/unified/configuring-dlp-notification-templates) from the drop-down menu.
- Configure the end user notification (EUN) for the rule. The type of EUN messages that appear on the endpoint depends on the **Action** configured for the rule.
- **End User Notification**: Select **Show** to show an EUN message on endpoints when a user's activity triggers the Endpoint DLP policy rule, or select **Hide** if you don't want an EUN message to appear.
- **Custom Message**: Select **Default** to use the default EUN message configured for the channel, or select a custom EUN message from the drop-down menu. You can also search for custom messages or click the **Add** icon to add a new custom message.
To learn about configuring custom messages for the **Allow**, **Block**, and **Protect** actions, see [Configuring EUNs for Endpoint DLP](/unified/configuring-euns-endpoint-dlp). To learn about configuring custom messages for the **Confirm** action, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
For example, if an endpoint policy rule using predefined Zscaler DLP engines is configured as shown in the following image, the Zscaler service encrypts all PDF files that:
- Contain medical information
- Are any size
- Are being saved by any user to removable storage devices
[See image.](#endpoint-parent-rule)
The Zscaler service sends an email notification regarding the policy violation to the specified auditor but doesn't forward information to an incident receiver. End users receive the default notification configured for the Removable Storage channel.
[]Exception rules allow you to exclude specific users or groups in your organization that need to perform tasks as part of a necessary workflow that might otherwise violate Endpoint rules. You can add up to 32 exception rules to any Endpoint DLP rule, and the exception rules automatically inherit the channel and rule structure of the parent rule. You cannot assign a different channel to exception rules, but you can customize most other rule settings.
To learn more, see [Adding DLP Resources](/unified/adding-dlp-resources).
To define an exception rule:
- Go to **Policies **>** Data Protection **>** Policy **>** Endpoint Controls **>** Data Loss Prevention**.
- Find an existing exception rule in the list and click the **Add Exception Rule** icon. The **Add DLP Exception Rule** window appears.
- In the **Add DLP Exception Rule **window:
- Enter the following **DLP Rule** attributes:
- **Rule Name**: This field is inherited from the parent rule and cannot be changed.
- **Exception Rule Name**: Enter a name for the exception rule.
-
**Channel**: This field is inherited from the parent rule and cannot be changed. Depending on the channel of the parent rule, you can update the following settings:
- **Printers**: This field appears only when the **Channel** is **Printing**. Select one or more printers from the drop-down menu, then click **Done**. You can also search for printers.
- **Printer Group**: This field appears only when the **Channel** is **Printing**. Select one or more network printers from the drop-down menu, then click **Done**. You can also search for printer groups.
- **Removable Storage Devices**: This field appears only when the **Channel** is **Removable Storage**. Select one or more removable storage devices from the drop-down menu, then click **Done**.
- **Removable Storage Device Groups**: This field appears only when the **Channel** is **Removable Storage**. Select one or more removable storage devices from the drop-down menu, then click **Done**. You can also search for removable storage device groups.
- **Network Shares**: This field appears only when the **Channel** is **Network Share**. Select one or more network shares from the drop-down menu, then click **Done**.
- **Network Share Group**: This field appears only when the **Channel** is **Network Share**. Select one or more network shares from the drop-down menu, then click **Done**. You can also search for network share groups.
- **Personal Clouds**: This field appears only when the **Channel** is **Personal Cloud Storage**. Select one or more personal cloud accounts from the drop-down menu, then click **Done**.
iCloud is supported only for macOS.
- **Rule Status**: An enabled exception rule is actively enforced. A disabled exception rule is not actively enforced but does not lose its place in the Rule Order, the service skips it and moves to the next exception rule.
- **Severity**: Select the severity of the violation from the drop-down menu (i.e., **High**, **Medium**, **Low**, or **Information**).
- **Rule Order**: All parent rules are evaluated. If multiple rules match, the rule with the most restrictive action and highest rule order is applied. Exception rule evaluation stops at the first match, and an exception replaces a parent rule upon match.
- **Rule Label**: This field is inherited from the parent rule and cannot be changed.
- **Description**: (Optional) Enter additional notes or information about the exception rule. The description cannot exceed 10,240 characters.
- Define the following **Criteria**:
- **Content Matching**: Choose **Select DLP Engines** to select up to 4 engines. You can also search for DLP engines. If you select **None**, then the Zscaler service doesn't use DLP engines to scan the content; instead, the service functions as a filter, only flagging content based on the criteria you specify.
- **File Type**: From the drop-down menu, choose the file types for the exception rule. The list of available file types changes based on whether you're using DLP engines for content inspection. You can create Endpoint DLP policy rules that apply only to content being sent via specific file types. Zscaler DLP engines can scan files of up to 100 MB. For an archived file, the size of individual files when decompressed can also be a maximum of 100 MB. You can also search for file types.
- **Groups**:** **You can specify how the Endpoint DLP exception rule applies to your [groups](/unified/about-groups). Select **Any** to apply the rules to all groups or select up to 32 groups. You can also search for groups.
-
**Users**: You can specify how the Endpoint DLP rule applies to your [users](/unified/about-users). Select **Any** to apply the rules to all users or select up to 32 users. You can also search for users.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, or **Departments**.
- **Minimum Data Size (KB)**: Enter the minimum size requirement that data must meet before the DLP exception rule applies. The default minimum data size, 0 KB, means there is no minimum data size requirement.
- **Departments**:** **You can specify how the DLP exception rule applies to your [departments](/unified/about-departments). Select **Any** to apply the rules to all departments or select up to 32 departments. You can also search for departments.
The DLP policy applies OR logic to the Users, Groups, and Departments fields when inspecting your organization’s traffic. In order for the DLP exception rule to trigger, the Zscaler service must detect at least one of the exception rule’s selected users, groups, or departments.
- **Devices**: From the drop-down menu, select one or more devices that the exception rule applies to. To include all devices, select **Any**. You can also search for devices.
- **Device Groups**: From the drop-down menu, select one or more device groups that the exception rule applies to. To include all device groups, select **Any**. You can also search for device groups.
- **Device Trust Level**: Select the necessary device trust levels (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**). The trust levels assigned to the devices are based on your [posture configurations](/unified/adding-internet-saas-posture-profiles) in Zscaler Client Connector. You can also search for device trust levels.
- **User Risk Profile**: Select the user risk score levels to which the exception rule applies. Selecting no value ignores this criterion in the policy evaluation. You can also search for user risk profiles.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
-
Select the **Action** for the exception rule:
- **Allow**: The service allows and logs the activity.
-
**Block**: The service blocks and logs the activity.
For macOS, the **Block** action is supported for the **Removable Storage**, and **Personal Cloud Storage**, and **Network Share** channels. For the **Printing** channel, Zscaler monitors and reports policy violations.
- **Confirm**: The user can either justify the activity to continue, or cancel the activity altogether. In both cases, the Zscaler service logs the activity accordingly. Admins can choose to display a default template or a custom template. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
- **Protect**: This option appears only when the **Channel** is **Removable Storage**. When this setting is enabled, the Zscaler service applies encryption only to affected files, not to the removable storage device itself. After it is encrypted, the file can only be decrypted by members of the same organization who are running Endpoint DLP on their device.
-
This functionality is designed to keep files that contain sensitive data within organizational boundaries, while allowing the use of removable storage devices. It is designed specifically for short-term file transfers and should not be used to encrypt files for long-term backup.
- The encryption applied by the Zscaler service does not require additional key management because the encryption key is unique to each organization.
- When a file that contains sensitive data is saved to a removable storage device, the Zscaler service saves only a separate encrypted (`.zenc`) file on the removable storage device. The Zscaler service does not alter the original file or file path.
- Users who receive the encrypted file via a removable storage device must right-click the file and select **Decrypt** to use the Zscaler service to decrypt the file. The Zscaler service saves and automatically opens the decrypted file in the following directory:
- **Windows**: `/ProgramData/Zscaler/ZDP/Decrypted Files/<username>/`
- **macOS**: `/Library/Application Support/Zscaler/ZDP/Decrypted Files/<username>/`
- If a file that contains sensitive data is saved to a removable storage device but does not have an original source path (i.e., the file is cut and pasted onto the removable storage device), then the Zscaler service saves the `.zenc` file to the removable storage device and saves a copy of the decrypted file in the following directory:
- **Windows**: `/ProgramData/Zscaler/ZDP/User Files/<username>/Lost and Found/`
- **macOS**: `/Library/Application Support/Zscaler/ZDP/User Files/<username>/Lost and Found/`
- **None**: The service allows but does not log the activity. You can use this setting if there are users or groups in your organization whose activity should not be logged. When you select the **None** action, the **DLP Incident Receiver** and **Notification** options are not available.
- (Optional) Configure the **DLP Incident Receiver **settings:
- **Zscaler Incident Receiver**: Select the applicable Zscaler Incident Receiver from the drop-down menu. You must configure your [Zscaler Incident Receivers](/unified/configuring-zscaler-incident-receiver-premises-vms) to complete this step.
- **Cloud-to-Cloud Forwarding**: Select the applicable **Tenant** and **Cloud-to-Cloud Forwarding Configuration** from the drop-down menus. You must configure [Cloud-to-Cloud Forwarding](/unified/configure-dlp-cloud-cloud-incident-forwarding) to complete this step.
- Define the following **Notification** settings:
- (Optional) Configure an email notification for the exception rule. If you do not select an auditor and notification template, a notification is not sent for this exception rule.
- **Email Auditor Type**: Select whether the auditor is from a **Hosted** database or **External **to your organization.
- Select the **Auditor**:
- **Email Auditor**: If the auditor is from a hosted database, select or search for the auditor.
- **Auditor Email Address**: If the auditor is external, enter the auditor’s email address.
- **Email Notification Template**: Select a [notification template](/unified/configuring-dlp-notification-templates) from the drop-down menu.
- Configure the end user notification (EUN) for the exception rule. The type of EUN messages that appear on the endpoint depends on the **Action** configured for the exception rule.
- **End User Notification**: Select **Show** to show an EUN message on endpoints when a user's activity triggers the exception rule, or select **Hide** if you don't want an EUN message to appear.
-
**Custom Message**: Select **Default** to use the default EUN message configured for the channel, or select a custom EUN message from the drop-down menu. You can also search for custom messages or click the **Add** icon to add a new custom message.
To learn about configuring custom messages for the **Allow**, **Block**, and **Protect** actions, see [Configuring EUNs for Endpoint DLP](/unified/configuring-euns-endpoint-dlp). To learn about configuring custom messages for the **Confirm** action, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
For example, for an exception rule using predefined Zscaler DLP engines configured as shown in the following image, the Zscaler service allows all PDF files that:
- Contain medical information
- Are any size
- Are being saved to any removable storage device by members of the Service Admin Department
[See image.](#endpoint-exception-rule)
The Zscaler service sends an email notification regarding the exception to the specified auditor but doesn't forward information to an incident receiver. End users receive the default notification configured for the Removable Storage channel.
[]![Screenshot of an endpoint rule using predefined Zscaler DLP engines](/downloads/zia/policies/configuring-endpoint-dlp-policy-rules/ZIA-Example-Endpoint-DLP-Policy-parent-rule_MVP2.0.png)
[]![Screenshot of an endpoint exception rule using predefined Zscaler DLP engines](/downloads/zia/policies/configuring-endpoint-dlp-policy-rules/ZIA-Example-Endpoint-DLP-Policy-exception-rule_MVP2.0.png)