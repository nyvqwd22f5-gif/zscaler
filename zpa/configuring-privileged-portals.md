# Configuring Privileged Portals
Source: https://help.zscaler.com/zpa/configuring-privileged-portals
PDF: https://help.zscaler.com/pdf/com/en/1485116.pdf

After you have added an application segment with Privileged Remote Access, you can go to the Privileged Portals page. You can have up to 100 privileged portals. For a complete list of ranges and limits, see [Ranges & Limitations](/zpa/ranges-limitations).
To add a privileged portal:
- Go to **Resource Management **>** Privileged Remote Access > Privileged Portals**.
- Click **Add Portal**.
The **Add Portal** window appears.
- In the **Add Portal** window:
- **Name**: Enter a name for the privileged portal. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Enable the privileged portal. If disabled, the privileged portal is inaccessible to end users.
- **Certificate Type**: Select either **Managed **or **Custom**. Use an existing certificate by selecting the **Custom** certificate type. Select the **Managed** certificate type to reduce the need to create and renew custom certificates.
- If you select **Managed**, the portal certificate is managed by Zscaler.
- [See instructions.](#Managed)
- If you select **Custom**, then you select an existing certificate.
- [See instructions.](#Custom)
- **Description**: (Optional) Enter a description for the privileged portal.
- **User Portal for Portal Links**: Select a portal link if you want to access the related user portal Browser Access applications in the PRA Portal. The Browser Access applications are found on the My Web Applications tab in the PRA Portal.
- **Approval Reviewers**: Select or enter email addresses of administrators that you want to set up email notifications for when a privileged approval request has been created, approved, and rejected. To use this feature, you must have a privileged portal policy with **Review Approvals** enabled. To learn more, see [Configuring Portals Policies](/zpa/configuring-portals-policies).
- If you want to display a notification to your users at the top of the PRA portal page, under **Notification Banner**:
- **Status**: Enable the notification banner.
- **Message Text**: Enter the notification text that you want displayed in the PRA portal's banner.
![Update configuration for the privileged portal](/downloads/zpa/privileged-remote-access-management/privileged-portals/configuring-privileged-portals/Add%20Portal%20window.png)
- Click **Save**.
For privileged portals with a custom certificate, complete the following steps:
- On the **Privileged Portals** page, expand the row to view the privileged portal details within the table, then click the **Copy** icon next to the **Canonical Name (CNAME)**. You need this CNAME record for your public DNS.
![Privileged Portals page within ZPA Admin Portal](/downloads/zpa/privileged-remote-access-management/configuring-privileged-portals/UPDATED%20CNAME.png)
- Add the CNAME information you copied to your public DNS, and verify that the FQDN for the privileged portal resolves to the record.
For example, for a CNAME of:
la-portal.com. CNAME 72057594038060561.72057594037927936.pra.p.zpa-app.net
Verify that `la-portal.com` resolves to `72057594038060561.72057594037927936.pra.p.zpa-app.net`.
Zscaler automatically manages the public DNS for the FQDN of user portals with a Zscaler-managed certificate.
- []Enter the domain prefix.
- Select the domain suffix from the drop-down menu.
- Click the **Copy **icon to copy the URL.
[See image.](#manageimage)
- []Enter the full URL for the privileged portal. This is the URL that users access to view the portal. The URL must use the HTTPS protocol and be a fully qualified domain name (FQDN).
A privileged portal's FQDN cannot be configured as an application within an application segment.
- Select a certificate from the **Portal Server Certificate** drop-down menu that is associated with the privileged portal. To learn more, see [About (Web Server) Certificates](/zpa/about-BrowserAccessCertificates).
The certificate must support the FQDN specified for the privileged portal.
[See image.](#customimage)
[]![Selecting the Managed certificate type within the Add Privileged Portal window](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-privileged-portals-doc-53920/Managed%20privileged.png)
[]![Selecting the Custom certificate type within the Add Privileged Portal window](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-privileged-portals-doc-53920/Custom%20privileged.png)