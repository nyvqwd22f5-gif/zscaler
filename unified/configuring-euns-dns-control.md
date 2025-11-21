# Configuring EUNs for DNS Control
Source: https://help.zscaler.com/zia/configuring-euns-dns-control
PDF: https://help.zscaler.com/pdf/com/en/1532833.pdf

When network traffic from your users' devices is blocked by the DNS Control policy or a DNS redirect is performed, ZIA can notify users of the policy action through the Zscaler Client Connector service installed on users' endpoints. Zscaler provides a ready-to-use, editable notification message by default. Additionally, you can create custom messages and associate distinct notification messages with individual DNS Control rules, depending on your requirements. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/zia/about-zscaler-client-connector-based-end-user-notifications).
- This feature configuration requires Advanced DNS which is provided by the Advanced Firewall.
- The EUN is supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. You must also have configured the required settings in the Zscaler Client Connector Portal to display ZIA DNS notifications. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
To add a custom notification message:
-
Go to **Administration** > **End User Notifications** > **Client Connector** and click **Add Custom Message**.
The **Add Custom Message** window appears.
- In the **Add Custom Message** window:
- Under **General**:
- **Name**: Enter a unique name for the custom message.
- **Channel**: Select **DNS**, the policy type for which you are configuring the notification message.
-
Under **Message**, you can customize notification messages for the policy actions for which the EUN is supported. Select the required language from the drop-down menu and customize the message for the following actions:
-
**Block**: Enter text to customize the notification message that appears when the service blocks the user activity.
The **Block** message applies to both **Block** and **Block with Response Code** actions of the DNS Control policy.
- **Redirect Response**: Enter text to customize the notification message that appears when a DNS redirect is performed.
You can embed links in the message content by using the following format: `__url[``Link text`` | ``example.com``]` (note the double underscore at the beginning). For example, `__url[Learn more | https://acme.com/policy]`. You can also introduce line breaks in the message content by using the `//n` character.
Additionally, a **Reset All** option appears in the **Message** section when the default message or additional information in the following section is modified. You can restore the original notification configurations by clicking this option.
- Under **Additional Information**, you can select to include the following information in the notification:
- **Request Category**: The URL category of the DNS request.
- **Response Category**: The URL category of the DNS response.
- **Resolved IP**: The IP address to which the DNS request was resolved.
- **DNS Tunnel**: DNS tunnels and network applications identified in the DNS traffic.
- **Requested Domain**: The domain name for which DNS resolution was requested.
- **Server IP**: The DNS server IP address.
- **Protocol**: The protocol used by the DNS request.
- **Resolved IP-Based Country**: The country where the destination server is located.
-
Under **Preview**, you can view your configured notification message. You can click **Show More** to view the full notification with additional details, and use the **Next** and **Previous** icons to navigate through the Block and Redirect Response notification previews.
The notification preview also includes the customization made under [Settings](/zia/configuring-settings-zscaler-client-connector-based-euns), which are general, shared settings applicable to all Zscaler Client Connector-based EUNs, such as organization name, logo, and support details.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[See image.](#custom-message-dns)
You can edit both default and custom notification messages subject to the following conditions:
- The Channel field is non-editable in both default and custom messages.
- The Name field is non-editable in default messages.
After customizing the notification message, you need to [enable the EUN](/zia/configuring-dns-control-policy) within a DNS Control rule and associate an appropriate notification message to display to end users when their traffic matches the controlled activity. To learn more, see the [Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs](/zia/step-step-configuration-guide-zscaler-client-connector-based-euns).
[]![Add custom message for DNS channel of Zscaler Client Connector EUN](/downloads/zia/authentication-administration/end-user-notifications-euns/zscaler-client-connector-euns/configuring-euns-dns-control/zscaler-client-connector-eun-dns.png)