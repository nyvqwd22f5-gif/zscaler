# Adding Guest Domains
Source: https://help.zscaler.com/unified/adding-guest-domains
PDF: https://help.zscaler.com/pdf/com/en/1505631.pdf

You can add a list of guest domains to allow third-party users (guest users) to access the Zscaler service. Arbitrary guest domains allow you to enable guest users to access the Zscaler service from any domain. You can add users as guests and assign them with specific permissions to access these guest domains.
You can assign guest domains to only those guest users who do not have Zscaler Client Connector for authentication. These guest users cannot be assigned administrative entitlements.
To add a guest domain:
- Go to **Administration** >** Identity** > **ZIdentity **> **Domains**.
- Enter the domain name in the **Guest Domain** field, then click **Add**.
- Enable **Arbitrary Guest Domains**, if required. Enabling this option allows third-party users to authenticate using any domain even if it is not added to the list of guest domains.
-
Click **Save**.
[See image.](#zsl-guestdomain)
- After you add the guest domains:
- Add the third-party users to the Admin Portal. To learn more, see [Adding Users](/unified/adding-users-0).
- [Add these guest domains to the required identity provider (IdP)](/unified/adding-saml-identity-providers), so the third-party users can authenticate using single sign-on (SSO) and access the guest domains.
[]![Add the guest domains for guest users](/downloads/unified/administration/zidentity/ec-guestdomains.png)