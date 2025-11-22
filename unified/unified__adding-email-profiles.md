# Adding Email Profiles
Source: https://help.zscaler.com/unified/adding-email-profiles
PDF: https://help.zscaler.com/pdf/com/en/1503686.pdf

Zscaler's email profiles allow you to make custom sets of email domains and recipient profiles that you can easily use with Data Loss Prevention (DLP) tools across channels. To learn more, see [About Data Loss Prevention](/unified/about-data-loss-prevention), [About SaaS Security API DLP](/unified/about-saas-security-api-dlp), and [About Outbound Email Policy](/unified/about-outbound-email-policy).
To add email profiles:
-
Go to **Policies **>** Data Protection **>** Common Resources **>** Email Domain Profiles**.
The **Email Profiles **page appears.
- On the **Email Profiles** page:
- [Add a domain profile](#add-domain-profile)
- [Add a recipient profile](#add-recipient-profile)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]
- Click **Domain Profiles**.
-
Click **Add Domain Profile**.
The **Add Domain Profile **window appears.
-
In the **Add Domain Profile** window:
- **Profile Name**: Enter a name for the domain profile.
- **Top Personal Email Service Providers**: Select from a list of email service providers to include and click **Done**.
- **Include Organizational Domains**: Selecting this option automatically includes the domains listed on your Company Profile. To learn more, see [About the Company Profile](/unified/configuring-company-profile).
- **Custom Domains**: Enter one or more domain names separated by line breaks, then click **Add Items**.
- **Include Subdomains**: Select whether to automatically include subdomains in the domain profile (e.g., `blog.example.com` is a subdomain of `example.com`).
- **Description**: Enter additional notes or information. The description cannot exceed 256 characters.
[See image.](#domain-profiles-screenshot)
[]![The Add Domain Profile window in the Zscaler Admin Portal.](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Profiles-Add-Domain-Profile-with-subdomains.png)
[]
- Click **Recipient Profiles**.
-
Click **Add Recipient Profile**.
The **Add Recipient Profile **window appears.
-
In the **Add Recipient Profile** window:
- **Profile Name**: Enter a name for the recipient profile.
- **Recipients**: Enter one or more recipient email addresses separated by line breaks, then click **Add Items**.
- **Description**: Enter additional notes or information. The description cannot exceed 256 characters.
[See image.](#recipient-profiles-screenshot)
[]![The Add Recipient Profile window in the Zscaler Admin Portal.](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Profiles-Add-Recipient-Profile.png)