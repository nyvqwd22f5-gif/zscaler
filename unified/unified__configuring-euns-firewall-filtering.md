# Configuring EUNs for Firewall Filtering
Source: https://help.zscaler.com/unified/configuring-euns-firewall-filtering
PDF: https://help.zscaler.com/pdf/com/en/1533610.pdf

When network traffic from your users' devices is blocked by the Firewall Filtering policy, Internet & SaaS can notify users of the policy action through the Zscaler Client Connector service installed on users' endpoints. Zscaler provides a ready-to-use, editable notification message by default. Additionally, you can create custom messages and associate distinct notification messages with individual Firewall Filtering rules, depending on your requirements. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
- This feature configuration requires Advanced Firewall.
- The EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. You must also have configured the required settings in the Zscaler Client Connector Portal to display Internet & SaaS Firewall notifications. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
To add a custom notification message:
-
Go to **Policies **> **Common Configuration** > **Resources** >** End User Notifications **> **Client Connector **and click **Add Custom Message.**
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **Firewall**, the policy type for which you are configuring the notification message.
-
Under **Message**, you can customize notification messages for the policy actions for which the EUN is supported. You can customize the text in any of the supported languages by selecting the language from the drop-down menu.
In the **Block** field, enter text to customize the notification message that appears when the service blocks the user activity.
This message applies to all block actions of the Firewall Filtering policy, including **Block/Drop**, **Block/ICMP**, and **Block/Reset** actions.
You can embed links in the message content by using the following format: `__url[``Link text`` | ``example.com``]` (note the double underscore at the beginning). For example, `__url[Learn more | https://acme.com/policy]`. You can also introduce line breaks in the message content by using the `//n` character.
Additionally, a **Reset All** option appears in the **Message** section when the default message or additional information in the following section is modified. You can restore the original notification configurations by clicking this option.
- Under **Additional Information**, you can select to include the following information in the notification:
- **Network Service**: The network service that was matched.
- **Server Destination IP**: The destination server's IP address or domain that was matched.
- **Network Application**: The network application that was matched.
- **Application Service Group**: The network application service group that was matched.
- **Client Source IP**: The client's source IP address that was matched.
- **Server Destination Port**: The destination server's port that was matched.
- **Server Destination Protocol**: The protocol defined in the Network Service criteria that was matched.
-
Under **Preview**, you can view your configured notification message. You can click **Show More** to view the full notification with additional details.
The notification preview also includes the customization made under [Settings](/unified/configuring-settings-zscaler-client-connector-based-euns), which are general, shared settings applicable to all Zscaler Client Connector-based EUNs, such as organization name, logo, and support details.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[See image.](#firewall-eun-custom-message)
You can edit both default and custom notification messages subject to the following conditions:
- The Channel field is non-editable in both default and custom messages.
- The Name field is non-editable in default messages.
After customizing the notification message, you need to [enable the EUN](/unified/configuring-firewall-filtering-policy) within a Firewall Filtering rule and associate an appropriate notification message to display to end users when their traffic matches the controlled activity. To learn more, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/unified/step-step-configuration-guide-zscaler-client-connector-based-euns).
[]![Add custom message for Firewall channel of Zscaler Client Connector EUN](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-firewall-filtering/zscaler-client-connector-eun-firewall.png)