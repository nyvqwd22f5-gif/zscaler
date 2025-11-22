# Adding Guest Domains
Source: https://help.zscaler.com/zidentity/adding-guest-domains
PDF: https://help.zscaler.com/pdf/com/en/1499281.pdf

You can add a list of guest domains to allow third-party users (guest users) to access the Zscaler service. Arbitrary guest domains allow you to enable guest users to access the Zscaler service from any domain. You can add users as guests and assign them with specific permissions to access these guest domains.
You can assign guest domains to only those guest users who do not have Zscaler Client Connector for authentication. These guest users cannot be assigned administrative entitlements.
To add a guest domain:
- Go to **Administration** > **Domains**.
- Enter the domain name in the **Guest Domain** field, then click **Add**.
-
Enable **Arbitrary Guest Domains**, if required. Enabling this option allows third-party users to authenticate using any domain even if it is not added to the list of guest domains.
Arbitrary Guest Domains are supported only with [Privileged Remote Access](/zpa/understanding-privileged-remote-access).
- Click **Save**.
[See image.](#zsl-guestdomain)
- After you add the guest domains:
- Add the third-party users to the ZIdentity Admin Portal. To learn more, see [Adding Users](/zidentity/adding-users).
- [Add these guest domains to the required identity provider (IdP)](/zidentity/adding-saml-identity-providers), so the third-party users can authenticate using single sign-on (SSO) and access the guest domains.
[]![Domains page displaying the list of available domains. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-adding-guest-domains-doc-58313/Guest-domain1.png)