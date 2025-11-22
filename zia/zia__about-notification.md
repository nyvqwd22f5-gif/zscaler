# About Notification
Source: https://help.zscaler.com/zia/about-notification
PDF: https://help.zscaler.com/pdf/com/en/1402286.pdf

The Notification pane displays warnings and any other notifications to keep your ZIA Gateway up to date.
[See Image](#zianotifications)
[]![About ZIA Notifications](/downloads/zia/getting-started/admin-portal/about-notification/ZIA-error-notification-page-DNS-setup1.png)
The following are the most common notifications that you may view on the Admin Portal.
[](/zia/about-partner-integrations#MCAS)
[](/zia/about-dns-control)
[](/zia/about-provisioning-authenticating-users)
[](/zia/about-exact-data-match)
[](/zdx/using-zdx-setup-wizard)
| Notification | Resolution |
| ------------ | ---------- |
| MCAS
MCAS integration sync failed. | If the integration sync fails the first time, enter a new token value and click the **Test** button. The **Test** button is enabled only if you enter a new token value. The integration sync error message disappears as soon as your token is successfully accepted. To learn more, see About Partner Integrations. |
| DNS Control
It is recommended to move the predefined DNS rules for ZPA to either order 1 or 2. | Change the predefined ZPA rules 3 and 4 to 1 and 2 respectively. To learn more, see About DNS Control. |
| Your SP SSL certificate is going to expire in 7 day(s). | Change the default IdP setting to use a valid certificate or the admin should get a new IdP certificate with a future expiry date and replace the configuration with it. To learn more, see About Provisioning and Authenticating Users. |
| SaaS Application Tenants
Reauthorization Required (Errors 3) | Edit the Saas Application tenant from **Administration** >** ****SaaS Application Tenants **and click **Reauthorize**. |
| Exact Data Match (EDM)
EDM Indexing Failed Schemas | Update the EDM index failure schema with a new CSV file which adds no further duplicates. You can also either remove or update the working schemas to decrease the duplicate count to less than 2048 per primary key. To learn more, see About Exact Data Match. |
| Configure Zscaler Digital Experience | Admins with ZDX Standard subscription and full permissions to the Policy Access, Administration Access, and Organizational Scope are notified with a link to access the ZDX setup wizard if the ZDX service is not already configured. To learn more, see Using ZDX Setup Wizard. |