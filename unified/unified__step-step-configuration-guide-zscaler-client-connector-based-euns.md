# Step-by-Step Configuration Guide for Zscaler Client Connector-Based EUNs
Source: https://help.zscaler.com/unified/step-step-configuration-guide-zscaler-client-connector-based-euns
PDF: https://help.zscaler.com/pdf/com/en/1529665.pdf

This guide describes the configuration steps for displaying notifications to users through Zscaler Client Connector when the user activity triggers a Internet & SaaS policy action. You can customize these notifications and associate them with individual policy rules as explained in the following steps. To learn more, see [About Zscaler Client Connector-Based End User Notifications](/unified/about-zscaler-client-connector-based-end-user-notifications).
Prerequisites
Before configuring Zscaler Client Connector EUNs, ensure that you meet the necessary requirements based on the policy type:
- [Inline Web Data Loss Prevention (DLP)](#web-dlp-eun-requirement)
- [Endpoint DLP](#endpoint-dlp-eun-requirement)
- [Cloud App Control](#cloud-app-control-eun-requirement)
- [Firewall Filtering](#firewall-filtering-eun-requirement)
- [DNS Control](#dns-control-eun-requirement)
- [IPS Control](#ips-control-eun-requirement)
Configuring Zscaler Client Connector-Based EUNs
To configure Zscaler Client Connector-based EUNs:
- [Step 1: Enable EUNs in Zscaler Client Connector](#enable-eun)
- [Step 2: (Optional) Customize Notification Messages](#customize-notification-message)
- [Step 3: (Optional) Customize Notification Settings](#customize-notification-settings)
- [Step 4: Use Notifications in Policy Rules](#associate-eun-policy-rule)
[]Ensure that you have EUN customization enabled for your organization and complete the necessary configurations depending on the policy type:
- [Inline Web Data Loss Prevention (DLP)](#zscaler-client-connector-web-dlp-eun)
- [Endpoint DLP](#zscaler-client-connector-endpoint-dlp-eun)
- [Cloud App Control](#zscaler-client-connector-cloud-app-control-eun)
- [Firewall Filtering](#zscaler-client-connector-firewall-filtering-eun)
- [DNS Control](#zscaler-client-connector-dns-eun)
- [IPS Control](#zscaler-client-connector-ips-eun)
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows or macOS) and enable the **Install Endpoint ZDP** option.
EUNs for Inline Web DLP and Cloud App Control are supported as a standalone feature, without requiring Endpoint DLP. Depending on your organization's subscription, the Endpoint ZDP agent activates either Endpoint DLP (includes EUN) or standalone EUN.
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows or macOS) and enable the **Install Endpoint ZDP** option.
You must have Endpoint DLP in Zscaler Client Connector to use these EUNs.
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows or macOS) and enable the **Install Endpoint ZDP** option.
EUNs for Inline Web DLP and Cloud App Control are supported as a standalone feature, without requiring Endpoint DLP. Depending on your organization's subscription, the Endpoint ZDP agent activates either Endpoint DLP (includes EUN) or standalone EUN.
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows only) and enable the **ZIA Notification Framework** option. Additionally, you must select a Notification Template for your App Profile that has **ZIA Firewall** and **Firewall Popup Notifications** options enabled.
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows only) and enable the ZIA Notification Framework option. Additionally, you must select a Notification Template for your App Profile that has **DNS** and **DNS Popup Notifications** options enabled.
[]Configure an [App Profile](/unified/configuring-zscaler-client-connector-app-profiles) for your devices (Windows only) and enable the ZIA Notification Framework option. Additionally, you must select a Notification Template for your App Profile that has **IPS** and **IPS Popup Notifications** options enabled.
[]You can modify the default messages provided by Zscaler and additionally create custom notification messages. You can customize the message component of the notification in [multiple languages](/unified/multiple-language-support-zscaler-client-connector-based-euns) supported and choose to include additional details about the traffic and policy conditions. You can create multiple, distinct notification messages for each policy and its subcategories (referred to as "channels").
To learn more, see:
- [Configuring EUNs for Inline Web DLP](/unified/configuring-euns-inline-web-dlp)
- [Configuring EUNs for Endpoint DLP](/unified/configuring-euns-endpoint-dlp)
- [Configuring EUNs for Cloud App Control](/unified/configuring-euns-cloud-app-control)
- [Configuring EUNs for Firewall Filtering](/unified/configuring-euns-firewall-filtering)
- [Configuring EUNs for DNS Control](/unified/configuring-euns-dns-control)
- [Configuring EUNs for IPS Control](/unified/configuring-euns-ips-control)
[]In addition to customizing the notification message, you can modify general settings, such as organization name, logo, support details, notification duration, and more. These attributes are shared by all Zscaler Client Connector-based notifications across policies.
To learn more, see [Configuring Settings for Zscaler Client Connector-Based EUNs](/unified/configuring-settings-zscaler-client-connector-based-euns).
[]After customizing the notifications, you can configure the respective policy rules to show EUNs when a specific rule action is triggered and select the notification message to display.
To learn more, see:
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring Endpoint DLP Policy Rules](/unified/configuring-endpoint-dlp-policy-rules)
- [Adding Rules to the Cloud App Control Policy](/unified/adding-rules-cloud-app-control-policy)
- [Configuring the Firewall Filtering Policy](/unified/configuring-firewall-filtering-policy)
- [Configuring the DNS Control Policy](/unified/configuring-dns-control-policy)
- [Configuring the IPS Control Policy](/unified/configuring-ips-control-policy)
[]
-
-
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Endpoint DLP (includes EUN) or EUN as a standalone feature must be enabled. Standalone EUN feature requires:For Windows: 4.6.0.123 or laterFor macOS: 4.3.1.56 or later |
| In ZIA | Contact Zscaler Support to enable EUN for Inline Web DLP. |
[]
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Endpoint DLP must be enabled. |
| In ZIA | Endpoint DLP policy must be enabled. |
[]
-
-
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Endpoint DLP (includes EUN) or EUN as a standalone feature must be enabled. Standalone EUN feature requires:For Windows: 4.6.0.123 or laterFor macOS: 4.3.1.56 or later |
| In ZIA | Contact Zscaler Support to enable EUN for Cloud App Control. |
[]
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. |
| In ZIA | Firewall Filtering policy must be enabled with Advanced Firewall. |
[]
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. |
| In ZIA | DNS Control Policy must be enabled with Advanced DNS, which is provided by the Advanced Firewall. |
[]
| Requirement | Details |
| ----------- | ------- |
| In Zscaler Client Connector | Supported on Windows devices running Zscaler Client Connector version 4.8 or later over Z-Tunnel 2.0. |
| In ZIA | IPS Control policy must be enabled through Advanced Firewall. |