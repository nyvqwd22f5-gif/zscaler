# About Zscaler Client Connector-Based End User Notifications
Source: https://help.zscaler.com/unified/about-zscaler-client-connector-based-end-user-notifications
PDF: https://help.zscaler.com/pdf/com/en/1508001.pdf

When network traffic from user devices is blocked or restricted by your security policies, Internet & SaaS can automatically notify users of the policy action through [Zscaler Client Connector](/client-connector/what-is-zscaler-client-connector) installed on users' endpoints. The end user notification (EUN) provides context to users about traffic restrictions enforced by an organization's security policy when they engage in restricted activities and keeps users informed of your corporate policy.
Zscaler Client Connector EUN provides the following benefits and allows you to:
- Enable the use of customized notification messages on a per-rule basis for web and firewall policies.
- Create and manage EUNs for various security policies in a single location and enhance your user experience by fully customizing the notification messages with a unified look and feel.
Zscaler Client Connector-based notifications are supported for the following Internet & SaaS policies:
- [Inline Web Data Loss Prevention (DLP)](/unified/configuring-euns-inline-web-dlp)
- [Endpoint DLP](/unified/configuring-euns-endpoint-dlp)
- [Cloud App Control](/unified/configuring-euns-cloud-app-control)
- [Firewall Filtering](/unified/configuring-euns-firewall-filtering)
- [DNS Control](/unified/configuring-euns-dns-control)
- [IPS Control](/unified/configuring-euns-ips-control)
Zscaler provides a preconfigured notification message for each policy type, which can be customized per requirements. In addition, you can add custom notification messages and associate distinct notification messages with individual policy rules to provide context-sensitive information to end users. You can customize the notification message in [multiple, supported languages](/unified/multiple-language-support-zscaler-client-connector-based-euns) and include or exclude specific details about the traffic conditions. In addition to the notification message, you can customize the [general, shared settings](/unified/configuring-settings-zscaler-client-connector-based-euns) of all EUNs, including the organization name, logo, support details, notification display duration, and more. After customizing the notification message, you need to enable the EUN within the policy rule configuration page and associate an appropriate notification message to display to end users when their traffic matches the rule action. To learn more, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/unified/step-step-configuration-guide-zscaler-client-connector-based-euns).
A maximum of 64 custom messages is supported across policies for an organization. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
About the Client Connector EUN Page
On the Client Connector EUN page (Policies > Common Configuration > Resources > End User Notifications > Client Connector), you can do the following:
- Add a new custom notification message for different policy types.
-
View a list of all notification messages. For each notification message, you can see:
- **Channel**: The type of policy or the category within a policy for which the notification message is configured. For example, Cloud App Control is a type of policy whereas Network Share is a category within the Endpoint DLP policy.
- **Name**: The name of the notification message. Default notifications can be identified by their name.
You can sort the list by either of these fields.
-
Edit or delete a notification message.
Default notification messages cannot be deleted. If a custom message that is currently used in one or more policies is deleted, the default notification message for the corresponding channel is automatically assigned to those policies.
- [Modify the table and its columns.](/unified/using-tables)
- Search for a notification message.
- Configure the [notification settings](/unified/configuring-settings-zscaler-client-connector-based-euns) that are shared by all Zscaler Client Connector-based EUNs.
- Filter the notification list by a specific type of policy or a category within the policy. Selecting **All** displays notification messages configured across the supported policies.
- Go to the [Browser EUN page](/unified/configuring-end-user-notifications).
![Screenshot of Client Connector End User Notifications](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/about-zscaler-client-connector-based-end-user-notifications/client-connector-euns-page_0.png)