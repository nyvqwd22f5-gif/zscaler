# About IdP Configuration
Source: https://help.zscaler.com/zpa/about-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1483631.pdf

[Watch a video about IdP configuration.](https://fast.wistia.net/embed/iframe/h1pzwui70g)
For users to access your applications via ZPA, they must first authenticate into Zscaler Client Connector using any SAML 2.0-compliant identity provider (IdP) with the service provider-initiated (SP initiated) model. ZPA user SSO is SP initiated, but ZPA admin SSO can be SP initiated or IdP initiated. When a ZPA admin selects **Single Sign-On Using IdP** on the [ZPA Admin Portal's Sign In page](/zpa/accessing-and-navigating-zpa-admin-portal#LoggingIn), the login is SP initiated. If the ZPA admin logs directly into their IdP, it's IdP initiated.
Prior to configuring your IdP, Zscaler recommends reading [IdP Configuration Best Practices](/zpa/idp-configuration-best-practices).
The IdP must be configured to recognize Zscaler as a valid SP, and you must configure the full details for the IdP within the ZPA Admin Portal. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
IdP configuration provides the following benefits and enables you to:
- Authenticate and access applications via ZPA.
- Use SCIM, a standard protocol for automating the exchange of identity information, so that you can provision users and groups.
About the IdP Configuration Page
The IdP Configuration page is read only if you are subscribed to ZIdentity for users. An orange **Info** icon ![Orange Info Icon within the ZPA Admin Portal](/downloads/zpa/authentication/idp-configuration/about-idp-configuration/zpa-orange-info-icon.png)
is displayed next to disabled IdPs that have been migrated to ZIdentity. These IdPs will be deleted 30 days after migration. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
On the IdP Configuration page (Authentication > User Authentication > IdP Configuration), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the IdP Configuration page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
[Add a new IdP configuration.](/zpa/configuring-idp-single-sign)
The **Add **button is hidden if you are subscribed to ZIdentity for users. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
- View a list of the names of all IdPs that were configured for your organization. For each IdP configuration, you can see:
-
**Name**: The name of the IdP configuration. An icon shows next to the name of the IdP if the IdP certificate is close to expiring or has expired:
- If the IdP certificate has expired, a red **Warning** icon (![Red warning icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-red-warning-icon.png)
) is displayed.
- If the IdP certificate has less than 7 days before expiration, a yellow **Caution** icon (![Yellow caution icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-yellow-caution-icon.png)
) is displayed.
- If the IdP certificate has less than 30 days before expiration, an orange **Info** icon (![Orange info icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idp-configuration/zpa-orange-info-icon.png)
) is displayed.
If the IdP certificate is part of a certificate chain instead of a single certificate, the certificate expiring the earliest is considered to reflect the expiration icons.
- **Status**: The status of the IdP configuration (i.e., enabled, disabled, or resume if the configuration was [paused during set up](/zpa/configuring-idp-single-sign#Pause)).
- **IdP Entity ID**: The entity ID URL for the IdP.
- **Single Sign-On**: Indicates whether the IdP is set up for **Admin** or **User** SSO.
If the IdP configuration was set up prior to the [Multiple Identity Provider Support for Single Sign-On release](/zpa/release-upgrade-summary-2019?applicable_category=private.zscaler.com&deployment_date=2019-05-23) and was configured to use **Both **(i.e., admin and user SSO), it still functions as before. However, it is listed in the table with **Admin, User** displayed for this column.
[See image.](#LegacyIdPConfig_Both)
You can expand the row to view details regarding the configuration, [import SAML attributes](/zpa/about-saml-attributes), or [verify that SSO](/zpa/configuring-idp-single-sign) was configured correctly for the IdP.
-
[Edit an existing IdP configuration.](/zpa/editing-idp-configuration)
IdP configurations that are managed by Zscaler are read only and cannot be edited.
- Delete an IdP configuration.
An IdP cannot be deleted if it is used for [emergency access](/zpa/configuring-emergency-access) or managed by Zscaler. When an IdP gets deleted, all [user risk scores](/zpa/about-user-risk-scores) associated with users of that IdP are also deleted.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [SAML Attributes](/zpa/about-saml-attributes) page to import attributes or add them manually. If you expand the row to view details for an IdP configuration set up for **User **SSO, you can click **Show Attributes** to see a filtered view of the **SAML Attributes** page for that IdP.
- Go to the [Settings](/zpa/configuring-authentication-settings) page to modify authentication settings (e.g., enabling Remote Assistance).
- Go to the [Emergency Access](/zpa/configuring-emergency-access) page to configure emergency access for third-party users.
- Go to the [Emergency Access Users](/zpa/about-emergency-access-users) page to view and manage users designated for emergency access.
![Viewing and Managing IdP Configurations ](/downloads/zpa/authentication/idp-configuration/about-idp-configuration/zpa-idp-configuration-page-react.png)
[]![IdP Configuration page within the ZPA Admin Portal ](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/about-idps/zpa-both-legacy-idpconfig.png)