# Editing an IdP Configuration
Source: https://help.zscaler.com/zpa/editing-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1483636.pdf

To edit your IdP configuration:
- Go to **Authentication **>** User Authentication **>** IdP Configuration**.
-
Locate the IdP configuration you want to modify within the table, and click the **Edit** icon.
IdP configurations that are managed by Zscaler are read only and cannot be edited.
The **Edit IdP Configuration **window appears.
- In the **Edit IdP Configuration** window, modify fields as necessary. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO).
If the IdP configuration was set up prior to the [Multiple Identity Provider Support for Single Sign-On release](/zpa/release-upgrade-summary-2019?deployment_date=2019-05-23) and was configured to use **Both** (i.e., admin and user SSO), this is selected under **Single Sign-On**. However if you want to make any modifications, you need to add a new IdP configuration within the ZPA Admin Portal.
If the IdP configuration was set up after the Multiple Identity Provider Support for Single Sign-On release, then this field does not appear.
If you are editing the IdP to change the **Status** from **Enabled** to **Disabled**, this change applies to SAML authentication and arbitrary domains if you are using clientless access ([Privileged Remote Access](/zpa/about-privileged-portals), [Browser Access](/zpa/about-browser-access), and [Cloud Browser Isolation](/zpa/about-isolation-policy)).
Single Sign-On needs to be set to **User** for **Use with Arbitrary Domains** to appear as an option in the **Edit IdP Configuration window**. Once you’ve enabled arbitrary domains with an IdP, it no longer appears as an option for additional IdP configurations, unless you disable or delete the existing arbitrary domain-enabled IdP.
To disable SCIM for identity management, you must select **Disabled** for **SCIM Sync**. To learn more, see [Enabling SCIM for Identity Management](/zpa/enabling-scim-identity-management).
If you are editing the IdP in order to change the service provider certificate, you might also need to update the configuration of the IdP. To learn more, see [Managing a Service Provider Certificate Rotation](/zpa/managing-service-provider-certificate-rotation).
[See image.](#edit-idp-window)
[]![Edit IdP Configuration window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/editing-idp-configuration/zpa-edit-idp-configuration-window.png)
- Click **Save**.