# Enforcing Secure PAC URLs
Source: https://help.zscaler.com/zscaler-client-connector/enforcing-secure-pac-urls
PDF: https://help.zscaler.com/pdf/com/en/1532829.pdf

You can require administrators to use secure URLs when adding custom PAC URLs. When enabled, administrators can only enter URLs with the https:// prefix (not http://) in the Custom PAC URL field on an [app profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#pac-proxy) and a [forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector#forwarding-profile-action-zia). You can use this feature to protect traffic from malicious PAC files by enforcing secure PAC URLs.
If you have existing custom PAC URLs that use the http:// prefix, after enabling this option you’ll be required to update the PAC URLs the next time you edit the profile. Contact Zscaler Support to enable this feature.
If you use Zscaler Client Connector version 4.8 and later for Windows, this feature also prevents Zscaler Client Connector from falling back to the HTTP protocol if downloading the default PAC file via HTTPS fails.
To enforce secure PAC URLs:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, select **Client Connector Support**.
-
On the **User Privacy** tab, select **Enforce Secure PAC URLs**.
![Enforcing secure PAC URLs](/downloads/zscaler-client-connector/zscaler-client-connector-support-settings/user-privacy/enforcing-secure-pac-urls/zclient-connector-enforce-secure-pac-urls.png)
- Click **Save**.