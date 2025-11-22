# Configuring EUNs for Endpoint DLP
Source: https://help.zscaler.com/unified/configuring-euns-endpoint-dlp
PDF: https://help.zscaler.com/pdf/com/en/1508011.pdf

You can customize the messages for Zscaler Client Connector-based notifications that are displayed for end users when a Zscaler [Endpoint Data Loss Prevention (DLP) policy](/unified/about-endpoint-data-loss-prevention) configured in Internet & SaaS is triggered by the end user's activity. For example, you can block your organization users from transferring sensitive corporate data from their endpoints to their personal cloud storage accounts or removable storage and display a notification informing the end user of the policy violation. In another scenario, you can allow your users to print documents containing sensitive data using a network printer but with a notification cautioning them about the risks associated.
These end user notifications (EUNs) are triggered by Internet & SaaS based on your policy configuration and are issued by the Zscaler Client Connector service that is installed on the users’ endpoints. You can customize various elements of the notification, including the notification message for different policy actions, company name, logo, information displayed on the notification, duration of the notification, and more. You can modify the default notification message that’s preconfigured in the Admin Portal and additionally create custom messages for each supported Endpoint DLP channel, including Printing, Removable Storage, Network Share, and Personal Cloud Storage. By configuring custom messages, you can allow the selection of different notification messages for individual Endpoint DLP rules of each channel type. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
To display the EUN for a specific Endpoint DLP rule, you must enable the EUN within the rule configuration page and select the notification message (corresponding to the specified channel) that must be used for that particular rule. To learn about Endpoint DLP policy configuration, see [Configuring Endpoint DLP Policy Rules](/unified/configuring-endpoint-dlp-policy-rules).
This article describes how you can customize the EUN messages used in the Endpoint DLP policy. To learn more about how to enable and configure EUNs, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/unified/step-step-configuration-guide-zscaler-client-connector-based-euns).
The following sections provide information on the steps required to create custom notification messages for Zscaler Client Connector-based EUNs for the various channels supported in Endpoint DLP policy:
- [EUNs for the Removable Storage Channel in Endpoint DLP Policy](#removable-storage)
- [EUNs for the Printing Channel in Endpoint DLP Policy](#printing)
- [EUNs for the Network Share Channel in Endpoint DLP Policy](#network-share)
- [EUNs for the Personal Cloud Storage Channel in Endpoint DLP Policy](#personal-cloud-storage)
-
[]Go to **Policies** >** Common Configuration **>** Resources **> **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Removable Storage** which would be the channel used in the Endpoint DLP policy triggering this notification message.
-
Under **Message**, you can customize the notification message in any of the languages available from the language drop-down menu. You can customize the message that appears when an Endpoint DLP rule is matched and the configured action is applied:
- **Allow**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule, but the service allows the traffic and logs the activity.
- **Block**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule and the service blocks the activity.
- **Protect**: Enter text to customize the notification message that appears when an end user's activity triggers a rule and the service encrypts an affected file. When a file is encrypted, users who receive the file must use the Zscaler service to decrypt the file.
For Endpoint DLP rules that are configured with the Confirm action, the Zscaler service provides an EUN message that is customized separately. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
[See image.](#removable-storage-messages)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **File Name**: Select to include the name of the file that triggered the rule in the notification.
- **Destination**: Select to include the removable storage to which the file was copied and the rule was triggered in the notification.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **DLP Engines**: Select to include the name of the DLP engines that triggered the rule in the notification.
[See image.](#removable-storage-additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow, Block, and Protect notification previews.
[See image.](#removable-storage-preview)
- Click **Save** and activate the change.
In addition to the notification message, ensure that the notification customizations shared by all Zscaler Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/unified/configuring-settings-zscaler-client-connector-based-euns) on the Zscaler Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default messages for all actions. This option appears only when you modify the default messages.
-
[]Go to **Policies** >** Common Configuration **>** Resources **> **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Printing** which would be the channel used in the Endpoint DLP policy triggering this notification message.
-
Under **Message**, you can customize the notification message in any of the languages available from the language drop-down menu. You can customize the message that appears when an Endpoint DLP rule is matched and the configured action is applied:
- **Allow**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule, but the service allows the traffic and logs the activity.
- **Block**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule and the service blocks the activity.
For Endpoint DLP rules that are configured with the Confirm action, the Zscaler service provides an EUN message that is customized separately. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
[See image.](#printing-messages)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **File Name**: Select to include the name of the file that triggered the rule in the notification.
- **Destination**: Select to include the name of the printer to which the file was sent and the rule was triggered in the notification.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **DLP Engines**: Select to include the name of the DLP engines that triggered the rule in the notification.
[See image.](#printing-additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow and Block notification previews.
[See image.](#printing-preview)
- Click **Save** and activate the change.
In addition to the notification message, ensure that the notification customizations shared by all Zscaler Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/unified/configuring-settings-zscaler-client-connector-based-euns) on the Zscaler Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default messages for all actions. This option appears only when you modify the default messages.
-
[]Go to **Policies** >** Common Configuration **>** Resources **> **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Network Share** which would be the channel used in the Endpoint DLP policy triggering this notification message.
-
Under **Message**, you can customize the notification message in any of the languages available from the language drop-down menu. You can customize the message that appears when an Endpoint DLP rule is matched and the configured action is applied:
- **Allow**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule, but the service allows the traffic and logs the activity.
- **Block**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule and the service blocks the activity.
For Endpoint DLP rules that are configured with the Confirm action, the Zscaler service provides an EUN message that is customized separately. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
[See image.](#network-share-messages)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **File Name**: Select to include the name of the file that triggered the rule in the notification.
- **Destination**: Select to include the network share to which the file was copied and the rule was triggered in the notification.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **DLP Engines**: Select to include the name of the DLP engines that triggered the rule in the notification.
[See image.](#network-share-additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow and Block notification previews.
[See image.](#network-share-preview)
- Click **Save** and activate the change.
In addition to the notification message, ensure that the notification customizations shared by all Zscaler Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/unified/configuring-settings-zscaler-client-connector-based-euns) on the Zscaler Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default messages for all actions. This option appears only when you modify the default messages.
-
[]Go to **Policies** >** Common Configuration **>** Resources **> **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Personal Cloud Storage** which would be the channel used in the Endpoint DLP policy triggering this notification message.
-
Under **Message**, you can customize the notification message in any of the languages available from the language drop-down menu. You can customize the message that appears when an Endpoint DLP rule is matched and the configured action is applied:
- **Allow**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule, but the service allows the traffic and logs the activity.
- **Block**: Enter text to customize the notification message that appears when an end user's activity triggers an Endpoint DLP rule and the service blocks the activity.
For Endpoint DLP rules that are configured with the Confirm action, the Zscaler service provides an EUN message that is customized separately. To learn more, see [Configuring User Confirmation Notification Templates](/unified/configuring-user-confirmation-notification-templates).
[See image.](#personal-cloud-storage-messages)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **File Name**: Select to include the name of the file that triggered the rule in the notification.
- **Destination**: Select to include the personal cloud storage to which file was uploaded and the rule was triggered in the notification.
- **Rule Name**: Select to include the name of the triggered rule in the notification.
- **DLP Engines**: Select to include the name of the DLP engines that triggered the rule in the notification.
[See image.](#personal-cloud-storage-additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow and Block notification previews.
[See image.](#personal-cloud-storage-preview)
- Click **Save** and activate the change.
In addition to the notification message, ensure that the notification customizations shared by all Zscaler Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/unified/configuring-settings-zscaler-client-connector-based-euns) on the Zscaler Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default messages for all actions. This option appears only when you modify the default messages.
[]![Removable Storage EUN message language](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/multi-lan-supp-rs.png)
[]![A screenshot of Removable Storage EUN additional information](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/removable-storage-eun-additional-info.png)
[]![Removable Storage EUN preview](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/removable-storage-eun-preview_1.png)
[]![Printing EUN message language](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/multi-lang-supp-pr.png)
[]![A screenshot of Printing EUN additional information](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/printing-eun-additional-info.png)
[]![Printing EUN preview](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/printing-eun-preview_1.png)
[]![Network Share EUN message language](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/multi-lang-supp-ns.png)
[]![A screenshot of Network Share EUN additional information](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/network-share-eun-additional-info.png)
[]![Network Share EUN preview](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/network-share-eun-preview_1.png)
[]![Personal Cloud Storage EUN message language](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/multi-lang-supp-pcs.png)
[]![A screenshot of Personal Cloud Storage EUN additional information](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/personal-cloud-storage-eun-additional-info.png)
[]![Personal Cloud Storage EUN preview](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-endpoint-dlp/personal-cloud-storage-eun-preview_2.png)