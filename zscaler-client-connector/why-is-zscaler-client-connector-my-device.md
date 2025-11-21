# Why Is Zscaler Client Connector on My Device?
Source: https://help.zscaler.com/zscaler-client-connector/why-is-zscaler-client-connector-my-device
PDF: https://help.zscaler.com/pdf/com/en/1308821.pdf

[Watch a video about Zscaler Client Connector.](https://fast.wistia.net/embed/iframe/j78q41slik)
Zscaler is a SaaS security platform that provides fast, secure connections between you and your applications, regardless of device, location, or network. Zscaler Client Connector is an application that allows you to receive all of the benefits of the Zscaler service from your device, even when you are off your corporate network. Zscaler Client Connector forwards your traffic to the Zscaler Internet Access (ZIA) service. It also allows you to use the Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX), and Zscaler Endpoint Data Loss Prevention (DLP) services.
- With the ZIA service, you can protect your internet traffic and allow your users to securely access the internet. This service scans all traffic in real time to ensure compliance with corporate policies and protection from threats. These threats include viruses, advanced threats, malware, phishing attempts, malicious sites, and more.
- With the ZPA service, you can securely access internal applications and services from any location.
- With the ZDX service,Zscaler Client Connector performs synthetic probing to a desired Software as a Service (SaaS) application or internet-based service (e.g., OneDrive, Gmail, etc.) to triage and pinpoint the source of performance issues.
- With the Endpoint DLP service, you can protect your organization from data loss on endpoints (i.e., printing, saving to removable storage, saving to network shares, or uploading to personal cloud storage accounts.
Using Zscaler Client Connector
You must log in to Zscaler Client Connector with your user ID and complete the one-step device enrollment process. Then you can safely connect to the web and your organization's internal resources.
Zscaler Client Connector automatically recognizes when you are connected to a trusted network (i.e., your corporate office network), and depending on your organization's configuration, can disable its ZIA, ZPA, ZDX, or Endpoint DLP service accordingly. It can also recognize when you connect to Wi-Fi hotspots (i.e., airports, hotels, cafés) where you must pay or accept a use policy before connecting. The app disables its services for a period of time and re-enables itself after you've had a chance to complete the steps necessary to connect.
To learn more about using Zscaler Client Connector and its features, see [Using Zscaler Client Connector](/zscaler-client-connector/using-zscaler-client-connector).
You can view the connection status of the ZIA, ZPA, ZDX, and Endpoint DLP services on Zscaler Client Connector:
- On the **Internet Security** page, if the **Status** is **ON**, your internet traffic is protected.
[See image.](#z-app-on-zia)
- On the **Private Access** page, if the **Service Status** is **ON**, you can securely access your internal resources.
[See image.](#z-app-on-zpa)
- On the **Digital Experience** page, if the **Service Status** is **ON**, your network, application, and device performance are being measured.
[See image.](#z-app-on-zdx)
- On the **Data Protection** page, if the **Service Status** is **ON**, endpoint user activity is monitored.
[See image.](#endpoint-dlp-service)
[]![The connection status of ZIA on the Zscaler Client Connector](/downloads/z-app/getting-started/why-zscaler-app-my-device/z-app-zpa-status.png)
[]![The connection status of ZPA on the Zscaler Client Connector](/downloads/z-app/getting-started/why-zscaler-app-my-device/z-app-zia-status.png)
[]![The connection status of ZDX on the Zscaler Client Connector](/downloads/z-app/getting-started/why-zscaler-app-my-device/z-app-zdx-status.png?1602237306)
[![The service status of Endpoint DLP on Zscaler Client Connector](/downloads/tech-pubs-drafts/client-connector-draft-articles/why-zscaler-client-connector-my-device-draft-doc-48428/endpoint-dlp-service-status.jpg)
]
When does Zscaler protect me?
The Zscaler service protects your internet traffic when you connect to your corporate network or to a public internet connection, depending on your organization's configuration. For example, your organization's configuration might mean that you are protected when connected to the corporate network, but you are not protected when connected from home. Your organization can tell you when your connection is protected by Zscaler.
What about privacy?
The Zscaler service does not record or store personal data when you browse the internet. The service only inspects your internet traffic for threats when you are connected to your corporate network or when Zscaler Client Connector is enabled. Your company might also choose to exempt non-corporate applications from inspection.
Depending on your organization’s corporate policy, your organization might track your internet browsing activity. Follow your organization’s terms of service (TOS) when browsing the internet.
Why does my organization need to install a certificate on my device?
If your organization requires it, you might be prompted to install a certificate. This certificate is used to inspect your applications' traffic to protect against security threats. This certificate is typically not used when you access the internet from outside of your organization's network (e.g., home Wi-Fi, cafés, public hotspots) and when you disable Zscaler Client Connector.
What should I be aware of when I browse the internet?
Follow your organization's TOS when browsing the internet. Your organization has configured policies to protect you from harmful websites, and to restrict access to sites that do not conform with its internal internet usage guidelines. Your organization might also limit bandwidth to streaming websites, in order to ensure access to business-related sites is undisrupted.
How do I troubleshoot Zscaler Client Connector?
Zscaler Client Connector displays error messages in the **Status**. You can either:
- [Click** Retry** to resolve the error.](#retry)
- [Click **Repair App** to resolve the error.](#repair-app)
To learn more about connection status errors, see [Zscaler Client Connector: Connection Status Errors](/zscaler-client-connector/zscaler-client-connector-connection-status-errors).
If you encounter an error that is not in the** Status** and has an error code, contact your organization's support team.
[See image.](#Z-App-Error)
You must contact your organization's support team if you experience general issues not specific to Zscaler Client Connector.
[]The **Retry** option appears next to the **Status**.
![The Retry option for Zscaler Client Connector](/downloads/retry-z-app.png)
[]The** Repair App** option appears on the **More** page in the **Troubleshoot** menu.
![The Repair option for Zscaler Client Connector](/downloads/zia/repair-app-z-app.png)
[]![A Zscaler Client Connector error](/downloads/zia/z-app-error.png)
Who should I contact if I experience any issues?
If you experience any issues with your internet connection, contact your organization's support team.
For issues with Zscaler Client Connector (if your organization enables this feature), you can send support request emails directly from the app to your organization's support team, or you can submit tickets directly from the app to Zscaler Support. If this feature is unavailable, contact your organization's support team.
To learn how to report issues from Zscaler Client Connector, see [Reporting an issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector).