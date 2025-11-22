# Configuring Restricted Access for Admins
Source: https://help.zscaler.com/zia/configuring-restricted-access-admins
PDF: https://help.zscaler.com/pdf/com/en/1402211.pdf

To enable this feature, contact your Zscaler Account team.
You can enable access restrictions for the admins logging in to the ZIA Admin Portal based on their source IP address. By default, this option is disabled.
To configure restricted access for admins:
- Go to** Administration** > **Administrator Management**.
- Click the** Administrator Management** tab.
- In the **Restricted Access** section:
-
**Enable Restricted Access to Admin Portal**: Enable this option to enforce access restrictions to the ZIA Admin Portal based on the source IP address of the admin. Only those admins whose source IP addresses are included in the **Allowlist IP Addresses and Ranges** list can access the ZIA Admin Portal. You can optionally exempt the restriction for admin logins that are either SAML-based or routed through a known Zscaler Proxy.
-
**Allow Logins via Zscaler Proxy**: Enable this option to automatically allow ZIA Admin Portal access to all authenticated admin logins routed from a known Zscaler proxy. However, there is no automatic access permission for traffic routed through a Zscaler Private Service Edge (formerly Private ZEN or PZEN) unless the source IP address of the Private Service Edge is included in the **Allowlist IP Addresses and Ranges** list. If this option is disabled, you can include the IP address of the Zscaler Public Service Edge in the **Allowlist IP Addresses and Ranges** list to provide access to the admins that route traffic through the Public Service Edge.
This setting only applies to traffic originating from the same cloud as your ZIA tenant.
- **Allow SAML Based Logins**: Enable this option to automatically allow ZIA Admin Portal access to all SAML-authenticated admin logins, if SAML authentication is enabled. If this option is disabled, the SAML-authenticated admins have access only if their source IP addresses from the SAML assertion are included in the **Allowlist IP Addresses and Ranges** list.
- **Allowlist IP Addresses and Ranges**: Specify a list of source IP addresses or ranges from which admins can access the ZIA Admin Portal when restricted access is enabled. You can add up to 512 entries.
[See image.](#restricted-access)
-
Click **Save**.
Upon saving the changes, the previously authenticated admins whose source IP addresses are not placed on the allowlist are able to continue their sessions until they log out or their session expires.
Ensure that your source IP address is placed on the allowlist while enabling this feature before saving.
![Screenshot of the Restricted Access section in the Administration Management page](/downloads/zia/authentication-administration/administrator-role-management/configuring-restricted-access-admins/zia-configuring-restricted-access-admins-image.png)
[]