# Configuring EUNs for Inline Web DLP
Source: https://help.zscaler.com/zia/configuring-euns-inline-web-dlp
PDF: https://help.zscaler.com/pdf/com/en/1486486.pdf

You can customize the messages for Zscaler Client Connector-based notifications that are displayed for end users when an [inline web DLP policy](/zia/about-data-loss-prevention) configured in ZIA is triggered by the end user's activity. For example, you can block users from posting personally identifiable information (PII) on third-party websites and display a notification informing the user regarding the policy violation. In another scenario, you can allow a user to upload a file containing sensitive corporate information to the user's personal storage and display a notification cautioning the user about the risks associated and that the activity is monitored.
These End User Notifications (EUNs) are triggered by ZIA based on your policy configuration and are issued by the Client Connector service that is installed on the users' endpoints. You can customize various elements of the notification, including the notification message for different policy actions, company name, logo, information displayed on the notification, duration of the notification, and more. You can modify the default notification message that's preconfigured in the ZIA Admin Portal and additionally create custom messages to allow the selection of different notification messages for individual DLP rules. This allows you to display customized notification messages for different types of audiences (e.g., partners and organization employees). To learn more, see [About Zscaler Client Connector-Based End User Notifications](/zia/about-zscaler-client-connector-based-end-user-notifications).
EUNs are supported for different types of DLP rules, including DLP rules that use Zscaler's DLP engines for content inspection and DLP rules that only use specific criteria to filter data. To display the EUN for a specific DLP rule, you need to enable EUN within the rule configuration page and select the notification message that must be used for that particular rule. To learn more about DLP policy configuration, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection) and [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection).
This article describes how you can customize the EUN messages used in the Inline Web DLP policy. To learn more about how to enable and configure EUNs, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/zia/configuring-euns-inline-web-dlp).
To create a custom notification message for Client Connector-based EUN triggered by DLP policy:
-
Go to **Administration** > **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**, provide the following basic information about the custom message:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Inline Web **which would be the policy triggering this notification message.
-
Under **Message**, you can customize the notification message in any of the languages available from the language drop-down menu. You can customize notification messages that are displayed for end users when a policy matches with the traffic and the configured action to allow or block the traffic is taken:
- **Allow**: Enter text to customize the notification message that appears when an end user's activity triggers a DLP rule, but the service allows and logs the activity.
- **Block**: Enter text to customize the notification message that appears when an end user's activity triggers a DLP rule and the service blocks the activity.
You can embed links in the message content by using the following format: `__url[Link text | example.com]` (note the double underscore at the beginning). For example, `__url[Learn more | https://acme.com/policy]`. You can also introduce line breaks in the message content by using the `//n` character.
[See image.](#custom-message)
-
Under **Additional Information**, select the additional information that must be displayed in the notification:
- **File Name**: Select to show the name of the file that triggered the rule.
- **Destination**: Select to show the domain name to which traffic was sent and that triggered the rule.
- **Rule Name**: Select to show the name of the triggered rule.
- **URL Category**: Select to show the category of the URL that triggered the rule.
- **URL**: Select to show the URL that triggered the rule.
- **DLP Engines**: Select to show the name of the DLP engines that triggered the rule.
[See image.](#additional-info)
-
Under **Preview**, you can get a full view of the notification message you configured, including the customization options available under [Settings](/zia/configuring-settings-zscaler-client-connector-based-euns), such as company name, logo, support information, etc. You can interact with the notification previews by clicking the **Show More** button to view the additional details configured. Use the **Next** and **Previous** icons to navigate through the Allow and Block notification previews.
[See image.](#preview)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
In addition to the notification message, ensure that the notification customizations shared by all Client Connector-based EUNs are configured as needed. These customizations are available under the [Settings option](/zia/configuring-settings-zscaler-client-connector-based-euns) on the Client Connector EUN page.
You can edit both default and custom notification messages to customize them based on your requirements subject to the following conditions:
- The Channel field is non-editable in both default and custom messages
- The Name field is non-editable in default messages
The default notification additionally provides a **Reset All** option that allows you to restore the default messages for all actions. This option appears only when you modify the default messages.
[][![Custom EUN message configuration for Inline Web DLP policy](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-inline-web-dlp/zia-client-connector-eun-inline-web.png)
](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-inline-web-dlp/inline-web-dlp-custom-eun_0.png)
[]![Inline Web DLP EUN custom message additional info](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-inline-web-dlp/inline-web-additional-info.png)
[]![Inline Web DLP EUN custom message preview](/downloads/zia/authentication-administration/end-user-notifications-euns/client-connector-euns/configuring-euns-inline-web-dlp/inline-web-EUN-preview.png)