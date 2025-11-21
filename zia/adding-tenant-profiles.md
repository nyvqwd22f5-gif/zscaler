# Adding Tenant Profiles
Source: https://help.zscaler.com/zia/adding-tenant-profiles
PDF: https://help.zscaler.com/pdf/com/en/1401746.pdf

Zscaler's tenancy restriction feature allows you to restrict access either to personal accounts, business accounts, or both for certain cloud applications. The feature consists of two parts: creating [tenant profiles](/zia/about-tenant-profiles) and associating the profiles with the [Cloud App Control policy rules](/zia/adding-rules-cloud-app-control-policy).
To add a tenant profile:
- Go to **Administration** > **Tenant Profiles**.
-
Click **Add Tenant Profile**.
The **Add Tenant Profile** page appears.
-
In the **Cloud Application** field, select one of the following applications and configure it accordingly:
- [YouTube](#youtube)
- [Google Apps](#google)
- [Microsoft Login Services](#microsoft-login-services)
- [Slack](#slack)
- [Amazon Web Services](#AWS)
- [Dropbox](#dropbox)
- [Webex Login Services](#webex-login-services)
- [Zoho Login Services](#zoho-login-services)
- [Google Cloud Platform](#google-cloud-platform)
- [Zoom](#tr-zoom)
- [IBM SmartCloud](#tr-ibm-smart-cloud)
- [GitHub](#tr-github)
- [ChatGPT](#tr-chatgpt)
Ensure to select these cloud applications as a criterion in an SSL Inspection rule if their tenant profiles are associated with a cloud application rule.
In the SSL Inspection rule, for the following cloud applications, do as follows:
- **Office 365**:** **Select **Microsoft Login Services** as the cloud application with a rule order higher than Office 365 One Click Rule.
- **Google Apps**:** **Select **Google Login Services** as the cloud application.
- **Webex Teams/Webex Meetings**: Select **Webex Login Services** as the cloud application.
[See image.](#applications-image)
-
In the **Tenant Profile Name** field, enter a unique name for the tenant profile.
This name is displayed while configuring the respective Cloud App Control policy rules.
- **Description**: (Optional) Enter any additional comments or information. The description cannot exceed 10,240 characters.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]To configure the tenant profile for YouTube, in the **YouTube Configuration** field, select one of the following configuration types:
- [YouTube Category ID](#youtube-category-id)
- [YouTube Channel ID](#youtube-channel-id)
- [YouTube School ID](#youtube-school-id)
To learn more about associating tenant profiles of YouTube with the Cloud App Control policy rule, see [Adding a Streaming Media Rule for Cloud App Control](/zia/adding-streaming-media-rule-cloud-app-control).
[]In the **YouTube Category ID** field, select the required categories from the following list of categories:
- Action/Adventure
- Anime/Animation
- Autos & Vehicles
- Classics
- Comedy
- Documentary
- Drama
- Education
- Entertainment
- Family
- Film & Animation
- Foreign
- Gaming
- Horror
- Howto & Style
- Movies
- Music
- News & Politics
- Nonprofits & Activism
- People & Blogs
- Pets & Animals
- Science & Technology
- Sci-fi/Fantasy
- Shorts
- Short Movies
- Shows
- Sports
- Thriller
- Trailers
- Travel & Events
- Videoblogging
You can select any number of YouTube category IDs and also search for YouTube category IDs.
[]In the **YouTube Channel ID** field, enter the YouTube channel IDs (e.g., UCSylwuqCXM_W13ARfzASm3Q) you want to add to this tenant profile, and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 200 YouTube channel IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[]In the **YouTube School ID** field, enter the IDs YouTube assigned to your school network (e.g., UC1xagwHTcYzlpIriGARvPig), which you want to add to this tenant profile, and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 YouTube school IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[]To configure the tenant profile for Google apps:
-
In the **Domains** field, enter the domains (e.g., www.zscaler.com) you want to add to this tenant profile and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 domains. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- For the **Allow Consumer Access** field, select **Yes** to allow consumer access to the domains in the tenant profile. This field is set to **No** by default.
- For the **Allow Visitor Access** field, select **Yes** to allow visitors access to the domains in the tenant profile. This field is set to **No** by default.
The service intercepts any google.com (or associated Google app) request and adds the HTTP header X-GoogApps-Allowed-Domains (values of the **Domains** field), which identifies the domains from which users can access Google services. This prevents users from accessing Gmail and other Google apps from other domains.
This feature does not affect Google apps that do not require users to sign in, such as Google search. But a user who signs in from Google search with an account that is not placed on the allowlist is blocked.
For additional information from Google, see [here](https://support.google.com/a/answer/1668854?hl=en-uk&hlrm=en) and [here](http://support.google.com/a/answer/9230591?hl=en-IE).
To learn more about associating tenant profiles of Google apps with the Cloud App Control policy rule, see [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
[]You can configure the following tenant profile types for Microsoft Login Services:
- [Version 1](#mst-login-services-v1)
- [Version 2](#mst-login-services-v2)
The version of the tenant profiles can be changed only when the profiles are not associated with any policy.
The following headers are inserted only for each incoming request to login.microsoftonline.com, login.microsoft.com, login.windows.net, and login.live.com:
- Restrict-Access-Context (value of the **Tenant Directory ID **field)
- Restrict-Access-To-Tenants (values of the **Office 365 Tenants or Tenant IDs **field)
- sec-Restrict-Tenant-Access-Policy (value of the **Tenant Directory ID:Policy ID** field)
To learn more about Microsoft Tenant Restrictions, refer to the [Microsoft Tenant Restriction documentation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/tenant-restriction-v2-is-now-public-preview/ba-p/3094113#:~:text=Tenant%20restrictions%20V2%20let%20an,accounts%20created%20in%20unknown%20tenants) and [Microsoft documentation](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/tenant-restrictions).
To learn more about associating tenant profiles of Microsoft Login Services with the Cloud App Control policy rule, see [Adding an IT Services Rule for Cloud App Control](/zia/adding-it-services-rule-cloud-app-control).
[]To configure Version 1 tenant profile for Microsoft Login Services:
- In the **Tenant Directory ID** field, enter the tenant directory ID (e.g., f4c77d8d-6bb8-41a2-a3c9-69dd3edaa158).
-
In the **Office 365 Tenants or Tenant IDs** field, enter the tenant names or tenant IDs (e.g., corp1.safemarch.com or 784b1673-628c-56e3-c3b2-5d2f0d59524m) that you want to add to this tenant profile, and click **Add Items**.
Do not exempt these domains from [authentication](/zia/about-advanced-settings#auth-exemption).
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add one tenant directory per tenant profile and up to 500 Office 365 tenant names. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- For the **Allow Personal Office 365 Domains** field, select **No** to block the personal Office 365 domains in the tenant profile. This field is set to **Yes **by default. To learn more about allowing personal accounts for Microsoft applications, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).
[]In the **Tenant Directory ID:Policy ID** field, enter the tenant directory ID of your organization followed by the policy ID with a colon in between (e.g., f4c77d8d-6bb8-41a2-a3c9-69dd3edaa158:quadsj) to configure Version 2 tenant profile for Microsoft Login Services. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/governance/policy/overview).
The **Tenant Directory ID** and **Policy ID **are GUIDs from your tenant on the Azure Active Directory portal. You can find these GUIDs as follows:
- **Tenant Directory ID**: Log in as an administrator to the Azure Active Directory portal, select **Azure Active Directory**, and then select **Properties**.
-
**Policy ID**: Call the following API endpoint: `/crosstenantaccesspolicy/default`. Use the `id` field value in the Response preview.
[See image.](#xtap-response)
[]![Screenshot of Azure Active Directory XTAP API Response](/downloads/zia/policies/cloud-apps/tenant-restriction/adding-tenant-profiles/Azure-Active-Directory-XTAP-Response.png)
[]To configure the tenant profile for Slack:
-
In the **Your Workspace ID** field, enter your workspace ID (e.g., T2DQ3J9AA).
If an incorrect value is entered in this field, Slack might allow traffic to any Slack workspace, resulting in a security gap. To approve Slack workspaces for your network, refer to the [Slack help](https://slack.com/intl/en-in/help/articles/360024821873-Approve-Slack-workspaces-for-your-network) page.
-
In the **Allowed Workspace ID** field, enter the allowed workspace IDs you want to add to this tenant profile, and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 256 allowed workspace IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
The service intercepts requests related to Slack and adds the following headers:
- X-Slack-Allowed-Workspaces-Requester (value of the **Your Workspace ID** field)
- X-Slack-Allowed-Workspaces (values of the **Allowed Workspace ID** field)
To learn more about associating tenant profiles of Slack with the Cloud App Control policy rule, see [Adding a Collaboration & Online Meetings Rule for Cloud App Control](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control).
[]To configure the tenant profile for Amazon Web Services, in the **Account IDs** field, enter the account IDs (e.g., 123456789012) you want to add to the tenant profile and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 256 account IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
To learn more about associating tenant profiles of Amazon Web Services with the Cloud App Control policy rule, see [Adding a Hosting Providers Rule for Cloud App Control](/zia/adding-hosting-providers-rule-cloud-app-control).
- Zscaler Internet Access (ZIA) supports the following AWS login methods:
- Sign in to the AWS Management Console as a root user or IAM user.
- Sign in as a federated identity.
- Sign in through the AWS Command Line Interface and other programmatic methods like API and SDK (Software Development Kit).
- Zscaler service supports the tenancy restrictions for Amazon Web Services through CLI. However, the tenancy restrictions via CLI are not supported for the following services:
- Amazon Auto Scaling
- Amazon Bedrock
- Amazon Braket
- Amazon Chime
- Amazon Cloud Directory
- Amazon CloudSearch
- Amazon Comprehend
- Amazon DynamoDB
- Amazon EMR
- Amazon Elastic Block Store
- Amazon Elastic Container Service
- Amazon Elastic File System
- Amazon Elastic Kubernetes Service
- Amazon Elastic Load Balancing
- Amazon Elastic Transcoder
- Amazon Elasticsearch Service
- Amazon EventBridge
- Amazon Fraud Detector
- Amazon FSx
- Amazon Kendra
- Amazon Lex
- Amazon Lightsail
- Amazon Macie
- Amazon MSK
- Amazon Polly
- Amazon S3
- Amazon SES
- Amazon Simple Queue Service
- Amazon SNS
- Amazon Textract
- Amazon Transcribe
- Amazon Translate
- Amazon WorkDocs (Amazon Zocalo)
- Amazon WorkMail
- Amazon Workspaces
- AWS Cloud Financial Management
- AWS Data Exchange
- AWS DataSync
- AWS Identity and Access Management
- AWS Key Management Service
- AWS Managed Services
- AWS Network Firewall
- AWS Resource Access Manager
- AWS Snow Family
- AWS Storage Gateway
- AWS VPN
[]To configure the tenant profile for Dropbox, in the **Dropbox Team ID** field, enter the team IDs (e.g., 4875936) you want to add to this tenant profile, and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 team IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
The service intercepts requests related to Dropbox and adds the HTTP header X-Dropbox-allowed-Team-Ids (values of the **Dropbox Team ID** field). This header's value is the business account's team ID, which can be obtained from the network control section of the Dropbox Business admin console. You must enable network control for tenancy restriction. To learn more about network control, refer to the [Dropbox help](https://help.dropbox.com/security/network-control) page.
To learn more about associating tenant profiles of Dropbox with the Cloud App Control policy rule, see [Adding a File Sharing Rule for Cloud App Control](/zia/adding-file-sharing-rule-cloud-app-control).
[]To configure the tenant profile for Webex Teams and Webex Meetings, in the **Webex Tenants(Webex Teams and Meetings)** field, enter the tenants (e.g., zscaler.com) you want to add to this tenant profile and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 tenants. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
The service intercepts incoming requests to the following domains and adds the HTTP header CiscoSpark-Allowed-Domains (values of the **Webex Tenants(Webex Teams and Meetings)** field):
- identity.webex.com
- identity-eu.webex.com
- idbroker.webex.com
- idbroker-secondary.webex.com
- idbroker-b-us.webex.com
- idbroker-eu.webex.com
- atlas-a.wbx2.com
To learn more about Webex Tenant Restrictions, refer to the [Webex documentation](https://help.webex.com/en-US/article/m0jby2/Configure-a-List-of-Allowed-Domains-to-Access-Webex-While-on-Your-Corporate-Network#task_B58EAD2F2BE2C599F06E0B836DB118D8).
To learn more about associating tenant profiles of Webex Login Services with the Cloud App Control policy rule, see [Adding an IT Services Rule for Cloud App Control](/zia/adding-it-services-rule-cloud-app-control).
[]To configure the tenant profile for Zoho Login Services, in the **Zoho ID** field, enter your Zoho ID (e.g., 100001) you want to add to this tenant profile and click **Add Items**.
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 128 IDs. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
Contact Zoho support to get Zoho ID.
To learn more about associating tenant profiles of Zoho Login Services with the Cloud App Control policy rule, see [Adding an IT Services Rule for Cloud App Control](/zia/adding-it-services-rule-cloud-app-control).
[]To configure the tenant profile for the Google Cloud Platform:
-
In the **Allowed Organization IDs** field, enter the allowed organization IDs (e.g., 123456789012) you want to add to this tenant profile and click **Add Items**. To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/resource-manager/docs/organization-restrictions/configure-organization-restrictions).
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 tenants. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- For the **Allow Cloud Storage Resources** field, select **Yes** to allow the users to access the public cloud storage resources. This field is set to **No **by default.
To learn more about associating Google Cloud Platform tenant profiles with the Cloud App Control policy rule, see [Adding a Hosting Providers Rule for Cloud App Control](/zia/adding-hosting-providers-rule-cloud-app-control).
[]To configure a tenant profile for Zoom, in the **Policy Label** field, enter the policy label associated with the X-ZoomApps-Policy header for Zoom.
Contact Zoom Support for the policy label.
To learn more about associating Zoom tenant profiles with the Cloud App Control policy rule, see [Adding a Collaboration & Online Meetings Rule for Cloud App Control](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control).
You can associate only one Zoom tenant profile with the Cloud App Control policy rule.
[]To configure a tenant profile for IBM SmartCloud, in the **IBM Account IDs** field, enter the account IDs (e.g., 1234567890123456) associated with the IBM-Cloud-Tenant header for IBM SmartCloud and click **Add Items**. To learn more, refer to the [IBM Cloud documentation](https://www.ibm.com/blog/how-to-limit-access-to-specific-ibm-cloud-accounts/).
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 100 account IDs per profile. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
The service intercepts incoming requests to cloud.ibm.com and its subdomain (*cloud.ibm.com) and adds the HTTP header IBM-Cloud-Tenant (values of the **IBM Account IDs** field).
To learn more about associating IBM SmartCloud tenant profiles with the Cloud App Control policy rule, see [Adding a Hosting Providers Rule for Cloud App Control](/zia/adding-hosting-providers-rule-cloud-app-control).
[]To configure a tenant profile for GitHub, in the **Enterprise Slug for GitHub** field, enter the enterprise slug (e.g., avocado-corp) associated with the sec-GitHub-allowed-enterprise header for GitHub. To learn more, refer to the [GitHub documentation](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-your-enterprise-account/creating-an-enterprise-account#upgrading-an-organization-to-an-enterprise-account).
You can add only one enterprise slug per profile. To learn more, see [Ranges & Limitations](/zia/ranges-limitations).
To learn more about associating GitHub tenant profiles with the Cloud App Control policy rule, see [Adding a System & Development Rule for Cloud App Control](/zia/adding-system-development-rule-cloud-app-control).
[]To configure a tenant profile for ChatGPT, in the **Workspace ID for ChatGPT** field, enter the workspace ID (e.g., 437adf77-4085-4b22-b7b1-de7b6f5ec6c0) associated with the ChatGPT-Allowed-Workspace-Id header for ChatGPT and click **Add Items**. To learn more, refer to the [ChatGPT documentation](https://help.openai.com/en/articles/8798594-what-is-a-workspace-how-do-i-access-my-chatgpt-team-workspace).
To enter multiple entries, press **Enter** after each entry, then click **Add Items**. You can add up to 16 workspace IDs per profile. To learn more, see [Ranges & Limitations](/zia/ranges-limitations). For item lists, you can filter the list by searching for a word, phrase, or number contained in an item, and you can remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
The service intercepts requests related to chatgpt.com and its subdomain (*chatgpt.com) and adds the HTTP header ChatGPT-Allowed-Workspace-Id (values of the **Workspace ID for ChatGPT** field).
To learn more about associating ChatGPT tenant profiles with the Cloud App Control policy rule, see [Adding an AI & ML Applications Rule for Cloud App Control](/zia/adding-ai-ml-applications-rule-cloud-app-control).
[]![Add Tenant Profile page.](/downloads/zia/policies/cloud-apps/tenant-restriction/adding-tenant-profiles/ZIA-Add-Tenant-Profile.png)