# Configuring Gmail for Zscaler Outbound Email DLP
Source: https://help.zscaler.com/unified/configuring-gmail-zscaler-outbound-email-dlp
PDF: https://help.zscaler.com/pdf/com/en/1518601.pdf

Zscaler Outbound Email Data Loss Prevention (DLP) allows you to establish a connection between your Gmail server and Zscaler's cutting-edge Data Loss Prevention (DLP) tools to prevent the exfiltration of sensitive data in outbound emails sent to external domains. To do so, you must configure routing to allow bidirectional communication between your Gmail server and the Zscaler smart host, and you must configure compliance rules to determine how mail flows from your Gmail server to the Zscaler service, and vice versa.
This article explains how to configure your Gmail server to use a Zscaler smart host for a basic use case. To learn more about configuring your Gmail server for other use cases, refer to the [Google technical documentation](https://support.google.com/a/topic/9202). To learn about configuring your Microsoft Exchange server for Outbound email DLP, see [Configuring Microsoft Exchange for Zscaler Outbound Email DLP](/unified/configuring-microsoft-exchange-zscaler-outbound-email-dlp).
Configuration changes in the Google Admin console can sometimes take up to 24 hours to propagate across Google Services before reaching your users. To learn more, refer to the [Google technical documentation](https://support.google.com/a/answer/7514107?hl=en).
To configure your Gmail server to use a Zscaler smart host:
- [1. Retrieve the IP ranges for the Zscaler smart host.](#retrieve-ip-ranges)
- [2. Configure a host to forward outbound emails to the Zscaler smart host.](#configure-forward-host)
- [3. Configure routing to receive emails after scan.](#configure-receive-routing)
- [4. Configure a compliance rule to add headers for the Zscaler smart host.](#compliance-rule-outbound)
- [5. Configure a compliance rule to deliver email received from the Zscaler smart host.](#compliance-rule-inbound-deliver)
- [6. Configure a compliance rule to reject email received from the Zscaler smart host.](#compliance-rule-inbound-reject)
With these settings configured, and with a Zscaler [outbound email policy rule configured](/unified/configuring-outbound-email-policy-rules) to detect and block sensitive information, users who try to send an email containing sensitive or confidential information to an external domain receive a message from the Gmail server that their message was blocked.
[See image.](#blocked-message-gmail)
[]![Blocked Email Message from Gmail](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Gmail-Rejection-Notification.png)
[][][][][]
-
Go to [config.zscaler.com](http://config.zscaler.com).
The **Zscaler Config** page appears.
- Select your organization's Zscaler cloud from the **Cloud** drop-down menu at the top left of the page.
- In the left-side navigation, go to **Email DLP**. The **Email DLP** page lists all of the outbound connections that need to be configured for the Zscaler smart host to communicate with your Gmail server.
[See image.](#Zscaler-Email-DLP-Requirements-Page)
- Make note of all the IPs that are listed on this page because you need to add them when you configure your Gmail server to communicate with the Zscaler smart host.
[]![The Zscaler Config page for Outbound Email DLP](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-DLP-Zscaler-Config-Page.png)
[][]
- Sign in to the [Google Admin console](https://admin.google.com/).
- In the left-side navigation, go to **Apps > Google Workspace > Gmail**.
[See image.](#gmail-left-side-nav-01)
The **Gmail** overview page appears.
- Click **Hosts**.
The **Hosts** page appears.
- On the **Hosts** page, click **Add Route**.
[See image.](#hosts-outgoing-add-route)
The **Add mail route** window appears.
- In the **Add mail route** window:
-
Specify a name for the host, then specify the FQDN for your Zscaler smart host.
You can find the smart host FQDN on the [Edit Email Tenant page](/unified/editing-email-tenants#copied-values-for-exchange) in the Admin Portal.
- Select **Require mail to be transmitted via a secure (TLS) connection (Recommended)**.
- Click **Save**.
[See image.](#outbound-add-route-save)
[]![The Gmail menu option in the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-01.png)
[]![The Add Route option on the Google Admin Hosts page](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-Hosts-Add-Route.png)
[]![The Add Route window on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Outbound-Add-Route-Save.png)
[]
- Sign in to the [Google Admin console](https://admin.google.com/).
- In the left-side navigation, go to **Apps > Google Workspace > Gmail**.
[See image.](#gmail-left-side-nav-02)
The **Gmail** overview page appears.
- Click **Routing**.
The **Routing** page appears.
-
On the **Routing** page, in the **SMTP relay service** section, click **Add another rule**.
[See image.](#receive-add-another-rule)
If you have not previously configured rules, you must click **Configure** to add a rule.
The **Add setting** window appears.
- In the **Add setting** window:
- Specify a description for the rule.
- In the **Allowed senders** section, select **Only addresses in my domains** from the drop-down menu.
- In the **Authentication** section, select **Only accept mail from the specified IP addresses**.
- Click **Add**, enter an optional description and the IP range [that you retrieved earlier for the Zscaler smart host](#retrieve-ip-ranges-substep1), select **Enable**, then click **Save**.
- Repeat the previous step as needed.
- In the **Add setting** window, click **Save**.
[See image.](#inbound-add-route-save)
[]![The Gmail menu option in the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-02.png)
[]![The Add another rule option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-SMTP-Add-Another-Rule.png)
[]![The Add Setting Window on Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-SMTP-Add-Setting-Save-2.png)
[]Rules in Gmail are used to perform various actions based on the criteria you specify (e.g., adding custom headers or rejecting the emails that contain sensitive information). In this step, you add a header with information from your configured Zscaler smart host so that the Zscaler service can properly receive and process email content from your Gmail server.
To configure a compliance rule to add headers for the Zscaler smart host:
- Sign in to the [Google Admin console](https://admin.google.com/).
- In the left-side navigation, go to **Apps > Google Workspace > Gmail**.
[See image.](#gmail-left-side-nav-03)
The **Gmail** overview page appears.
- Click **Compliance**.
The **Compliance** page appears.
- On the **Compliance** page, in the **Content compliance** section, click **Add another rule**.
The **Add setting** window appears.
- In the **Add setting** window:
- Specify a description for the compliance rule.
- In the **Email message to affect** section, select **Outbound**.
-
In the **Add expressions that describe the content that you want to search for in each message** section:
- Select **If ALL of the following match the message** from the drop-down menu.
- Click **Add**.
The **Add setting** window appears.
-
In the **Add setting** window:
- Select **Metadata match** from the drop-down menu.
- In the **Attribute** section, select **Source IP** from the drop-down menu.
- In the **Match type** section, select **Source IP is not within the range** from the drop-down menu, then add the IP range [that you retrieved earlier for the Zscaler smart host](#retrieve-ip-ranges-substep2).
- Click **Save**.
[See image.](#source-ip-attribute)
You return to the first **Add setting** window.
- In the **Add setting** window, in the **If the above expressions match, do the following** section, select **Modify message** in the drop-down menu.
- In the **Headers** section, select **Add custom headers** then click **Add**.
[See image.](#outbound-compliance-add-custom-headers)
The **Add setting** window appears.
-
In the **Add setting** window:
- Enter `Zscaler-Tenantid` in the **Header key** field, then paste the **Key for Transport Rules** value from the Admin Portal in the **Header value** field. You [copied the **Key for Transport Rules** value](/unified/adding-email-tenants#copy-smart-host-fqdn) when you configured the email tenant in the Admin Portal. You can also find the value on the **Edit Email Tenant** page in the Admin Portal.
- Click **Save**.
[See image.](#outbound-add-fqdn)
You return to the first **Add setting** window.
- In the **Add setting window**, in the **Route** section, select **Change route** then select the host you created earlier from the drop-down menu.
- Click **Show options**, then, in the **Account types to affect** section, select all options (i.e., **Users**, **Groups**, and **Unrecognized/catch-all**).
- Click **Save**.
[See image.](#outbound-headers-full-window)
[]![The Gmail menu option in the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-03.png)
[]![The Source IP Attribute rule option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Source-IP-Attribute_2.png)
[]![The Add custom header option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Add-Headers-Setting.png)
[]![The Add custom header option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Add-Zscaler-TenantID-header_2.png)
[]![The Outbound Compliance Rule Options on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Smarthost-Headers-Full-Window-2.png)
[]To properly route email that was processed by the Zscaler smart host but not blocked by policy rules, you must configure a compliance rule so that your Gmail server can deliver those messages.
To configure compliance rules to deliver email received from the Zscaler smart host:
- Sign in to the [Google Admin console](https://admin.google.com/).
- In the left-side navigation, go to **Apps > Google Workspace > Gmail**.
[See image.](#gmail-left-side-nav-04)
The **Gmail** overview page appears.
- Click **Compliance**.
The **Compliance** page appears.
- On the **Compliance** page, in the **Content compliance** section, click **Add another rule**.
The **Add setting** window appears.
- In the **Add setting** window:
- Specify a description for the compliance rule.
- In the **Email message to affect** section, select **Outbound**.
-
In the **Add expressions that describe the content that you want to search for in each message** section:
- Select **If ALL of the following match the message** from the drop-down menu.
- Click **Add**.
The **Add setting** window appears.
-
In the **Add setting** window:
- Select **Metadata match** from the drop-down menu.
- In the **Attribute** section, select **Source IP** from the drop-down menu.
- In the **Match type** section, select **Source IP is within the range** from the drop-down menu, then add the the IP range [that you retrieved earlier for the Zscaler smart host](#retrieve-ip-ranges-substep3)
- Click **Save**.
[See image.](#inbound-source-ip-attribute)
You return to the first **Add setting** window.
- In the **Add setting** window, click **Add** again.
The **Add setting** window appears.
-
In the **Add setting** window:
- Select **Advanced content match** from the drop-down menu.
- In the **Location** section, select **Full headers** from the drop-down menu.
- In the **Match type** section, select **Contains text** from the drop-down menu, enter `X-Zscaler-Block: 0` in the **Content** field.
- Click **Save**.
[See image.](#inbound-advanced-content-match)
You return to the first **Add setting** window.
- In the **Add setting** window, in the **If the above expressions match, do the following** section, select **Modify the message** from the drop-down menu.
- In the **Headers** section, select **Add X-Gm-Original-To header**.
- Scroll down and click **Show options**, then, in the **Account types to affect** section, select all options (i.e., **Users**, **Groups**, and **Unrecognized/catch-all**).
- Click **Save**.
[See image.](#inbound-headers-full-window)
[]![The Gmail menu option in the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-04.png)
[]![The Source IP Attribute rule option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Source-IP-for-Smart-Host_2.png)
[]![The Add custom header option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Zscaler-Block-Header_2.png)
[]![The Inbound compliance rule options on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Full-Compliance-Rule-from-smarthost.png)
[]As a final setup step, you must configure a compliance rule so that your Gmail server rejects email that was processed by the Zscaler smart host and was blocked by policy rules. With this rule in place, all emails returned with a `X-Zscaler-Block` header value of `1` are rejected and are not delivered to the recipient. Instead, the sender receives a rejection message.
To configure compliance rules to reject blocked email received from the Zscaler smart host:
- Sign in to the [Google Admin console](https://admin.google.com/).
- In the left-side navigation, go to **Apps > Google Workspace > Gmail**.
[See image.](#gmail-left-side-nav-05)
The **Gmail** overview page appears.
- Click **Compliance**.
The **Compliance** page appears.
- On the **Compliance** page, in the **Content compliance** section, click **Add another rule**.
The **Add setting** window appears.
-
In the **Add setting** window:
- Specify a description for the compliance rule.
- In the **Email message to affect** section, select **Outbound**.
- In the **Add expressions that describe the content that you want to search for in each message** section:
- Select **If ALL of the following match the message** from the drop-down menu.
- Click **Add**.
The **Add setting** window appears.
-
In the **Add setting** window:
- Select **Metadata match** from the drop-down menu.
- In the **Attribute** section, select **Source IP** from the drop-down menu.
- In the **Match type** section, select **Source IP is within the range** from the drop-down menu, then add the the IP range [that you retrieved earlier for the Zscaler smart host](#retrieve-ip-ranges-substep4)
- Click **Save**.
[See image.](#inbound-source-ip-attribute-reject)
You return to the first **Add setting** window.
- In the **Add setting** window, click **Add** again.
The **Add setting** window appears.
-
In the **Add setting** window:
- Select **Advanced content match** from the drop-down menu.
- In the **Location** section, select **Full headers** from the drop-down menu.
- In the **Match type** section, select **Contains text** from the drop-down menu, enter `X-Zscaler-Block: 1` in the **Content** field.
- Click **Save**.
[See image.](#inbound-advanced-content-match-1)
You return to the first **Add setting** window.
- In the **Add setting** window, in the **If the above expressions match, do the following** section, select **Reject the message** from the drop-down menu.
- In the **Customize the rejection notice** field, enter a message to notify senders that their email contained sensitive information (i.e., `Sensitive or confidential information found.`).
- Click **Show options**, then, in the **Account types to affect** section, select all options (i.e., **Users**, **Groups**, and **Unrecognized/catch-all**).
- Click **Save**.
[See image.](#inbound-reject-headers-full-window)
[]![The Gmail Menu Option in Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Admin-Console-05.png)
[]![The Add custom header option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Zscaler-Block-Header-Reject_2.png)
[]![The Source IP Attribute rule option on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Source-IP-for-Smart-Host-Reject_2.png)
[]![The Inbound compliance rule options on the Google Admin console](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Google-Full-Rejection-Rule-from-smarthost.png)