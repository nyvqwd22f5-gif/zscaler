# Configuring EUNs for IPS Control
Source: https://help.zscaler.com/unified/configuring-euns-ips-control
PDF: https://help.zscaler.com/pdf/com/en/1533612.pdf

When network traffic from your user devices is allowed or blocked by the IPS Control policy, Internet & SaaS can notify users of the policy action through the Zscaler Client Connector service installed on users' endpoints. Zscaler provides a ready-to-use, editable notification message by default. Additionally, you can create custom messages and associate distinct notification messages with individual IPS Control rules, depending on your requirements. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
- To access this feature, you must have the IPS Control policy which is provided by the Advanced Firewall.
- This EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. You must also have configured the required settings in the Zscaler Client Connector Portal to display Internet & SaaS IPS notifications. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
To add a custom notification message:
-
Go to **Policies **>** Common Configuration **>** Resources** > **End User Notifications **>** Client Connector **and click **Add Custom Message.**
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **IPS**, the policy type for which you are configuring the notification message.
-
Under **Message**, you can customize notification messages for the policy actions for which the EUN is supported. Select the required language from the drop-down menu and customize the message for the following actions:
- **Allow**: Enter text to customize the notification message that appears when the service detects potentially malicious activity but allows the traffic based on the configured IPS policy.
-
**Block**:** **Enter text to customize the notification message that appears when the service blocks the user activity.
The **Block** message applies to both **Block/Drop** and **Block/Reset** actions of the IPS Control policy.
You can embed links in the message content by using the following format: `__url[``Link text`` | ``example.com``]` (note the double underscore at the beginning). For example, `__url[Learn more | https://acme.com/policy]`. You can also introduce line breaks in the message content by using the `//n` character.
Additionally, a **Reset All** option appears in the **Message** section when the default message or additional information in the following section is modified. You can restore the original notification configurations by clicking this option.
-
Under **Additional Information**, you can select to include the following information in the notification:
- **Threat Name**: The name of the threat detected in the traffic.
- **Threat Category**: The category of the threat detected in the traffic.
- **Threat Severity**: The severity of the threat detected.
- **Threat Score**: The score assigned to the threat detected.
- **Network Service**: The network service identified in the traffic and matched with the rule.
- **Server Destination IP**: The destination server's IP address.
- **Destination Country**: The country where the destination server is located.
You can view Zscaler's listing of threats and specific threat information, including threat severity and score, in the [Zscaler Threat Library](https://threatlibrary.zscaler.com).
-
Under **Preview**, you can view your configured notification message. You can click **Show More** to view the full notification with additional details, and use the **Next** and **Previous** icons to navigate through the Block and Redirect Response notification previews.
The notification preview also includes the customization made under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), which are general, shared settings applicable to all Zscaler Client Connector-based EUNs, such as organization name, logo, and support details.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[See image.](#custom-message-ips)
You can edit both default and custom notification messages subject to the following conditions:
- The Channel field is non-editable in both default and custom messages.
- The Name field is non-editable in default messages.
After customizing the notification message, you need to [enable the EUN](/unified/configuring-ips-control-policy) within an IPS Control rule and associate an appropriate notification message to display to end users when their traffic matches the controlled activity. To learn more, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/unified/step-step-configuration-guide-zscaler-client-connector-based-euns).
[]![Add custom message for IPS channel of Zscaler Client Connector EUN](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-ips-control/zscaler-client-connector-eun-ips.png)