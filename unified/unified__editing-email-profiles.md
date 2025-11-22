# Editing Email Profiles
Source: https://help.zscaler.com/unified/editing-email-profiles
PDF: https://help.zscaler.com/pdf/com/en/1503691.pdf

Zscaler's email profiles allow you to make custom sets of email domains and recipient profiles that you can easily use with Data Loss Prevention (DLP) tools across channels. To learn more, see [About Data Loss Prevention](/unified/about-data-loss-prevention), [About SaaS Security API DLP](/unified/about-saas-security-api-dlp), and [About Outbound Email Policy](/unified/about-outbound-email-policy).
To edit email profiles:
-
Go to **Policies** > **Data Protection** > **Common Resources** > **Email Domain Profiles**.
The **Email Profiles **page appears.
- On the **Email Profiles** page:
- [Edit a domain profile](#add-domain-profile)
- [Edit a recipient profile](#add-recipient-profile)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]
- Click **Domain Profiles**.
-
Find a domain profile in the list, then click **Edit**.
The **Edit Domain Profile **window appears.
-
In the **Edit Domain Profile** window:
- **Profile Name**: Enter a name for the domain profile.
- **Top Personal Email Service Providers**: Select from a list of email service providers to include and click **Done**.
- **Include Organizational Domains**: Selecting this option automatically includes the domains listed on your Company Profile. To learn more, see [Configuring the Company Profile](/unified/configuring-company-profile).
- **Custom Domains**: Enter one or more domain names separated by line breaks, then click **Add Items**.
- **Include Subdomains**: Select whether to automatically include subdomains in the domain profile (e.g., `blog.example.com` is a subdomain of `example.com`).
- **Description**: Enter additional notes or information. The description cannot exceed 256 characters.
[See image.](#domain-profiles-screenshot)
[]![The Edit Domain Profile window in the Zscaler Admin Portal.](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Profiles-Edit-Domain-Profile-with-subdomains.png)
[]
- Click **Recipient Profiles**.
-
Find a recipient profile in the list, then click **Edit**.
The **Edit Recipient Profile **window appears.
-
In the **Edit Recipient Profile** window:
- **Profile Name**: Enter a name for the recipient profile.
- **Recipients**: Enter one or more recipient email addresses separated by line breaks, then click **Add Items**.
- **Description**: Enter additional notes or information. The description cannot exceed 256 characters.
[See image.](#recipient-profiles-screenshot)
[]![The Edit Recipient Profile window in the Zscaler Admin Portal.](/downloads/zia/policies/outbound-email-policy/ZIA-Email-Profiles-Edit-Recipient-Profile.png)