# Adding Email Tenants
Source: https://help.zscaler.com/unified/adding-email-tenants
PDF: https://help.zscaler.com/pdf/com/en/1503666.pdf

Email tenants allow you to use the Zscaler service as a smart host for inspecting email content sent to external domains as part of your outbound email policy rules. The email tenants you create are used as part of the mail flow rules that you configure on your email server to act on content that violates your outbound email policy rules. To learn more, see [Configuring Microsoft Exchange for Zscaler Outbound Email DLP](/unified/configuring-microsoft-exchange-zscaler-outbound-email-dlp) and [Configuring Gmail for Zscaler Outbound Email DLP](/unified/configuring-gmail-zscaler-outbound-email-dlp).
To add an email tenant:
- In the Admin Portal, go to **Policies > Data Protection > Policy > Email Tenants**.
- Click **Add Email Tenant**.
The **Add Email Tenant **window appears.
- Under **Choose the Email Service Provider**, select **Gmail** or **Exchange**.
[See image.](#select-service-provider)
- Under **Name Email Tenant**, enter a unique name for the tenant.
- Under **Email Tenant Security Options**, the setting for **Outbound Email Security **is automatically selected and is not configurable.
[See image.](#name-security-options)
- Under **Configure Connectors and Rules**, click **Get Configuration Info**.
The **Key for Transport Rules** information appears.
[See image.](#connectors-and-rules)
- []Copy the values for **Smart Host FQDN** and for **Key for Transport Rules** and save them for later configuration on the email server.
- Under **Email Domain Configuration **specify the information for the email domain next hop, which is where the Zscaler service sends email content after inspection:
- **Domain**: Select a domain from the list. The domains in the list are listed in your [company profile](/unified/configuring-company-profile).
- **Next Hop Address**: Enter the address of the relay host for the email domain of the tenant you're configuring. For Gmail domains, enter `smtp-relay.gmail.com`. For Microsoft domains, use the following instructions to locate the relay host address:
- [Locate the relay host address for your Microsoft domain](#next-hop-m365)
- **Port Number**: Enter the port number for the email domain (i.e., `25`).
- Click **Add Domain**.
The domain information is added to the email tenant
[See image.](#domain-next-hop)
- Click **Save** and activate the change.
[]
- Sign in to the [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home#/homepage).
- In the left-side navigation, go to **Settings > Domains**.
[See image.](#settings-domains)
The **Domains** page appears.
- In the list of domains, click the name of the email domain you're using to configure your outbound email policy.
The **Overview** page for the domain appears.
[See image.](#domain-overview-page)
- On the **Overview** page, click **DNS Records**.
The **DNS Records** page appears.
- On the **DNS Records** page, click the name of the mail exchange (MX) record for the domain.
The **MX record** page appears.
- On the **MX record** page, in the **Expected record** row, copy the value from the **Points to address or Value** column.
[See image.](#mx-record-copy-value)
- In the Admin Portal, paste the copied value into the **Next Hop Address** field.
[]![The Domains menu option in the Microsoft M365 Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Next-Hop-M365-Admin-Settings-Domain.png)
[]![The Domain Overview page in the Microsoft M365 Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Next-Hop-M365-Domain-Overview.png)
[]![A screenshot of the copy MX record value in the Microsoft M365 Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Next-Hop-M365-MX-Value.png)
[]![The Zscaler Add Email Tenant window highlighting the Email Tenant service provider selection](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Tenant-Service-Provider.png)
[]![The Email Tenant Name and Security Options](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Tenant-Name-Security-Options.png)
[]![The Add Email Tenant window highlighting the Email Tenant Connectors and Rules Configuration](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Tenant-Config-Connectors-and-Rules.png)
[]![The Add Email Tenant window with Email Tenant Domain Configuration](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Tenant-Domain-Next-Hop-25.png)