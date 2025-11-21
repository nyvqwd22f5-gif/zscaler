# Configuring AI-Powered Recommendations Settings
Source: https://help.zscaler.com/zpa/configuring-ai-powered-recommendations-settings
PDF: https://help.zscaler.com/pdf/com/en/1485176.pdf

You can control what kinds of recommendations you see on the AI-Powered Recommendations page from the Settings drawer. Enter wildcards, subnets, and defined application segments that you don’t want to include to stop receiving recommendations related to those specific configurations. You can also select the System for Cross-domain Identity Management (SCIM) or Security Assertion Markup Language (SAML) attribute to display for recommended users on the AI-Powered Recommendations page. You can exclude specific FQDNs or IP address ranges from application segment recommendations, or remove specific application segments even if they are defined as wildcards from application segment recommendations.
To configure settings for the AI-Powered Recommendations page:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **AI-Powered Recommendations** > **Settings**.
-
In the **Settings** drawer:
- **Exclude**: Select or enter the items you want to exclude.
- **Wildcards/Subnets**: Enter wildcards or subnets that you want to exclude from recommendations.
- **Defined Application Segments**: Select a defined application segment from the drop-down menu that you want to exclude.
-
**Define Criteria for Recommendations**: From the **Criteria** drop-down menu, select one of the following options to generate recommended users:
- **SCIM Group**: Recommended users are based on the SCIM groups associated with the user.
- **SCIM Attribute**: Recommended users are displayed based on the selected SCIM attribute.
- **SAML Attribute**: Recommended users are are displayed based on the selected SAML attribute (e.g., **Department**).
You must enable [SCIM Sync](/zpa/enabling-scim-identity-management) to display SCIM criteria (i.e., **SCIM Attribute** or **SCIM Group**).
[See image.](#img_settings)
- Click **Save**.
[]
![Customize your AI-Powered recommendations](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-ai-powered-recommendations-settings/ZPA-AI-Powered-Recommendations-Settings-0.png)