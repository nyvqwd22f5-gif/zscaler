# Configuring AI-Powered Recommendations Settings
Source: https://help.zscaler.com/unified/configuring-ai-powered-recommendations-settings
PDF: https://help.zscaler.com/pdf/com/en/1520241.pdf

You can control what kinds of recommendations you see on the AI-Powered Recommendations page from the Settings drawer. Enter wildcards, subnets, and defined application segments that you don’t want to include to stop receiving recommendations related to those specific configurations. You can also select the SCIM attribute to display for recommended users on the AI-Powered Recommendations page. You can exclude specific FQDNs or IP address ranges from application segment recommendations, or remove specific application segments even if they are defined as wildcards from application segment recommendations.
To configure settings for the AI-Powered Recommendations page:
- Go to **Policies **> **Access Control **> **Private Applications** > **App Segments** > **AI-Powered Recommendations** > **Settings**.
-
In the **Settings** drawer:
- **Exclude**: Select or enter the items you want to exclude.
- **Wildcards/Subnets**: Enter wildcards or subnets that you want to exclude from recommendations.
- **Defined Application Segments**: Select a defined application segment from the drop-down menu that you want to exclude.
- **Define Criteria for Recommendations**: From the **Criteria** drop-down menu, select the SCIM attribute (**SCIM Group** or **SCIM Department**) to display for recommended users.
[See image.](#img_settings)
- Click **Save**.
[]
![Application segments setting page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-segments-settings/ZPA-AI-Powered-Recommendations-Settings-1_smaller.png)