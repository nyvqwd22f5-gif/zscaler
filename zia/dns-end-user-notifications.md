# DNS End User Notifications
Source: https://help.zscaler.com/zia/dns-end-user-notifications
PDF: https://help.zscaler.com/pdf/com/en/1529651.pdf

Zscaler supports different types of End User Notifications (EUNs) for the DNS Control policy. These EUNs are displayed to end users when their activities trigger DNS Control rules with specific actions, such as blocking traffic or redirecting responses. All these notifications are configured at the individual rule level. The following table provides an overview of the EUNs supported and distinguishes key features between different EUN types:
[](#eun-ip)[]
-
-
[](/zia/authentication-administration/end-user-notifications/browser-euns)[](/zia/choosing-ca-certificate-ssl-inspection)
| DNS EUN Type | DNS Basic Web EUN (Static Web EUN) | DNS Advanced Web EUN (Integrated with ZIA Web Proxy) | Zscaler Client Connector-Based EUN |
| ------------ | ---------------------------------- | ---------------------------------------------------- | ---------------------------------- |
| Advantage | Eliminates the need for organizations to host and manage their own web notification page. | Zscaler Client Connector displays a pop-up notification to notify users of DNS Control policy actions. |
| Use Case | Best used for unauthenticated users such as in guest Wi-Fi situations where a web EUN is presented. | Ideal for authenticated users for seamless web experience with SSL/TLS decryption. It can also be used for unauthenticated users from existing locations. | Ideal for user devices running Zscaler Client Connector. |
| Dependencies | Web EUN requests can reach the EUN web server via ZIA or directly through the internet (without going via ZIA). | Web EUN requests must be sent to ZIA using standard forwarding methods (via Generic Routing Encapsulation (GRE), Internet Protocol Security (IPSec) tunnel, or Z-Tunnel 2.0) or from a known location defined in ZIA (guest W-Fi scenario). | Supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. |
| Policy Configuration | Enabled on a per-rule basis in DNS Control, requiring manual configuration of an EUN IP address using the Redirect Response action in a DNS Control rule. | Enabled on a per-rule basis in DNS Control using the Block action in rules with an additional option to enable the web EUN notification. | Enabled on a per-rule basis for Block, Block with Response Code, and Redirect Response actions in DNS Control, with an option to select the default or custom notification message. |
| DNS Request Types | Applicable to DNS A requests. | Applicable to DNS A and AAAA requests. | Applicable to all DNS traffic managed by the DNS Control. |
| EUN IP Addresses and FQDNs | **Fixed IP**: `34.215.46.88`**FQDN**: `blockpage.zscaler.com` (a CNAME record that resolves to IP addresses that could change). | Zscaler-managed web page. | N/A |
| EUN Web Page Customization Support | Static, non-customizable. | Standard customization available for web EUN. | Fully customizable—including custom notification message, layout, additional details to display, and more. |
| Certificate Trust Requirements | Zscaler Certificate Authority (CA) certificate is not used. However, if a web EUN request is sent via ZIA with SSL inspection enabled, the client browser or device needs to trust the Zscaler CA certificate (or the custom certificate that the organization uses). | Client browser or device is required to trust the Zscaler CA certificate (or the custom certificate that the organization uses). To learn more, see Choosing the CA Certificate for SSL Inspection. | N/A |
| Applicable Traffic | Primarily designed to support HTTP-based web EUN requests, with potential compatibility for HTTPS-based web EUN requests depending on browser behavior, which is outside of Zscaler's control. | Supported for HTTP- and HTTPS-based web EUN requests. | Supported for all DNS transactions managed by the DNS Control, including DNS over UDP, TCP, and HTTPS. |
The following sections provide further detailed information on each DNS EUN type and how to configure them in ZIA.
DNS Advanced Web EUN (Integrated with ZIA Web Proxy)
Zscaler provides a standard EUN page for web traffic that is built into the secure web gateway's (i.e., web proxy's) EUN infrastructure and therefore seamlessly integrated with the policy action. This EUN is supported along with the DNS Control policy's Block action, so the EUN displays to users when their traffic is blocked, informing them of your organization's policy restriction. Configuring this EUN in the DNS Control policy requires enabling the web EUN within the rule. Zscaler hosts this EUN web page, eliminating the need for organizations to host their own EUN web page. You can customize the notification to display your organization's name, logo, and a custom message to inform users of why access to specific sites is blocked.
The EUN web page is served only for DNS requests corresponding to A and AAAA DNS record types. It is accessible for web traffic routed through ZIA using standard forwarding methods (via GRE, IPSec tunnel, or Z-Tunnel 2.0). This page is also accessible for web traffic that is sent directly to the web server's resolved IP address without being routed through ZIA (e.g., guest Wi-Fi environment), but the traffic should come from a known location (i.e., source IP address registered as a [location](/zia/configuring-locations) in ZIA).
The EUN web page is accessible over HTTP and HTTPS. For HTTPS access, a [Zscaler intermediate CA certificate or a custom certificate](/zia/about-intermediate-ca-certificates) that the organization configures is used to complete a Transport Layer Security (TLS) handshake with the client. If the user's device has a Zscaler certificate installed, no certificate warning displays. However, in guest Wi-Fi environments where a certificate is not installed on the user's device, a certificate error or warning displays in the browser.
This web EUN configuration is supported only with the Block action of the DNS Control policy.
The following sections describe how to customize the web EUN and configure it in DNS Control rules:
- [1. (Optional) Customize the Web EUN.](#customize-web-eun)
- [2. Configure the Web EUN in DNS Control rules.](#configure-web-eun)
DNS Basic Web EUN (Static Web EUN)
This is a static EUN web page that Zscaler hosts and fully manages at a publicly routable IP address: `34.215.46.88`. You can redirect users to this static web EUN page by manually configuring this IP address in the DNS Control policy using the Redirect Response action. The Redirect Response action replaces the IP address of the resolved hostname in the DNS response with a preferred IP address before sending the response to the client. Organizations can use this Redirect Response action to direct users to an EUN page when access to a domain is blocked. The EUN page can either be the Zscaler-hosted static EUN web page hosted at `34.215.46.88` or a custom EUN web page hosted at a dedicated IP address managed by the organization.
The Zscaler-hosted EUN web page eliminates the need for organizations to host and manage their own notification page. This static DNS EUN web page is primarily designed to support HTTP-based web EUN requests, with potential compatibility for HTTPS-based web EUN requests depending on browser behavior, which is outside of Zscaler's control. It is available for tunneled traffic (sent via GRE, IPSec tunnel, or Z-Tunnel 2.0) and is also accessible to users whose web traffic is not sent through forwarding tunnels and unauthenticated users, making it well-suited for guest Wi-Fi environments and similar scenarios. To learn more, see [DNS Static Web End User Notification](/zia/dns-static-web-end-user-notification).
This static EUN configuration is supported only with the Redirect Response action of the DNS Control policy. This EUN web page is non-customizable.
To configure this static EUN for a DNS Control rule:
- Go to **Policy** > **DNS Control**, and add a new rule or edit an existing rule.
- On the DNS rule configuration page, select the necessary rule conditions.
-
Under **Action**:
- Select **Redirect Response **from the **Network Traffic** drop-down menu.
- Enter `34.215.46.88` in the **IP Address** field.
[See image.](#redirect-response-zscaler-web-eun)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
Zscaler Client Connector-Based EUN
This EUN is displayed through Zscaler Client Connector installed on a user's endpoint when the user activity triggers a DNS Control rule configured with the EUN. It uses the [ZIA Notification Framework](/zscaler-client-connector/using-zscaler-notification-framework) that is bundled with Zscaler Client Connector and extends EUN support for various ZIA policies. This EUN is integrated with the DNS Control policy and allows you to enable the notification on a per-rule basis. It is supported with the DNS rule's Block, Block with Response Code, and Redirect Response actions, enabling organizations to show this notification to end users when they access blocked traffic or when a DNS redirect is performed. Configuring this EUN in the DNS Control policy requires enabling the Zscaler Client Connector EUN option and selecting an appropriate notification message within the policy rule.
Zscaler provides a ready-to-use, editable notification message by default. In addition, you can create fully customized notification messages and associate distinct messages with individual DNS rules, depending on your requirements. This EUN is ideal for endpoints running Zscaler Client Connector and is displayed for policy violations detected in DNS traffic managed the DNS Control.
- This EUN is supported on Windows devices running Zscaler Client Connector version 4.8 and later over Z-Tunnel 2.0.
- The EUN configuration is supported with Block, Block with Response Code, and Redirect Response actions of the DNS Control policy.
- The DNS Advanced Web EUN and Zscaler Client Connector EUN cannot function simultaneously. When both options are enabled, the Web EUN takes precedence and only this notification is displayed to users.
The following sections describe how to customize the Zscaler Client Connector EUN and configure it in DNS Control rules:
- [1. (Optional) Customize the notification message.](/zia/configuring-euns-dns-control)
- [2. Configure the Zscaler Client Connector EUN in DNS Control rules.](#configure-zscaler-client-connector-eun-dns)
- []Go to **Policy** > **DNS Control**, and add a new rule or edit an existing rule.
- On the DNS rule configuration page, select the necessary rule conditions.
- Under **Action**, select **Block **or **Redirect Response** action from the **Network Traffic** drop-down menu, as required for the rule.
-
Under **Notification**:
- Select **Enable** for **Client Connector EUN**.
- Select the default or custom message from the **Notification Message** drop-down menu.
[See image.](#enable-zscaler-client-connector-eun)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []Go to **Administration** > **End User Notifications** > **Browser** > **Global EUN Configuration**.
- With the **Notification Type** set to **Default**, you can customize the following settings:
-
In the **Configure Notifications** section:
- **Display Reason**: Enable to display the reason for blocking access in the notification.
- **Display Company Name**: Enable to include your organization's name in the notification.
- **Display Company Logo**: Enable to display your organization's logo in the notification. You can upload your organization's logo on the [Company Profile](/zia/about-company-profile) page.
-
In the text box, provide a custom message to be displayed in the notification. You can [customize the appearance](/zia/customizing-euns-css-styles) of this notification with CSS styles.
This option allows you to customize a portion of the notification message. Some texts in the notification are auto-generated based on policy restrictions and are not customizable.
[See image.](#customize-dns-web-eun)
-
In the **IT Support** section, you can provide contact details such as email address and phone number and include a link to your organization's policy.
[See image.](#customize-dns-web-eun-support-info)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
These customization settings are shared by other browser-based EUNs, such as block notifications for other policies, caution messages, and quarantine notifications, so ensure that the customizations are considered globally for all browser-based EUNs.
- []Go to **Policy** > **DNS Control**, and add a new rule or edit an existing rule.
- On the DNS rule configuration page, select the necessary rule conditions.
-
Under **Action**:
- Select **Block **from the **Network Traffic** drop-down menu.
- Select **Enable** for **Web EUN**.
[See image.](#block-action-web-eun)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn more, see [Configuring the DNS Control Policy](/zia/configuring-dns-control-policy).
[]![Configuring Redirect Response action with IP address to show Zscaler web EUN page](/downloads/zia/policies/firewall/dns-control/dns-end-user-notifications/dns-rule-web-eun-redirect-response-action.png)
[]![Enabling to show Zscaler DNS EUN page for Block action](/downloads/zia/policies/firewall/dns-control/dns-end-user-notifications/dns-block-action-web-proxy-eun.png)
[]![Customizing DNS web EUN to include organization's name, logo, and custom message](/downloads/zia/policies/firewall/dns-control/dns-end-user-notifications/dns-browser-eun-customization.png)
[]![Customizing DNS web EUN to include organization's name, logo, and custom message](/downloads/zia/policies/firewall/dns-control/dns-end-user-notifications/dns-browser-eun-customize-support-info.png)
[]![Customizing DNS web EUN to include organization's name, logo, and custom message](/downloads/zia/policies/firewall/dns-control/dns-end-user-notifications/dns-zscaler-client-connector-eun.png)