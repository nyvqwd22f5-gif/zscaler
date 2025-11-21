# Configuring EUNs for Cloud App Control
Source: https://help.zscaler.com/zia/configuring-euns-cloud-app-control
PDF: https://help.zscaler.com/pdf/com/en/1486501.pdf

You can customize the messages for Zscaler Client Connector-based notifications that are displayed for end users when a [Cloud App Control policy](/zia/about-cloud-app-control) configured in ZIA is triggered by the end user's activity. For example, you can block your organization users from interacting with and uploading files to AI and ML applications such as ChatGPT and Google Gemini and display a notification informing the user regarding the policy violation.
Client Connector-based notification for end users is supported only for Block rules under specific conditions when the application access is allowed but specific interactions with the application are blocked (e.g., viewing a social networking site is allowed but posting content is blocked).
These end user notifications (EUNs) are triggered by ZIA based on your policy configuration and are issued by the Client Connector service that is installed on the users' endpoints. You can customize various elements of the notification, including the notification message for different policy actions, company name, logo, information displayed on the notification, duration of the notification, and more. You can modify the default notification message that is preconfigured in the ZIA Admin Portal and additionally create custom messages to allow the selection of different notification messages for individual Cloud App Control rules. This allows you to display customized notification messages for different types of audiences (e.g., partners and organization employees). To learn more, see [About Zscaler Client Connector-Based End User Notifications](/zia/about-zscaler-client-connector-based-end-user-notifications).
To display the EUN for a specific Cloud App Control rule, you need to enable the EUN within the rule configuration page and select the notification message that must be used for that particular rule. To learn about Cloud App Control policy configuration, see [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
This article describes how you can customize the EUN messages used in the Cloud App Control policy. To learn more about how to enable and configure EUNs, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/zia/step-step-configuration-guide-zscaler-client-connector-based-euns).
To create a custom notification message for Client Connector-based EUN triggered by Cloud App Control policy:
-
Go to **Administration** > **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**, provide the following basic information about the custom message:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Cloud App Control** which would be the policy triggering this notification message.
-
Under **Message**, enter text to customize the **Block** notification message that appears when an end user's activity triggers a Cloud App Control rule and the service blocks the activity. You can customize the notification message in any of the languages available from the language drop-down menu.
Client Connector-based EUNs are supported only for Block rules in Cloud App Control policy under specific conditions. To learn more, see [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
You can embed links in the message content by using the following format: `__url[Link text | example.com]` (note the double underscore at the beginning). For example, `__url[Learn more | https://acme.com/policy]`. You can also introduce line breaks in the message content by using the `//n` character.
[See image.](#custom-message)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **Destination**: Select to show the application name to which traffic was sent and that triggered the rule.
- **Rule Name**: Select to show the name of the triggered rule.
- **App Activity**: Select to show the cloud application activity that triggered the rule.
- **URL**: Select to show the URL that triggered the rule.
- **App Category**: Select to show the category of the cloud application that triggered the rule.
[See image.](#additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/zia/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow and Block notification previews.
[See image.](#preview)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
In addition to the notification message, ensure that the notification customizations shared by all Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/zia/configuring-settings-zscaler-client-connector-based-euns) on the Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default message. This option appears only when you modify the default message.
[]![Cloud App Control EUN message with multi-language support](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-cloud-app-control/zia-client-connector-eun-cloud-app-control.png)
[]![Cloud App Control EUN additional information](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-cloud-app-control/cloud-app-eun-additional-info.png)
[]![Cloud App Control EUN preview](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-cloud-app-control/cloud-app-control-EUN-preview.png)