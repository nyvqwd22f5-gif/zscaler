# Adding SaaS Application Tenants
Source: https://help.zscaler.com/zia/adding-saas-application-tenants
PDF: https://help.zscaler.com/pdf/com/en/1401256.pdf

[Watch a video about SaaS Application Tenants](https://fast.wistia.net/embed/iframe/net3zjd13m)
Zscaler Data at Rest Scanning provides visibility and security for [sanctioned SaaS applications](/zia/about-saas-application-tenants) used in your organization. You can authorize sanctioned SaaS applications with Zscaler by adding them as tenants. Most apps require configuration to provide Zscaler access and enable their full functionality.
To add a SaaS application tenant:
- Go to **Administration** > **SaaS Application Tenants**.
-
Click **Add SaaS Application Tenant**.
The **Add SaaS Application Tenant** page appears.
-
Under **Choose the SaaS Application Provider**, search for or choose from one of the sanctioned SaaS applications.
[See image.](#seeimage3)
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique. This name is displayed when configuring the Data at Rest Scanning DLP policy, Malware Detection policy, Workflow Automation, or Scan Configuration depending on the functionality available for that specific application.
-
Under **Onboard SaaS Application for**, select the checkbox for the functionality you want to enable. You can choose from **App Governance**, **DLP and Malware scanning SaaS API**, **SSPM Scan**, or **Workflow Automation** if the app supports the functionality.
[See image.](#nametenant)
To learn more about the different onboarding functionalities, see [Connecting Your Platforms to 3rd-Party App Governance](/zia/connecting-your-platforms-3rd-party-app-governance), [About Data at Rest Scanning Malware Detection](/zia/about-data-rest-scanning-malware-detection), [What Is Advanced Posture Management?](/zia/what-advanced-posture-management), and [What Is Workflow Automation?](/workflow-automation/what-workflow-automation)
- Complete the specific configuration steps for your chosen application:
- [][Amazon S3](#amazons3)
- [Bitbucket](#bitbucket)
- [Box](#box)
- [ChatGPT](#chatgpt)
- [Confluence](#confluence)
- [Docusign](#docusign)
- [Dropbox](#dropbox)
- [Dynamics 365](#msft_dynamics365)
- [GitHub](#github)
- [GitLab](#gitlab)
- [Gmail](#gmail)
- [Google Cloud](#GoogleCloud)
- [Google Drive](#googledrive)
- [Google Workspace](#google-workspace)
- [Google Workspace Marketplace](#GoogleMarketplaceWorkspace)
- [Jira Software](#jira)
- [Microsoft 365](#M365)
- [Microsoft Azure](#MSAzure)
- [Microsoft Copilot](#copilot)
- [Microsoft Exchange](#exchange)
- [Microsoft OneDrive](#onedrive)
- [Microsoft SharePoint](#sharepoint)
- [Microsoft Teams](#teams)
- [Okta](#okta)
- [Salesforce](#salesforce)
- [ServiceNow](#servicenow)
- [ShareFile](#sharefile)
- [Slack](#slack)
- [Smartsheet](#smartsheet)
- [Trello](#trello)
- [Twilio](#twilio)
- [Webex Teams](#WebexTeams)
- [Workday](#workday)
- [Zoom](#zoom)
- Under **(Optional) Configure External Trusted Domains & Users for the Tenant**:
-
Click the drop-down menu for **External Trusted Domains** or **External Trusted Users**.
[See image.](#optional_domains)
- **External Trusted Domains**: Select trusted email domains that are outside your organization (i.e., using a different domain). The Zscaler service views any email addresses from the added domains as trusted, internal users. For example, if your organization's domain is safemarch.com and your organization recently acquired a company with the domain example.com, you can add example.com to this list, and the service treats any email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. You can add up to 1,000 domains.
- **External Trusted Users**: Select trusted email addresses that are outside your organization (i.e., using a different email domain). The Zscaler service views the email addresses as trusted, internal users. For example, if your organization's email domain is safemarch.com and your organization recently salecontracted with someone using an external email domain (e.g., johnsmith@example.com), you can add the contractor's email to this list, and the service treats the contractor as an internal user from safemarch.com. You can add up to 1,000 email addresses.
If you use an external trusted domain or external trusted user when onboarding a SaaS application tenant, the same domain or user profile is not available to use as part of your SaaS Security Data at Rest Scanning DLP policy rules because those domains and users are already considered internal. To learn more, see [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-content-inspection) and [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection).
-
You can search for and select from your list of domain or recipient profiles created under the **Email Profiles** page. Up to 32 profiles can be selected for a single tenant. To learn more, see [About Email Profiles](/zia/about-email-profiles) and [Ranges & Limitations](/zia/ranges-limitations).
[See image.](#optional_domains_select)
- If you don’t have any domain or recipient profiles created, you can click the **Add** icon next to the search bar and create a new one. To learn more about creating profiles, see [About Email Profiles](/zia/about-email-profiles).
- After selecting your profiles, click **Done**.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
After adding the tenants, you can configure the Data at Rest Scanning [DLP policy](/zia/about-saas-security-api-dlp), [Malware Detection policy](/zia/about-saas-security-api-malware-detection), and [Scan Configuration](/zia/about-saas-security-api-scan-configuration). You can also view reports and data for the tenants in the SaaS Security [Report](/zia/saas-security-report), [Insights](/zia/saas-security-insights), and [Logs](/zia/saas-security-insights-logs).
You can add up to 16 tenants per SaaS application. Contact Zscaler Support for a possible increase in this limit.
[]![Choose the SaaS Application Provider section in the Add SaaS Application Tenant page](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Adding%20SaaS_Tenants_24.11.08_0.png)
[]To enable Amazon S3 for your organization, contact your Zscaler Account team.
Zscaler and AWS are technology partners. To learn more about the Zscaler and Amazon S3 integration, see the [Zscaler and AWS Deployment Guide](/zscaler-technology-partners/zscaler-and-aws-deployment-guide).
To configure Amazon S3:
- [a. Configure an IAM Role for the Zscaler S3 Connector](#aws-iam-role)
- [b. Edit the Trust Relationship](#aws-edit-trust-relationship)
- [c. Obtain the CloudTrail Bucket ARN](#aws-cloudtrail-bucket-arn)
- [d. Create a Quarantine Bucket](#aws-quarantine-bucket)
To learn more about the steps in AWS, refer to the [AWS documentation](https://docs.aws.amazon.com/).
- [][]Under **Authorize the SaaS Application**, copy the **Zscaler S3 Connector** and **Zscaler S3 Connector User ARN**.
[See image.](#seeimageamazons3-aii)
- Click **Go to AWS**.
[See image.](#seeimageamazons3-aiii)
The AWS portal appears.
- Log in to AWS.
- Go to **Services** > **IAM**.
- In the left-side navigation, go to **Access management** > **Roles**.
[See image.](#seeimageamazons3-avi)
- Click **Create role**.
[See image.](#seeimageamazons3-avii)
- In **Select type of trusted entity**, click **Another AWS account**.
[See image.](#seeimageamazons3-aviii)
- In **Specify accounts that can use this role**:
- **Account ID**: Enter the Zscaler S3 Connector value you copied in [Step i](#aws-step-aii).
- **Require external ID (Best practice when a third party assumes this role)**: Deselect.
- **Require MFA**: Deselect.
[See image.](#seeimageamazons3-aix)
- Click **Next: Permissions**.
- In **Attach permissions policies**, enter `AmazonS3FullAccess` in the search bar, and select it.
[See image.](#seeimageamazons3-axi)
- Click **Next: Tags**.
- In **Add tags (optional)**, enter a key-value pair.
[See image.](#seeimageamazons3-axiii)
- Click **Next: Review**.
- In **Review**:
- **Role name**: Enter a role name.
- **Description**: (Optional) Enter additional notes or information.
[See image.](#seeimageamazons3-axv)
- Click **Create role**.
[]![Tenant Name field in the Name the SaaS Application Tenant section](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Name%20and%20Onboard_0.png)
[]![The Copy buttons for the Zscaler S3 Conenctor and Zscaler S3 Connector User ARN](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Amazon%20S3%20External%20ID.png)
[]![The Go to AWS button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Go-to-AWS.png)
[]![The Roles menu for AWS Identity and Access Management (IAM)](/downloads/zia/adding-saas-application-tenants/AWS-IAM-Roles-menu.png)
[]![The Create role button on the Roles page.](/downloads/zia/adding-saas-application-tenants/AWS-Create-Role-Button.png)
[]![The Another AWS account option in the Select type of trusted entity section.](/downloads/zia/adding-saas-application-tenants/AWS-Select-type-of-trusted-entity-Another-AWS-account.png)
[]![The Specify accounts that can use this role section.](/downloads/zia/adding-saas-application-tenants/AWS-Specify-accounts-that-can-use-this-role-section.png)
[]![The AmazonS3FullAccess policy in the Attach permissions policies section.](/downloads/zia/adding-saas-application-tenants/AWS-Attach-permissions-policies-section.png)
[]![The configured key-value pair in the Add tags (optional) section.](/downloads/zia/adding-saas-application-tenants/AWS-Add-tags-optional-key-value.png)
[]![The Review section in the Create role window.](/downloads/zia/adding-saas-application-tenants/AWS-Review-Section.png)
- []Click the **Role Name** of the IAM role you created in [a. Configure an IAM Role for the Zscaler S3 Connector](#aws-iam-role).
[See image.](#seeimageamazons3-bi)
- Click the **Trust relationships** tab.
[See image.](#seeimageamazons3-bii)
- Click** Edit trust relationship**.
[See image.](#seeimageamazons3-biii)
- Under **Policy Document**, delete the existing `AWS` value, and enter the Zscaler S3 Connector User ARN you copied in Step i of [a. Configure an IAM Role for the Zscaler S3 Connector](#aws-iam-role):
{
"Version": "2012-10-17",
"Statement": [
{
"Effect": "Allow",
"Principal": {
"AWS": "arn:aws:iam::123456789012:user/AccountAadmin"
},
"Action": "sts:AssumeRole",
"Condition": {}
}
]
}
[See image.](#seeimageamazons3-biv)
- Click **Update Trust Policy**.
- Under **Summary**, copy the **Role ARN**. You need it for Step vi of [d. Create a Quarantine Bucket](#aws-quarantine-bucket).
[See image.](#seeimageamazons3-bvi)
[]![The Role name column on the Roles page.](/downloads/zia/adding-saas-application-tenants/AWS-Role-Name-Column.png)
[]![The Trust relationships tab on the Summary page.](/downloads/zia/adding-saas-application-tenants/AWS-Summary-Trust-relationships-Tab.png)
[]![The Edit trust relationship button in the Trust relationships tab.](/downloads/zia/adding-saas-application-tenants/AWS-Trust-relationships-Edit-trust-relationship.png)
[]![The updated Policy document on the Edit Trust Relationship page.](/downloads/zia/adding-saas-application-tenants/AWS-Edit-Trust-Relationship-Policy-Document.png)
[]![The Copy icon for the Role ARN on the Summary page.](/downloads/zia/adding-saas-application-tenants/AWS-Srummary-Role-ARN-Copy-Button.png)
You can use a single CloudTrail account to onboard multiple tenants. To learn more about CloudTrail, refer to the [AWS CloudTrail documentation](https://aws.amazon.com/cloudtrail/resources/?blog-posts-cards.sort-by=item.additionalFields.createdDate&blog-posts-cards.sort-order=desc).
- []Go to **Services** > **CloudTrail**.
- In the left-side navigation, click **Trails**.
[See image.](#seeimageamazons3-cii)
- In the **Name** column, click **s3-log-trail**.
[See image.](#seeimageamazons3-ciii)
-
To enable S3 data events, click **Edit** next to **Data events**. If you have already enabled S3 data events, skip to the [Trails step](#trails).
[See image.](#DE-Edit)
-
Check the **Data events** box. If **Advanced event selectors** are not enabled, click **Switch to advanced event selectors**.
[See image.](#DE-Switch)
-
In the **Data event type** drop-down menu, select **S3**. Then, make sure the **Log selector template** is set to **Log all events**.
[See image.](#DE-S3)
- Click **Save changes**.
- []Back on your **Trails** page, in **General details**, click the **Trail log location**.
[See image.](#seeimageamazons3-civ)
- In **Objects**, click **CloudTrail/**.
[See image.](#seeimageamazons3-cv)
- Click the **Properties** tab.
[See image.](#seeimageamazons3-cvi)
- Under **Amazon Resource Name (ARN)**, copy the CloudTrail bucket ARN. You need it for Step vi of [d. Create a Quarantine Bucket](#aws-quarantine-bucket).
[See image.](#seeimageamazons3-cvii)
[]![The Trails menu for AWS CloudTrail.](/downloads/zia/adding-saas-application-tenants/AWS-CloudTrail-Trails-Menu.png)
[]![The s3-log-trail on the Trails page.](/downloads/zia/adding-saas-application-tenants/AWS-Trails-s3-log-trail.png)
[]![The Trail log location in the General details section.](/downloads/zia/adding-saas-application-tenants/AWS-General-details-Trail-log-location.png)
[]![The CloudTrail/ folder in the Objects section.](/downloads/zia/adding-saas-application-tenants/AWS-Objects-CloudTrail-Folder.png)
[]![The Properties tab of the CloudTrail/ folder.](/downloads/zia/adding-saas-application-tenants/AWS-CloudTrail-Folder-Properties-Tab.png)
[]![The CloudTrail bucket Amazon Resource Name (ARN) in the Folder overview section.](/downloads/zia/adding-saas-application-tenants/AWS-CloudTrail-Folder-Overview-Amazon-Resource-Name-ARN.png)
[]![Editing Data events](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Data%20Events%20edit.png)
[]![Switch to advanced event selectors](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Data%20Events%20advanced%20event.png)
[]![Select S3 as data event type](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Data%20events%20type.png)
- []In the left-side navigation, click **Buckets**.
[See image.](#seeimageamazons3-di)
- Click **Create bucket**.
[See image.](#seeimageamazons3-dii)
The **Create bucket** window appears.
- In the **Create bucket** window:
- **Bucket name**: Enter a unique name for the quarantine bucket.
- **AWS Region**: Use the default region.
- **Block *****all***** public access**: Select.
- **Bucket Versioning**: Disable.
- **Tags**: (Optional) Click **Add tag** to tag your quarantine bucket.
- **Default Encryption**: Server-side encryption with Amazon S3 managed keys (SSE-S3)
[See image.](#seeimageamazons3-diii)
- Click **Create bucket**.
- []In the **Name** column, copy the quarantine bucket name.
[See image.](#seeimageamazons3-dv)
- In the ZIA Admin Portal, under **Register the SaaS Application**:
- **AWS Account ID**: Enter the ID of the AWS account used to configure the Zscaler S3 Connector.
- **IAM Role ARN**: Enter the IAM role ARN you copied in [b. Edit the Trust Relationship](#aws-edit-trust-relationship).
- **Quarantine Bucket Name**: Enter the quarantine bucket name you copied in [Step v](#aws-step-dv). If you add a [Malware Detection rule](/zia/configuring-saas-security-api-malware-detection-policy) with the action **Quarantine Malware**, the Zscaler servicemoves the malicious files detected to this bucket.
- **CloudTrail Bucket ARN**: Enter the ARN of the CloudTrail bucket, which stores your S3 data event logs.
[See image.](#seeimageamazons3-dvi)
[]![The Buckets menu for Amazon S3.](/downloads/zia/adding-saas-application-tenants/AWS-Amazon-S3-Buckets-Menu.png)
[]![The Create bucket button on the Buckets page.](/downloads/zia/adding-saas-application-tenants/AWS-Buckets-Create-bucket-Button.png)
[]![The configured Create bucket window.](/downloads/zia/adding-saas-application-tenants/AWS-Create-Bucket-Window.png)
[]![The quarantine bucket name listed in the Name column of the Buckets page.](/downloads/zia/adding-saas-application-tenants/AWS-Quarantine-Bucket-Name.png)
[]![The Register the SaaS Application section on the Add SaaS Application Tenant page.](/downloads/zia/adding-saas-application-tenants/ZIA-Register-the-SaaS-Application.png)
[]
Zscaler and Atlassian are technology partners. To learn more about the Zscaler and Atlassian (including Bitbuket) integration, see the [Zscaler and Atlassian Deployment Guide](/zscaler-technology-partners/zscaler-and-atlassian-deployment-guide).
To configure Bitbucket:
- Under **Enter Bitbucket Admin Email ID**, enter your admin email ID.
[See image.](#bitbucket01)
- Click **Provide Admin Credentials** and sign in to your Bitbucket account.
[See image.](#bitbucket02)
- Click **Save**.
[]![Enter Bitbucket admin email ID.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/BB01_Admin%20Email%20ID.png)
[]![Provide admin credentials.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/BB02_Authorize.png)
[]
Zscaler and Box are technology partners. To learn more about the Zscaler and Box integration, see the [Zscaler and Box Deployment Guide](/zscaler-technology-partners/zscaler-and-box-deployment-guide).
To configure Box:
Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#box-connector)
- [Zscaler-Defined](#step-b)
- [Custom](#custom_box)
- []Under **Authorize the SaaS Application**, select **Custom**.
-
Sign in to the [Box Developer Console](https://developer.box.com/), select **My Apps**, and then click **Create new app**.
If you don't have any apps yet, Box might directly open the next step after selecting **My Apps**.
[See image.](#box-myapps)
-
Select **Custom App**.
[See image.](#box-custom)
-
Enter an app name with `Zscaler` as the prefix, and under **Purpose**, select **Integration**. Fill in the rest of the required information based on your app needs and click **Next**.
[See image.](#box-appname)
-
For the **Authentication Method**, select **Server Authentication (with JWT)** and click **Create App**.
[See image.](#box-auth)
- On the **Configuration** tab, next to the **Application Scopes** section, select the following scopes:
- **Write all files and folders stored in Box**
- **Manage users**
- **Manage groups**
- **Manage enterprise properties**
-
In the **Advanced Features** section, select:
- **Make API calls using the as-user header**
- **Generate user access tokens**
To learn more about the required API permissions, see the following table:
- [API Permissions for Box](#BoxAPI)
-
In the **App Access Level** section, select **App + Enterprise Access** and click **Save Changes**.
[See image.](#box-access)
-
[]In the **Add and Manage Public Keys **section, select **Generate a Public/Private Keypair** and your JSON file is downloaded.
[See image.](#box-key)
- Next, you need to enable Suppress Notifications by referring to the [Box documentation](https://developer.box.com/guides/api-calls/suppress-notifications/). You need to contact your Box support contact to request the required scopes to be enabled for your application.
-
In the ZIA Admin Portal, under **Authorize the SaaS Application**, select **Custom** and then click **Upload File** to upload the JSON file you generated in a [previous step](#box_json).
[See image.](#box-upload)
- Click **Authorize** and then click **Save**.
[]
| Box Permissions | Associated Zscaler Actions |
| --------------- | -------------------------- |
| Content Actions > Write all files and folders stored in Box | Scanning, Policy Action |
| Administrative Actions > Manage Users | Scanning, Policy Action |
| Administrative Actions > Manage Groups | Scanning |
| Administrative Actions > Manage Enterprise Properties | Scanning |
| Administrative Actions > Make API calls using the as-user heading | Scanning, Policy Action |
- []Under **Authorize the SaaS Application**, copy the **Zscaler SaaS Connector**. You need it for [Step g](#step-h) when adding a custom application for Box.
[See image.](#seeimagebox-b)
- Click **Go to Box Settings**.
[See image.](#seeimagebox-c)
The Box portal appears.
- Log in to Box.
You are redirected to the Box Admin console.
- Go to **Apps**.
[See image.](#seeimagebox-e)
- Click the **Custom Apps Manager** tab.
[See image.](#seeimagebox-f)
- Click **Add App**.
[See image.](#seeimagebox-g)
The **App Authorization** window appears.
- []In the **App Authorization** window:
- **Client ID**: Enter Zscaler SaaS Connector value you copied in [Step a](#step-b).
[See image.](#seeimagebox-h-i)
- Click **Next**.
- Review the required permissions for the Zscaler service to access Box, and click **Authorize**.
- Click **Okay**.
- Go to **Account & Billing**.
[See image.](#seeimagebox-i)
- Under **Account Information**, copy the **Enterprise ID**.
[See image.](#seeimagebox-j)
- In the ZIA Admin Portal, under **Enter the Box Enterprise ID**, enter the Enterprise ID you copied from Box in the previous step.
[See image.](#seeimagebox-k)
To learn more about the steps in Box, refer to the [Box documentation](https://community.box.com/t5/Box-Community/ct-p/English).
[]![Screenshot of the Copy button under Zscaler SaaS Connector in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Copy-Box.png)
[]![Choose Zscaler Defined or Custom SaaS Connector](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc51976/Box-connector.png)
[]![Screenshot highlighting the Go to Box Settings button under the Authorize the SaaS Application.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Go-Box-Settings-6_1.png)
[]![Screenshot of the Apps menu in the Box Admin Console.](/downloads/zia/adding-saas-application-tenants/Box%20left%20nav.png)
[]![Screenshot of the Custom Apps tab in the Apps menu.](/downloads/zia/adding-saas-application-tenants/Box%20custom%20apps.png)
[]![Screenshot of the Authorize New App button under Custom Apps.](/downloads/zia/adding-saas-application-tenants/Box%20new%20app.png)
[]![Screenshot of the Client ID field in the App Authorization window.](/downloads/zia/adding-saas-application-tenants/Box-App-Authorization-Client-ID.png)
[]![Screenshot of the Account & Billing menu in the Box Admin Console.](/downloads/zia/adding-saas-application-tenants/Box%20left%20nav%20billing.png)
[]![Screenshot of the Enterprise ID in the Account Information section.](/downloads/zia/adding-saas-application-tenants/Box%20Enterprise%20ID.png)
[]![Screenshot of the Box Enterprise ID field in the Enter the Box Enterprise ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-Box-Enterprise-ID-6_1.png)
[]![Box Dev My Apps button](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-myapps.png)
[]![Select Custom App](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-customapp.png)
[]![Name the app and provide additional details](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-createcustom.png)
[]![Server authentication with JWT](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-authentication.png)
[]![Select App and Enterprise Access](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-appaccess.png)
[]![Generate a Public/Private keypair JSON file](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-key.png)
[]![Upload JSON file](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Box-upload.png)
[]To configure ChatGPT:
- Sign in to the [OpenAI API platform](https://platform.openai.com) with your admin credentials.
- Go to **API Keys** in the left-side navigation.
- Click **Create new secret key**.
-
Enter a **Name**, under **Project** select **Default project**, and under **Permissions** select **All**. Click **Create secret key**.
[See image.](#cgpt_secret)
- Save your key to use during onboarding. It can only be copied and viewed once. If you lose it, you need to generate a new one.
- Log in to [ChatGPT](https://chatgpt.com) and then go to the [ChatGPT admin settings](https://chatgpt.com/admin/settings).
-
Copy the **Workspace ID** and save it.
[See image.](#cgpt_id)
- To enable the necessary enterprise APIs, write an email to [OpenAI support](mailto:support@openai.com) requesting them to be enabled and include your secret key name, secret key, and workspace ID. Wait for confirmation that the APIs are enabled before continuing to onboard the application.
-
In the ZIA Admin Portal under **Authorize the SaaS Application**, enter your **Workspace Name**, **Workspace ID**, and **Workspace Secret Key**. Click **Authorize**.
[See image.](#cgpt_auth)
[]![Create and setup the secret key](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc51976/chatgpt%2001%20secretkey_0.png)
[]![Workspace ID location](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/chatgpt%2002%20workspace.png)
[]![Enter the Workspace Name, ID, and Secret Key](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/chatgpt%2003%20authorize.png)
[]To configure Confluence:
- Enter the **Atlassian Domain Address** you want to connect with Zscaler.
[See image.](#confluence01)
- Enter your **Confluence Organization API Key**. For help finding your API Key, follow the instructions on [Atlassian Support](https://support.atlassian.com/organization-administration/docs/manage-an-organization-with-the-admin-apis/).
[See image.](#confluence02)
- Click **Provide Admin Credentials** and sign in to your Confluence account.
- Click **Save**.
For Confluence, the Data at Rest Scanning DLP rule scans all the blogs, pages, and attachments within a space. The DLP rule does not scan the overview page for any space.
[]![Enter Atlassian Domain Address.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Confluence%20Atlassian.png)
[]![Enter Confluence API Key.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Con02.1_APIKey.png)
[]To configure ShareFile:
- Under **Enter the ShareFile Admin Email ID**, enter your admin email ID used to log in to the ShareFile portal.
[See image.](#seeimagesharefile-b)
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials**.
[See image.](#seeimagesharefile-c)
The ShareFile portal appears.
- Log in to ShareFile.
[]![Screenshot of the ShareFile Admin Email ID field in the Enter the ShareFile Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-ShareFile-Admin-Email-ID-6_1.png)
[]![Screenshot highlighting the Provide Admin Credentials button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Provide-Admin-Credentials-ShareFile.png)
[]To configure Docusign:
- Log in to the [Docusign Developer Center](https://developers.docusign.com/) by clicking the **Developer Account** drop-down menu and clicking **Log in**.
-
Click your **profile** icon in the top-right corner and click **My Apps & Keys**.
[See image.](#docu_keys)
- Click on **Add App and Integration Key**.
-
Enter an **App Name** and then click **Add Secret Key** to auto generate a secret key. Copy the integration and secret keys for use later.
[See image.](#docu_secret)
-
Click **Add URI** to add the redirect URI for your Zscaler cloud. For example, if your Zscaler cloud name is zscalertwo.net, then your redirect URI is `https://admin.``zscalertwo.net``/`. To learn how to find your Zscaler cloud, see [What is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
[See image.](#docu_uri)
- Click **Save**.
-
On the **Apps and Keys** page, copy your **API Account ID** and **Account Base URI**.
[See image.](#docu_id)
-
In the ZIA Admin Portal under **Register the OAuth Application**, enter your the **Client ID** (your Docusign Integration Key), **Secret Key**, **Account ID**, and **Base URI** that you copied earlier.
[See image.](#docu_register)
- Under **Enter the Docusign Admin Email ID**, enter your admin email ID.
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials** and log in with the Docusign account associated with this instance.
[]![Docusign main page with profile icon and My Apps and Keys links highlighted](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Docusign_appsandkeys.png)
[]![Docusign Apps and Keys page showing App Name, Integration Key, Secret Keys, and Redirect URIs](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Docusign_appsandkeys_page1.png)
[]![Additional settings section displaying the Add Secret Key button and field](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Docusign_appsandkeys_page2.png)
[]![Docusign account information including User ID, API Account ID, and Account Base URI](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Docusign_accountinfo.png)
[]![ZIA Register the OAuth Application section with Client ID, Secret Key, Account ID, and Account Base URI](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Docusign_register.png)
[]To configure Dropbox:
- Under **Enter the Dropbox Enterprise ID**, enter your Dropbox Enterprise email address.
[See image.](#DropboxAdminEmailID)
- Under **Authorize the SaaS Application**, click **Redirect to Dropbox**.
[See image.](#seeimagedropbox-b)
The Dropbox portal appears.
- Log in to Dropbox.
- For the **Before you connect this app...** warning, click **Continue.**
[See image.](#seeimagedropbox-e)
- Review the required permissions for the Zscaler service to access Dropbox and click **Allow**.
The ZIA Admin Portal refreshes and adds the Dropbox **Team ID** under **Authorize the SaaS Application**.
[See image.](#seeimagedropbox-f)
To learn more about the steps in Dropbox, refer to the [Dropbox documentation](https://help.dropbox.com/).
[][![Enter your Dropbox Enterprise login email ID.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Dropbox_2.email_login.png)
]
[]![Screenshot highlighting the Go to Dropbox button in the Authorize the SaaS Application section.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Dropbox_3.SaaS_Authorization.png)
[]![Screenshot highlighting the Continue button in the Before you connect this app... warning.](/downloads/zia/adding-saas-application-tenants/Dropbox-Before-you-connect-this-app-warning.png)
[]![Screenshot of the Dropbox Team ID in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Dropbox-Team-ID.png)
[]To configure Dynamics 365:
- Under **Enter Organization Domain Address**, enter the URL used to log in to your Dynamics 365 instance.
- Under **Authorize the SaaS Application **you can click **Provide Admin Credentials** and log in with the Microsoft account associated with your Dynamics 365 instance.
[See image.](#dynamics365-2)
- Click **Save**.
To learn more about the steps in Dynamics 365, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/dynamics365/).
[]![Dynamics%20365%20Admin%20Credentials.png](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Dynamics%20365%20Admin%20Credentials.png)
[]To configure GitHub:
- Under **Enter the GitHub Admin Email ID**, enter your admin email ID used to log in to the GitHub portal.
[See image.](#seeimagegithub-b)
-
Under **Authorize the SaaS Application**, click **Provide Admin Credentials** and then log in to Github.
[See image.](#seeimagegithub-c)
-
If you don't have SAML enabled for your organization, the GitHub Permissions page opens. Click **Grant** for all organizations you would like the scans to run for and then click **Authorize**.
[See image.](#github_grant)
To learn more about enabling SAML, see [Configuring SAML](/zia/configuring-saml) and [Adding Identity Providers](/zia/adding-identity-providers).
-
If you do have SAML enabled, the single sign-on page opens. Click **Authorize** and then **Continue**.
[See image.](#github_SAMLauth)
-
Click Grant on all organizations you want to provide Zscaler access to, and click **Authorize**.
[See image.](#github_SAMLgrant)
- Click **Save**.
[]![Screenshot of the GitHub Admin Email ID field in the Enter the GitHub Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-GitHub-Admin-Email-ID-6_1.png)
[]![Screenshot highlighting the Provide Admin Credentials button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Provide-Admin-Credentials-GitHub.png)
[]![Grant access to organization](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/github_grant02.png)
[]![Single sign-on authorize](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/github_SAMLauthorize.png)
[]![Authorize with SAML](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/github_SAMLgrant.png)
[]
Zscaler and GitLab are technology partners. To learn more about the Zscaler and GitLab integration, see the [Zscaler and GitLab Deployment Guide](/zscaler-technology-partners/zscaler-and-gitlab-deployment-guide).
To configure GitLab:
- Under **Enter the GitLab Admin Email ID**, enter your admin email ID used to log in to GitLab.
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials** and log in with your GitLab information.
- Click **Save**.
To learn more about the steps in GitLab, refer to the [GitLab documentation](https://about.gitlab.com/support/).
[]To configure Gmail:
- [Zscaler Defined](#zd_gmail0)
- [Custom](#custom_gmail)
- []Enter your **Google Admin Email ID**.
- []Under **Authorize the SaaS Application**, select Zscaler Defined, copy the **Zscaler SaaS Connector** and **Google Workspace Scope**. You need it for a [later step](#gmailstep-i) when adding an API client for Google Workspace.
[See image.](#seeimagegmail-b)
- Click **Go to Google Workspace**.
The Google Workspace portal appears.
- Log in to Google Workspace.
You are redirected to the Google Admin console.
- Go to **Security**.
[See image.](#seeimagegmail-e)
- Click **API controls**.
[See image.](#seeimagegmail-f)
- Under **Domain wide delegation**, click **MANAGE DOMAIN WIDE DELEGATION**.
[See image.](#seeimagegmail-g)
- Click **Add new**.
[See image.](#seeimagegmail-h)
The **Add a new client ID** window appears.
- []In the **Add a new client ID** window:
- **Client ID**: Enter Zscaler SaaS Connector value you copied in [a previous step](#gmailstep-b).
- **Overwrite existing client ID**: Deselect.
- **OAuth scopes (comma-delimited)**: Enter the Google Workspace scope you copied in [a previous step](#gmailstep-b).
[See image.](#seeimagegmail-i)
- Click **Authorize**.
The Zscaler Connector App is added as an API client.
- (Optional) Under **(Optional) Configure External Trusted Domains & Users for the Tenant**:
- **External Trusted Domains**: Enter trusted email domains that are outside your organization (i.e., using a different domain). The Zscaler service views any email addresses from the added domains as trusted; internal users for Gmail. For example, if your organization's domain is safemarch.com and your organization recently acquired a company with the domain example.com, you can add example.com to this list, and the service treats any email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. You can add up to 1,000 domains.
- **External Trusted Users**: Enter trusted email addresses that are outside your organization (i.e., using a different email domain). The Zscaler service views the email addresses as trusted, internal users for Gmail. For example, if your organization's email domain is safemarch.com and your organization recently contracted with someone using an external email domain (e.g., johnsmith@example.com), you can add the contractor's email to this list, and the service treats the contractor as an internal user from safemarch.com. You can add up to 1,000 email addresses.
[See image.](#seeimagegmail-l)
To learn more about the steps in the Google Admin console, refer to the [Google documentation](https://support.google.com/a/?hl=en#topic=4388346).
[]To create a custom Gmail Connector, you must first configure permissions in Google so that you can provide the **Private Key JSON** file for the Gmail account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![Screenshot of the Copy buttons for Zscaler SaaS Connector and Google Workspace Scope in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Copy-Gmail-6_1.png)
[]![Screenshot highlighting the Security menu in the Google Admin console.](/downloads/zia/adding-saas-application-tenants/Google-Security-menu-6_1.png)
[]![Screenshot of the API controls option in Security.](/downloads/zia/adding-saas-application-tenants/Google-API-controls.png)
[]![Screenshot highlighting the MANAGE DOMAIN WIDE DELEGATION button in the Domain wide delegation section.](/downloads/zia/adding-saas-application-tenants/Google-Manage-Domain-wide-delegation-button.png)
[]![Screenshot highlighting the Add new button for API clients.](/downloads/zia/adding-saas-application-tenants/Google-API-clients-Add-new-button.png)
[]![Screenshot of the configured Add a new client ID window.](/downloads/zia/adding-saas-application-tenants/Google-Add-new-client-ID-window-6_1.png)
[]![Screenshot of the (Optional) Configure External Trusted Domains & Users for the Tenant section.](/downloads/zia/adding-saas-application-tenants/zia-optional-configure-external-trusted-domains-users-tenant-gmail-6_1.png)
[]To enable Google Cloud for your organization, contact your Zscaler Account team.
- [Zscaler Defined](#zd_gcp)
- [Custom](#custom_gcp)
- [][a. Configure Google Cloud](#GCConfig)
- [b. Create Quarantine Bucket](#GCBucket)
- [c. Authorize Service Account and Add Scope](#GCAuthorize)
- [d. Create and Assign Role to Organization Administrator](#GCRole)
- [e. Enable Audit Logs](#GCAudit)
- [f. Confirm Activation of Cloud Storage JSON API for All Older Projects](#GCJSON)
- []Enter your **Google Cloud Admin Email ID**.
- Under **Authorize the SaaS Application:**
- Click Zscaler Defined.
- Click **Go to Google Cloud** and sign in with your Google Cloud account credentials.
- Enter the name of your **Quarantine Bucket**. If you don’t have a Quarantine Bucket configured yet, follow the instructions in [Step B](/zia/adding-saas-application-tenants#GCBucket).
- []Click **Save** to finish.
- [][]From your [Google Cloud Platform console](https://console.cloud.google.com/), click on **Cloud Storage**, and then click **Create Bucket**.
- Name the bucket and click **Continue**.
- Continue configuring the bucket as needed and click **Create** when finished.
[See image.](#GCP_08)
- Return to [Section a., Step iii](/zia/adding-saas-application-tenants#GCConfigiii).
[]The following tasks have to be performed by an Organization Administrator of the G Suite domain:
- Copy the Zscaler Saas Connector ID.
- Go to G Suite domain’s [Admin console](http://admin.google.com/).
- Select **Security** > **Access and data control** > **API controls**.
[See image.](#GCP_10_Security)
- Select **Manage Domain Wide Delegation**.
- If the Zscaler API client isn't listed, select **Add new**.
- In the **Client name** field enter the Zscaler Saas Connector ID you copied earlier.
[See image.](#GCP_11_Authorize)
- In the **OAuth scopes** field, enter the list of scopes that your application should be granted access to (copy from following list):
https://www.googleapis.com/auth/cloud-platform,https://www.googleapis.com/auth/devstorage.full_control,https://www.googleapis.com/auth/logging.read,https://www.googleapis.com/auth/admin.directory.user,https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/logging.admin
- Click **Authorize**.
- []Sign in to the [Google Cloud Platform console](http://console.cloud.google.com).
- Navigate into the desired organization using the project selection drop-down menu and select the appropriate domain in the listing.
[See image.](#GCP_12_Domain)
Organization Administrator should be granted **Members** permissions for your GCP organization.
- Go to **IAM & Admin** > **IAM** on the navigation bar.
- Select **Add**.
- Paste the Organization Administrator email address in the **New principals** field.
[See image.](#GCP_13_Add)
- Select the following roles necessary for complete cloud storage visibility/harvesting:
- **Browser** (roles/browser): Read access to browse the hierarchy for a project and IAM policy. This role doesn't include permission to view resources in the project.
- **Private Logs Viewer**: To view data access logs.
- **Storage Admin **(roles/storage.admin): Grants full control of objects and buckets.
- Click **Save**.
[]To access audit log configuration options in the Cloud Console, follow these steps:
- Go to the [Audit Logs page](https://console.cloud.google.com/iam-admin/audit).
- In the main table on the **Audit Logs** page, select one or more Google Cloud services from the **Title** column.
- In the **Log Type** tab, select the boxes by the Data Access audit log types that you want to enable and then click **Save**. Where you have successfully enabled audit logs, the table includes a checkmark.
[See image.](#GCP_14_LogType)
- Select **Cloud Logging API** and **Google Cloud Storage**, and enable **Admin Read**, **Data Write**, and **Data Read** audit logs.
Why should you enable the above operations?
- **Admin Read**: Entries for operations that read the configuration or metadata of a project, bucket, or object.
- **Data Read**: Entries for operations that read an object.
- **Data Write**: Entries for operations that create or modify an object.
- []From [Google Cloud Platform](https://console.cloud.google.com), go to **APIs & Services** > **Enabled APIs & services**. Ensure that for all the projects for the organization the Cloud Storage JSON API is activated. The JSON API is activated by default, and it can be used immediately.
- To enable the JSON API in an existing project, go to the [Google Cloud Storage JSON API](https://console.cloud.google.com/apis/library/storage-api.googleapis.com?_ga=2.14485175.1820178154.1590745287-1130016693.1577430858&_gac=1.195830040.1590495027.EAIaIQobChMI0Naek4bP6QIVQT5gCh2BvQEBEAAYASAAEgIqhfD_BwE) page in the Cloud Console API Library, and click the **Enable** button.
[]To create a custom Google Cloud Connector, you must first configure permissions in Google so that you can provide the **Organization ID**, **Quarantine Bucket** name, and **Private Key JSON** file for the Google Cloud Platform account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![Choose how to protect object data.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_08_choose_protect.png)
[]![API sub-section under Security.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_10_Security_google_admin_api_controls.png)
[]![Scope authorization window.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_11_Oauth_scopes_Authorize.png)
[]![Select domain from available list.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_12_Domain_select_from.png)
[]![Add principals and roles for resources.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_13_Add_principals.png)
[]![Audit Log Type window.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/GCP_14_LogType_2_services.png)
[]To configure Google Drive:
- [Zscaler Defined](#zd_gdrive)
- [Custom](#custom_gdrive)
- []Enter your **Google Admin Email ID**.
- []Under **Authorize the SaaS Application**, click **Zscaler Defined**, and copy the **Zscaler SaaS Connector** and **Google Workspace Scope**. You need it for [a later step](#gdrivestep-i) when adding an API client for Google Workspace.
[See image.](#seeimagegdrive-b)
- Click **Go to Google Workspace**.
The Google Workspace portal appears.
- Log in to Google Workspace.
You are redirected to the Google Admin console.
- Go to **Security**.
[See image.](#seeimagegdrive-e)
- Click **API controls**.
[See image.](#seeimagegdrive-f)
- Under **Domain wide delegation**, click **MANAGE DOMAIN WIDE DELEGATION**.
[See image.](#seeimagegdrive-g)
- Click **Add new**.
[See image.](#seeimagegdrive-h)
The **Add a new client ID** window appears.
- []In the **Add a new client ID** window:
- **Client ID**: Enter Zscaler SaaS Connector value you copied in [a previous step](#gdrivestep-b).
- **Overwrite existing client ID**: Deselect.
- **OAuth scopes (comma-delimited)**: Enter the Google Workspace scope you copied in [a previous step](#gdrivestep-b).
[See image.](#seeimagegdrive-i)
- Click **Authorize**.
The Zscaler Connector App is added as an API client.
To learn more about the steps in the Google Admin console, refer to the [Google documentation](https://support.google.com/a/?hl=en#topic=4388346).
[]To create a custom Google Drive Connector, you must first configure permissions in Google so that you can provide the **Private Key JSON** file for the Google Drive account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![Screenshot of the Copy buttons for Zscaler SaaS Connector and Google Workspace Scope in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Copy-Google-Drive-6_1.png)
[]![Screenshot highlighting the Security menu in the Google Admin console.](/downloads/zia/adding-saas-application-tenants/Google-Security-menu-6_1.png)
[]![Screenshot of the API controls option in Security.](/downloads/zia/adding-saas-application-tenants/Google-API-controls.png)
[]![Screenshot highlighting the MANAGE DOMAIN WIDE DELEGATION button in the Domain wide delegation section.](/downloads/zia/adding-saas-application-tenants/Google-Manage-Domain-wide-delegation-button.png)
[]![Screenshot highlighting the Add new button for API clients.](/downloads/zia/adding-saas-application-tenants/Google-API-clients-Add-new-button.png)
[]![Screenshot of the configured Add a new client ID window.](/downloads/zia/adding-saas-application-tenants/Google-Add-new-client-ID-window-6_1.png)
[]To configure Google Workspace:
- [Zscaler Defined](#zd_workspace)
- [Custom](#custom_workspace)
- []Enter the **Google Admin Email ID**.
- []Under **Authorize the SaaS Application**, click **Zscaler Defined**, and copy the **Zscaler SaaS Connector** and **Google Workspace Scope**. You need it for a later step when adding an API client for Google Workspace.
[See image.](#seeimagegworkspace-b3)
- Click **Go to Google Workspace**.
The Google Workspace portal appears.
- Log in to Google Workspace.
You are redirected to the Google Admin console.
- Go to **Security**.
[See image.](#seeimagegworkspace-e)
- Click **API controls**.
[See image.](#seeimagegworkspace-f)
- Under **Domain wide delegation**, click **MANAGE DOMAIN WIDE DELEGATION**.
[See image.](#seeimagegworkspace-g)
- Click **Add new**.
[See image.](#seeimagegworkspace-h)
The **Add a new client ID** window appears.
- In the **Add a new client ID** window:
- **Client ID**: Enter Zscaler SaaS Connector value you copied in [a previous step](#gworkspacestep-b).
- **Overwrite existing client ID**: Deselect.
- **OAuth scopes (comma-delimited)**: Enter the Google Workspace scope you copied in [a previous step](#gworkspacestep-b).
[See image.](#seeimagegworkspace-i)
- Click **Authorize**.
The Zscaler Connector App is added as an API client.
To learn more about the steps in the Google Admin console, refer to the [Google documentation](https://support.google.com/a/?hl=en#topic=4388346).
[]To create a custom Google Workspace Connector, you must first configure permissions in Google so that you can provide the **Private Key JSON** file for the Google Drive account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Google Applications](/zia/authorizing-custom-zscaler-connector-google-applications).
[]![Screenshot of the Copy buttons for Zscaler SaaS Connector and Google Workspace Scope in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Copy-Google-Workspace.png)
[]![Screenshot highlighting the Security menu in the Google Admin console.](/downloads/zia/adding-saas-application-tenants/Google-Security-menu-6_1.png)
[]![Screenshot of the API controls option in Security.](/downloads/zia/adding-saas-application-tenants/Google-API-controls.png)
[]![Screenshot highlighting the MANAGE DOMAIN WIDE DELEGATION button in the Domain wide delegation section.](/downloads/zia/adding-saas-application-tenants/Google-Manage-Domain-wide-delegation-button.png)
[]![Screenshot highlighting the Add new button for API clients.](/downloads/zia/adding-saas-application-tenants/Google-API-clients-Add-new-button.png)
[]![Screenshot of the configured Add a new client ID window.](/downloads/zia/adding-saas-application-tenants/Google-Add-new-client-ID-window-6_1.png)
[]To configure Google Workspace Marketplace:
- []Under **Authorize the SaaS Application**, copy the **Zscaler SaaS Connector** and **Google Workspace Scope**. You need it for [a later step.](#gmarketspacestep-i) when adding an API client for Google Workspace.
[See image.](#seeimagegworkspace-b2)
- Click **Go to Google Workspace**.
[See image.](#seeimagegworkspace-c2)
The Google Workspace portal appears.
- Log in to Google Workspace.
You are redirected to the Google Admin console.
- Go to **Security**.
[See image.](#seeimagegworkspace-e2)
- Click **API controls**.
[See image.](#seeimagegworkspace-f2)
- Under **Domain wide delegation**, click **MANAGE DOMAIN WIDE DELEGATION**.
[See image.](#seeimagegworkspace-g2)
- Click **Add new**.
[See image.](#seeimagegworkspace-h2)
The **Add a new client ID** window appears.
- []In the **Add a new client ID** window:
- **Client ID**: Enter Zscaler SaaS Connector value you copied in [a previous step](#gmarket-a).
- **Overwrite existing client ID**: Deselect.
- **OAuth scopes (comma-delimited)**: Enter the Google Workspace scope you copied in [a previous step](#gmarket-a).
[See image.](#seeimagegworkspace-i2)
- Click **Authorize**.
The Zscaler Connector App is added as an API client.
- In the ZIA Admin Portal, under **Enter the Google Admin Email ID**, enter your admin email ID used to log in to the Google Admin console.
[See image.](#seeimagegworkspace-k2)
To learn more about the steps in the Google Admin console, refer to the [Google documentation](https://support.google.com/a/?hl=en#topic=4388346).
[]![Screenshot of the Copy buttons for Zscaler SaaS Connector and Google Workspace Scope in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Copy-Google-Workspace.png)
[]![Screenshot highlighting the Go to Google Workspace button under the Authorize the SaaS Application.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Go-to-Google-Workspace-Google-Workspace.png)
[]![Screenshot highlighting the Security menu in the Google Admin console.](/downloads/zia/adding-saas-application-tenants/Google-Security-menu-6_1.png)
[]![Screenshot of the API controls option in Security.](/downloads/zia/adding-saas-application-tenants/Google-API-controls.png)
[]![Screenshot highlighting the MANAGE DOMAIN WIDE DELEGATION button in the Domain wide delegation section.](/downloads/zia/adding-saas-application-tenants/Google-Manage-Domain-wide-delegation-button.png)
[]![Screenshot highlighting the Add new button for API clients.](/downloads/zia/adding-saas-application-tenants/Google-API-clients-Add-new-button.png)
[]![Screenshot of the configured Add a new client ID window.](/downloads/zia/adding-saas-application-tenants/Google-Add-new-client-ID-window-6_1.png)
[]![Screenshot of the Google Admin Email ID field in the Enter the Google Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-Google-Admin-Email-ID.png)
[]To configure Jira Software:
- Enter the **Atlassian Domain Address** you want to connect with Zscaler.
[See image.](#jira01)
- Enter your **Jira Organization API Key**. For help finding your API Key, follow the instructions on [Atlassian Support](https://support.atlassian.com/organization-administration/docs/manage-an-organization-with-the-admin-apis/).
[See image.](#jira02)
- Click **Provide Admin Credentials** and sign in to your Jira account.
- Click **Save**.
[]![Enter Atlassian Domain Address.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Jira%20Atlassian.png)
[]![Enter Jira API Key.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Jira02_APIKey.png)
[]To configure Microsoft 365:
-
Under **Authorize the SaaS Application**, copy the SaaS connector ID.
[See image.](#M365Authorize)
- On a new browser tab, log in to the [Azure Portal](https://portal.azure.com/) with your Global Administrator account.
-
On the Azure Portal home page, search for the **Microsoft Entra roles and administrators **service and click that entry in the drop-down list.
[See image.](#M365-azure-roles)
-
On the** All Roles** page, search for** Exchange Administrator**, then click that entry to open it.
[See image.](#M365-azure-assignments)
-
On the **Exchange Administrator | Assignments** page, click **Add assignments**.
[See image.](#M365-azure-add-assignment)
-
On the **Add Assignments** page, click the **No member selected** link.
[See image.](#M365-azure-link)
-
On the **Select a member** page, paste the SaaS connector ID you copied in step c. Select the SaaS connector ID in the list below and click **Select **at the bottom of the screen.
[See image.](#M365-azure-select-member)
-
The **Add Assignments** page appears for the selected SaaS connector ID. Click **Next **at the bottom of the screen. On the following screen, provide a justification for this assignment and click **Assign**.
[See image.](#M365-azure-assignment-justify)
-
On the **Exchange Administrator | Assignments** page, verify that the SaaS connector ID you just added appears in the list of active assignments.
[See image.](#M365-azure-assignments-active)
-
Return to the **Add SaaS Application Tenant** page in the ZIA Admin Portal and click **Provide Admin Credentials** to add the tenant ID.
[See image.](#M365Reauthorize)
[][![Provide Microsoft account information to authorize the SaaS application.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/authorize-saas-app-O365.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/authorize-saas-app-O365.png)
[][![Select the Microsoft Entra roles and administrators service.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-roles-O365.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-roles-O365.png)
[][![Select the Exchange Administrator role.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-exchange-admin-O365.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-exchange-admin-O365.png)
[][![Click the Add Assignments button to add a new assignment.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignments.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignments.png)
[][![Click the link to add a new member.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-assign.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-assign.png)
[][![Paste the SaaS Connector ID in the search box.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-select-member.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-select-member.png)
[][![Enter a justification for this assignment.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignment-justify.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignment-justify.png)
[][![Verify the SaaS Connector ID is in the list of active assignments.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignments-active.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/azure-add-assignments-active.png)
[][![Select the SaaS connector ID.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/reauthorize-saas-app-O365.png)
](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/reauthorize-saas-app-O365.png)
[]To enable Microsoft Azure for your organization, contact your Zscaler Account team. To learn more about configuring Azure or for help finding your enterprise ID or storage account name, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/?product=popular).
- [Zscaler Defined](#configure-MS-Azure)
- [Custom](#azure-blob-custom)
[]
- [Configure Microsoft Azure](#azure-blob-zscaler-defined)
- [Create and Assign Roles](#MSARoles)
[]
-
Under **Authorize the SaaS Application**, select the checkbox for the functionality you want to enable.
[See image.](#azure-dlp)
- Click **Provide Admin Credentials**, and sign in with your Microsoft Azure account credentials.
- Under **Register the SaaS Application**:
- Enter your Microsoft Azure **Enterprise ID**.
- Enter the name of your **Quarantine Storage Account**.
- Click **Save** to finish.
[See image.](#Azure_01)
[]To create a custom Microsoft Azure Blob Storage Connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID**, and add **Role Assignments** for the Microsoft Azure Blob Storage account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
- []Copy the **Zscaler SaaS Connector ID**.
[See image.](#Azure_02)
- Log in to the [Azure Portal](https://portal.azure.com/) with your Global Administrator account. Go to **Azure Active Directory **> **Enterprise Application**.
- Copy the Application name matching the ID in Step a.
[See image.](#Azure_03)
- Go back to the Azure Portal home page, then go to **Subscriptions** and select your subscription. You must do this for each of your subscriptions.
[See image.](#Azure_04)
- Select **Access Control (IAM)** > **Role Assignments** > **Add **> **Add role assignment**.
[See image.](#Azure_05)
- Search "**Storage Contributor**". Select **Storage Blob Data Contributor** and **Storage Account Contributor** and then click **Next **(this must be done separately for each role).
- Click **Select members** and add the application name from Step c as a member to **Storage Blob Data Contributor** and **Storage Account Contributor**, then select **Review + assign**.
[See image.](#Azure_06)
Steps f and g must be done separately for both the **Storage Blob Data Contributor** and **Storage Account Contributor** roles. Steps d to g must be repeated for all subscriptions.
[]![authorize-saas-app-azure-blob.png](/downloads/zia/adding-saas-application-tenants/authorize-saas-app-azure-blob.png)
[]![Register the SaaS Application.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_00.3_register_saas.png)
![Authorize the SaaS Application.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_002_authorize.png)
[]
[]![Application ID](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_003_beta_connector.png)
[]![Subscriptions page.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_09_Subscriptions.png)
[]![Add role to subscription.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_071_add_access_control.png)
[]![Add role assignment.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Azure_08_add_role_assignment.png)
[]To configure Microsoft Copilot:
Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#Exchange-saas-connector-knob)
- [Zscaler Defined](#Zscaler-Defined-Copilot)
- [Custom](#Custom-Copilot)
[]
- Click **Provide Admin Credentials**.
The Azure portal appears.
- Log in to Azure.
- Review the required permissions for the ZIA service to access the Copilot account and click **Accept**.
- []After accepting, you return to ZIA and your **Zscaler SaaS Connector** and **Tenant ID** information is visible. Copy these for use later.
-
To complete the app registration for Copilot, run the following script in Azure via Power Platform API or PowerShell for Power Platform administrators. Use the **Zscaler Connector ID** you [copied earlier](#connector):
`$appId = "<Zscaler Connector ID>"
# Login interactively with a tenant administrator for Power Platform
Add-PowerAppsAccount -Endpoint prod -TenantID $tenantId
# Register a new application, this gives the SPN/client application the same permissions
New-PowerAppManagementApp -ApplicationId $appId`
[]
To create a custom Copilot connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
[]To configure Microsoft Exchange:
- Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#Exchange-saas-connector-knob)
- [Zscaler Defined](#Zscaler-Defined-Exchange)
- [Custom](#Custom-Exchange)
-
(Optional) In the ZIA Admin Portal, under **(Optional) Configure External Trusted Domains & Users for the Tenant**:
- **External Trusted Domains**: Enter trusted email domains that are outside your organization (i.e., using a different domain). The Zscaler service views any email addresses from the added domains as trusted, internal users for Exchange. For example, if your organization's domain is safemarch.com and your organization recently acquired a company with the domain example.com, you can add example.com to this list, and the service treats any email addresses from example.com (e.g., johnsmith@example.com) as internal users from safemarch.com. You can add up to 1,000 domains.
- **External Trusted Users**: Enter trusted email addresses that are outside your organization (i.e., using a different email domain). The Zscaler service views the email addresses as trusted, internal users for Exchange. For example, if your organization's email domain is safemarch.com and your organization recently contracted with someone using an external email domain (e.g., johnsmith@example.com), you can add the contractor's email to this list, and the service treats the contractor as an internal user from safemarch.com. You can add up to 1,000 email addresses.
[See image.](#seeimageexchange-e)
[]
- Click **Provide Admin Credentials**.
The Exchange Portal appears.
- Log in to Exchange.
- Review the required permissions for the ZIA service to access the Exchange account and click **Accept**.
[]
To create a custom Exchange connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the Exchange account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
[]![The SaaS Connector option in the Authorize the SaaS Application section.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/ZIA-SaaSAppTenants-Exchange-ZscalerDefinedConnector.png)
[]![Screenshot of the (Optional) Configure External Trusted Domains & Users for the Tenant section.](/downloads/zia/adding-saas-application-tenants/zia-optional-configure-external-trusted-domains-users-tenant-exchange-6_1.png)
[]To configure Microsoft OneDrive:
Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#OneDrive-saas-connector-knob)
- [Zscaler Defined](#Zscaler-Defined-OneDrive)
- [Custom](#Custom-OneDrive)
[]
- Click **Provide Admin Credentials**.
The OneDrive portal appears.
- Log in to OneDrive.
- Review the required permissions for the Zscaler service to access OneDrive, and click **Accept**.
[]
To create a custom OneDrive connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the OneDrive account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
[]![The SaaS Connector option in the Authorize the SaaS Application section.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/ZIA-SaaSAppTenants-OneDrive-ZscalerDefinedConnector.png)
[]
Zscaler and Microsoft are technology partners. To learn more about the Zscaler and Microsoft Sharepoint integration, see the [Zscaler and Microsoft Sharepoint Online Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-sharepoint-online-deployment-guide).
To configure Microsoft SharePoint:
Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#SharePoint-saas-connector-knob)
- [Zscaler Defined](#Zscaler-Defined-SharePoint)
- [Custom](#Custom-SharePoint)
[]
- Click **Provide Admin Credentials**.
The SharePoint portal appears.
- Log in to SharePoint.
- Review the required permissions for the Zscaler service to access SharePoint, and click **Accept**.
[]
To create a custom SharePoint connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the SharePoint account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
[]![The SaaS Connector option in the Authorize the SaaS Application section.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/ZIA-SaaSAppTenants-SharePoint-ZscalerDefinedConnector.png)
[]To configure Microsoft Teams:
- If you select **Workflow Automation**, an additional step appears to **Configure Microsoft Teams Bot**.
-
Click **Download Zip File** to download the bot’s AppBundle ZIP file, and then name the bot. The name must be identical to its name in the Teams App overview after the upload. By default, the name is `ZCN`. All other names lead to a 401 error while validating.
[See image.](#MSTeams_down)
-
In the ZIP file, open the **manifest.json** file in a text editor and replace the three `id` values with your **Zscaler Connector ID** found under the next step in the UI: **Authorize the SaaS Application**. Save the changes to the **manifest.json** file.
[See image.](#MSTeams_id)
-
Go to Microsoft Teams and navigate to **Apps** > **Manage your apps** > **Upload an app**.
[See image.](#MSTeams_upload)
-
Click **Upload a custom app**, select your AppBundle ZIP file, then return to the **Add SaaS Application Tenant** page in the ZIA Admin Portal. To learn more about packaging or uploading your Microsoft Teams Bot, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload#upload-your-app).
Microsoft deprecated multi-tenant bot creation for Teams on July 31, 2025. Existing multi-tenant bots are supported as usual. For new bots, use single-tenant or user-assigned managed identity only.
- Under **Authorize the SaaS Application**, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
[See image.](#msteams-saas-connector-knob)
- [Zscaler Defined](#Zscaler-Defined-ms-teams)
- [Custom](#Custom-ms-teams)
[]
- Click **Provide Admin Credentials**.
The Teams Portal appears.
- Log in to Teams.
- Review the required permissions for the ZIA service to access the Microsoft account and click **Accept**.
[]
To create a custom Teams connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the Teams account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/zia/authorizing-custom-zscaler-connector-microsoft-applications).
[]![The SaaS Connector option in the Authorize the SaaS Application section.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/ZIA-SaaSAppTenants-MS-Teams-ZscalerDefinedConnector.png)
[]![Name bot and download ZIP file](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/MSTeams-bot.png)
[]![Zscaler Connector ID](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/MSTeams_JSON_ID.png)
[]![Navigate to uploading an app in MS Teams](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/MSTeams-upload-app.png)
[]
Zscaler and Okta are technology partners. To learn more about the Zscaler and Okta integration, see the [Zscaler and Okta Deployment Guide](/zscaler-technology-partners/zscaler-and-okta-deployment-guide).
To configure Okta:
- []Under **Register the OAuth Application**, enter your Okta client ID and client secret that you copied (learn more in [Step f](#Okta_stepi)), as well as the URL used to login to your admin account in Okta.
[See image.](#okta-oauth)
- Under **Enter Okta Admin Email ID**, enter your admin email ID used to log in to Okta portal.
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials**.
- Click **Save**.
Create and configure an Okta App Integration:
- From the Okta admin console, go to **Applications** > **Applications** and then select **Create App Integration**.
[See image.](#Okta_Apps)
- Select **OIDC - OpenID Connect** for the sign-in method and **Web Application** for the application type.
[See image.](#Okta_signin)
- Click **Next**.
- Enter a name for the app integration, select **Authorization Code** and **Refresh Token** for grant types, and enter `https://admin.``<Zscaler Cloud Name>``.net` for the sign-in and sign-out URIs, where the cloud name is the ZIA cloud where you are hosted. In the following example we are using `https://admin.zscaler.net`.
[See image.](#Okta_general)
- Under **Assignments**, select **Allow everyone in your organization to access for controlled access** and click **Save**.
[See image.](#Okta_assignments)
- []In the **General** tab of the application you created, copy the Client ID and Secret for use in the previous section's [Step b](#Okta_stepID).
[See image.](#okta_id)
- In the **Okta API Scopes**, grant access to the following scopes:
- okta.apiTokens.read
- okta.apps.read
- okta.behaviors.read
- okta.clients.read
- okta.domains.read
- okta.events.read
- okta.factors.read
- okta.groups.read
- okta.linkedObjects.read
- okta.logs.read
- okta.networkZones.read
- okta.policies.manage
- okta.policies.read
- okta.reports.read
- okta.riskProviders.read
- okta.roles.manage
- okta.roles.read
- okta.sessions.read
- okta.threatInsights.manage
- okta.threatInsights.read
- okta.trustedOrigins.read
- okta.userTypes.read
- okta.users.read
[See image.](#Okta_api)
To learn more about the steps in Okta, refer to the [Okta documentation](https://support.okta.com/).
[]![Enter OAuth Application information](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Okta%20tennant01_01.png)
[]![Okta Applications menu](/downloads/zia/adding-saas-application-tenants/saas_okta_01_createapp.png)
[]![Okta app integration sign-in method and application type](/downloads/zia/adding-saas-application-tenants/saas_okta_02_appintegration.png)
[]![Okta app integration general settings](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/saas_okta_03_nameURI02_0.png)
[]![Okta app assignments](/downloads/zia/adding-saas-application-tenants/saas_okta_04_assignments.png)
[]![Okta API Scopes](/downloads/zia/adding-saas-application-tenants/saas_okta_05_oktascope.png)
[]![Okta application Client ID and Secret](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/saas_okta_06_id2.png)
[]Zscaler and Salesforce are technology partners. To learn more about the Zscaler and Salesforce integration, see the [Zscaler and Salesforce Deployment Guide](/zscaler-technology-partners/zscaler-and-salesforce-deployment-guide).
- [Zscaler Defined](#zd_sf)
- [Custom](#custom_sf)
[]
To configure Salesforce:
To view the activity report logs for Salesforce, ensure that you have access to the Event Monitoring add-on on your Enterprise or Unlimited Salesforce license.
- [a. Install the zscalerPackage](#salesforce-install-zpackage)
- [b. Create a user with system administrator profile and Salesforce license.](#sf_profile)
- [c. Create a Permission Set](#salesforce-create-permission-set)
- [d. Assign the Permission Set](#salesforce-assign-permission-set)
- [e. Configure the Salesforce CRM Content Settings](#salesforce-crm-content-settings)
- [f. Configure the Zscaler SaaS Connector Application](#salesforce-configure-connector-app)
To learn more about the steps in Salesforce, refer to the [Salesforce documentation](https://help.salesforce.com/).
[]You must install the zscalerPackage, which contains the contents for the Zscaler SaaS Connector application.
- Under **Select Tenant Type**, choose the appropriate tenant type based on your deployment:
- **Sandbox Account**: This option allows you to access Salesforce from the [test.salesforce.com](http://test.salesforce.com) URL where you can test your changes without having them affecting your customers until you move it to your production environment.
- **Production Account**: This option allows you to access Salesforce from the [login.salesforce.com](login.salesforce.com) URL where your changes affect your customers directly as they are applied to your production environment.
You can add both tenant types separately, but you can't change from a sandbox tenant type to production, or from production to sandbox.
[See image.](#SFTenantType)
- Under **Authorize the SaaS Application**, click **Go to Salesforce**.
[See image.](#seeimagesalesforce-aii)
The Salesforce portal appears.
- Log in to Salesforce.
The **Install zscalerPackage** page appears.
- On the **Install zscalerPackage** page:
- Ensure **Install for Admins Only **is selected.
- Select **I acknowledge that I’m installing a Non-Salesforce Application that is not authorized for distribution as part of Salesforce’s AppExchange Partner Program**.
- Click **Install**.
[See image.](#seeimagesalesforce-aiv)
- After installation is complete, click **Done**.
[See image.](#seeimagesalesforce-av)
You are redirected to the **Installed Packages** page.
[][![Select between Sandbox and Production tenant types.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Salesforce_S1.%20Salesforce%20tenant%20type_0.png)
]
[]![Screenshot highlighting the Go to Salesforce button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Go-to-Salesforce.png)
[]![Screenshot of the Install zscalerPackage configuration.](/downloads/zia/adding-saas-application-tenants/Salesforce-Install-zscalerPackage-page.png)
[]![Screenshot highlightingthe Done button on the Install zscalerPackage page.](/downloads/zia/adding-saas-application-tenants/Salesforce-Install-zscalerPackage-Done-button.png)
If the integration user already has a System Administrator Profile, copy and save the username and skip to Step C.
-
[]In the left-side navigation, go to **Users**.
[See image.](#sf_user)
-
[]Select **New User** and enter the required general information. For **User License** select **Salesforce**, for **Profile** select **System Administrator**, and click the checkbox for **Salesforce CRM Content User**.
[See image.](#sf_general)
-
Click the checkbox for **Generate new password and notify user immediately**.
[See image.](#sf_approver)
- Click the **Save** button.
- You will receive a verification email from Salesforce at the address you entered in [Step 2](#sf_step2). Follow the instructions in the email and set a new password for the user.
[]![Select Users from the left-side navigation](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/sf_new%20user.png)
[]![Enter required information into the General Information section](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/sf_general.png)
[]![Generate new password and notify user immediately checkbox in the Approver Settings section](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/sf_approver.png)
[]You must create a permission set to assign to your user account and the Zscaler SaaS Connector application.
To create a permission set:
- In the left-side navigation, go to **Users** > **Permission Sets**.
[See image.](#seeimagesalesforce-bi)
- Click **New**.
[See image.](#seeimagesalesforce-bii)
The **Permission Set Create** window appears.
- In the **Permission Set Create** window:
- **Label**: Enter a label for the permission set. In this example, it's Zscaler SaaS Connector User.
- **API Name**: This field populates based on the label you entered.
- **License**: Choose **Salesforce**.
[See image.](#seeimagesalesforce-biii)
- Click **Save**.
- In the **Apps **section, click **App Permissions**.
[See image.](#seeimagesalesforce-bv)
- Click **Edit**.
[See image.](#seeimagesalesforce-bvi)
- In the **Content** section, select the following permissions:
- **Manage record types and layouts for Files**
- **Manage Salesforce CRM Content**
- **Query All Files**
[See image.](#seeimagesalesforce-bvii)
- Click **Save** and then **Save** again to confirm.
[]![Screenshot highlighting the Permission Sets menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-menu.png)
[]![Screenshot highlighting the New button on the Permission Sets page.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-New-button.png)
[]![Screenshot of the configured Permission Set Create window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Set-Create-window.png)
[]![Screenshot highlighting the App Permissions option in the Apps section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Zscaler-SaaS-Connector-User-App-Permissions-Setting.png)
[]![Screenshot highlighting the Edit button for App Permissions.](/downloads/zia/adding-saas-application-tenants/Salesforce-App-Permissions-Edit-button.png)
[]![Screenshot of the selected permissions in the Content section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Sets-Content-section.png)
[]You must assign the permission set you created to your Salesforce user account.
To assign the permission set to your user account:
- In the left-side navigation, go to **Users** > **Users**.
[See image.](#seeimagesalesforce-ci)
- In the **Full Name** column, click your name.
[See image.](#seeimagesalesforce-cii)
- In the **User Details** section, select **Salesforce CRM Content User**.
[See image.](#seeimagesalesforce-ciii)
- In the **Permission Set Assignments **section, click **Edit Assignments**.
[See image.](#seeimagesalesforce-civ)
The **Permission Sets** window appears.
- In the **Permission Sets** window, under **Available Permission Sets**, select the permission set you configured in [Step b](#salesforce-create-permission-set), and click **Add**. In this example, it's Zscaler SaaS Connector User.
[See image.](#seeimagesalesforce-cv)
- Click **Save**.
[]![Screenshot highlighting the Users menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-Users-Menu.png)
[]![Screenshot highlighting the name of the user in the Full Name column.](/downloads/zia/adding-saas-application-tenants/Salesforce-All-Users-Full-Name-Column.png)
[]![The Salsforce CRM Content User option in the User Details section.](/downloads/zia/adding-saas-application-tenants/Salesforce-User-Details-Salesforce-CRM-Content-User.png)
[]![Screenshot highlighting the Edit Assignments button in the Permission Set Assignments section.](/downloads/zia/adding-saas-application-tenants/Salesforce-Permission-Set-Assignments.png)
[]![Screenshot of the Zscaler SaaS Connector User permission set added in the Enabled Permission Sets section.](/downloads/zia/adding-saas-application-tenants/Salesforce-User-Permission-Set-Assignments.png)
[]To configure the Salesforce CRM Content settings:
- In the left-side navigation, go to **Feature Settings** > **Salesforce Files** > **Salesforce CRM Content**.
[See image.](#seeimagesalesforce-di)
- Select the following Salesforce CRM Content settings:
- **Enable Salesforce CRM Content**
- **Autoassign feature licenses to existing and new users**
- **Files user interface allows sharing files with libraries**
[See image.](#seeimagesalesforce-dii)
- Click **Save**.
[]![The Salesforce CRM Content menu.](/downloads/zia/adding-saas-application-tenants/Salesforce-CRM-Content-Menu.png)
[]![The configured settings on the Salesforce CRM Content page](/downloads/zia/adding-saas-application-tenants/Salesforce-CRM-Content-Page.png)
[]To configure the Zscaler SaaS Connector application:
- In the left-side navigation, go to **Apps** > **App Manager**.
[See image.](#seeimagesalesforce-ei)
- Click the down arrow icon for the Zscaler SaaS Connector application. The name of the Zscaler SaaS Connector application varies depending on the URL you use to log in to the Zscaler service. For example, if you log in to https://admin.zscalerbeta.net, then your Zscaler SaaS Connector application name is similar to ZscalerSaaSConnectorZSBeta01. This guide uses the ZscalerSaaSConnectorZSBeta01 application as an example.
[See image.](#seeimagesalesforce-eii)
- Click **Manage**.
[See image.](#seeimagesalesforce-eiii)
- Click **Edit Policies**.
[See image.](#seeimagesalesforce-eiv)
The **Connected App Edit** window appears.
- In the **Connected App Edit** window:
- **Permitted Users**: Choose **Admin approved users are pre-authorized**.
- **IP Relaxation**: Choose **Relax IP restrictions**.
- **Refresh Token Policy**: Ensure **Refresh token is valid until revoked** is chosen.
[See image.](#seeimagesalesforce-ev)
- Click **Save**.
- In the **Profiles **section, click **Manage Profiles**.
[See image.](#seeimagesalesforce-evii)
The **Application Profile Assignment** window appears.
- In the **Application Profile Assignment** window, select **System Administrator**.
[See image.](#seeimagesalesforce-eviii)
- Click **Save**.
- In the **Permission Sets **section, click **Manage Permission Sets**.
[See image.](#seeimagesalesforce-ex)
The **Application Permission Set Assignment** window appears.
- In the **Application Permission Set Assignment** window, select the permission set you configured in [Step b](#salesforce-create-permission-set). In this example, it's Zscaler SaaS Connector User.
[See image.](#seeimagesalesforce-exi)
- Click **Save**.
- In the ZIA Admin Portal, under **Enter the Salesforce Admin Username**, enter your admin username used to log in to the Salesforce portal.
[See image.](#seeimagesalesforce-exiii)
[]![Screenshot highlighting the App Manager menu](/downloads/zia/adding-saas-application-tenants/Salesforce-App-Manager-menu.png)
[]![Screenshot highlighting the down arrow icon for ZscalerSaaSConnectorZSBeta01.](/downloads/zia/adding-saas-application-tenants/Salesforce-Lightning-Experience-App-Manager-Down-Arrow-Icon.png)
[]![Screenshot of the Manage option for ZscalerSaaSConnectorZSBeta01.](/downloads/zia/adding-saas-application-tenants/Salesforce-Manage-Option.png)
[]![Screenshot highlighting the Edit Policies button on the App Manager page.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Edit-Policies.png)
[]![Screenshot of the configured Connected App Edit window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Connected-App-Edit-window.png)
[]![Screenshot highlighting the Manage Profiles button in the Profiles section.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Manage-Profiles.png)
[]![Screenshot highlighting the System Administrator profile in the Application Profile Assignment window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Application-Profile-Asssignment-System-Administrator.png)
[]![Screenshot highlighting the Manage Permission Sets button in the Permission Sets section.](/downloads/zia/adding-saas-application-tenants/Salesforce-ZscalerSaaSConnector-Manage-Permission-Sets.png)
[]![Screenshot of the Zscaler SaaS Connector User permission set in the Application Permission Set Assignment window.](/downloads/zia/adding-saas-application-tenants/Salesforce-Application-Permission-Set-Asssignment-window.png)
[]![Enter the Salesforce Admin Username](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/SalesForce_Admin%20Username.png)
[]To create a custom Salesforce Connector, you must first configure permissions in Salesforce so that you can provide the client ID, client secret, username of integration user, instance URL, and quarantine library names (if using DLP and Malware scanning) for the Salesforce account in the ZIA Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Salesforce](/zia/authorizing-custom-zscaler-connector-salesforce).
[]
Zscaler and ServiceNow are technology partners. To learn more about the Zscaler and ServiceNow integration, see the [Zscaler and ServiceNow Deployment Guide](/zscaler-technology-partners/zscaler-and-servicenow-deployment-guide).
To configure ServiceNow as a tenant, you must have a ServiceNow user account with an admin role.
To configure ServiceNow:
- [a. Verify the OAuth 2.0 Plugin is Active](#verify-oauth-plugin-active)
- [b. Verify the OAuth Property is Active](#verify-oauth-property-active)
- [c. Configure an OAuth Client Application](#configure-oauth-application)
- [d. Add ServiceNow as a Tenant](#add-servicenow-tenant)
To learn more about the steps in ServiceNow, refer to the [ServiceNow documentation](https://docs.servicenow.com/).
To learn more about adding additional object types for ServiceNow tenants, see [Adding Object Types for ServiceNow Tenants](/zia/adding-object-types-servicenow-tenants).
[]To verify the the OAuth 2.0 plugin is installed and active:
- Log in to your ServiceNow instance.
-
Go to **System Application** > **All Available Applications** > **All**.
[See image.](#seeimageservicenow-aii)
-
Enter `OAuth 2.0` in the search bar. The OAuth 2.0 plugin appears. Ensure it's **Installed**.
[See image.](#seeimageservicenow-aiii)
If the plugin isn't installed, click **Install** and then **Activate**.
[]![The All menu under System Applications in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-All-Menu.png)
[]![The OAuth 2.0 plugin is installed in ServiceNow.](/downloads/zia/adding-saas-application-tenants/ServiceNow-OAuth-2_0-Plugin-Installed.png)
[]To verify that the OAuth property is active:
-
In the **Filter navigator**, enter `sys_properties.list` and press **Enter** on your keyboard.
[See image.](#seeimageservicenow-bi)
- On the **System Properties** page, enter the following property in the search bar and press **Enter** on your keyboard:
com.snc.platform.security.oauth.is.active
[See image.](#seeimageservicenow-bii)
-
Ensure that the **Value** column for the **com.snc.platform.security.oauth.is.active** property is **true**.
[See image.](#seeimageservicenow-biii-0)
If it's not, in the **Name** column, click **com.snc.platform.security.oauth.is.active**, enter `true` for the **Value**, and then click **Update**.
[See image.](#seeimageservicenow-biii-1)
[]![sys_properties.list entered in the ServiceNow Filter navigator.](/downloads/zia/adding-saas-application-tenants/ServiceNow-sys_properties_list-menu.png)
[]![com.snc.platform.security.oauth.is.active property entered in the search bar on the System Properties page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Properties-Search-Bar.png)
[]![true highlighted in the Value column for the com.snc.platform.security.oauth.is.active property.](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Properties-Value-Column.png)
[]![The Value field highlighted in the System Property window. ](/downloads/zia/adding-saas-application-tenants/ServiceNow-System-Property-Value-Field.png)
[]To configure an OAuth client application:
-
Go to **System OAuth** > **Application Registry**.
[See image.](#seeimageservicenow-ci)
-
Click **New**.
[See image.](#seeimageservicenow-cii)
-
Click **Create an OAuth API endpoint for external clients**.
[See image.](#seeimageservicenow-ciii)
The **Application Registries New Record** window appears.
-
[]In the **Application Registries New Record** window:
- **Name**: Enter a name for the OAuth client application. In this example, it's Zscaler SaaS Application Tenant.
- **Client ID**: Copy the client ID of the application. You need it for Step ii of [d. Add ServiceNow as a Tenant](#servicenow-step-dii).
- **Client Secret**: The shared secret of the application, which the ServiceNow instance and the OAuth client application use to authorize their communication. The secret generates after you submit this application registry.
- **Refresh Token Lifespan**: The default lifespan is 8,640,000 seconds (100 days). Zscaler recommends changing it to a larger value, such as 157,700,000 seconds (5 years) because you'll need to configure ServiceNow as a new tenant after the refresh token expires.
- **Access Token Lifespan**: The default value is 1,800 seconds (30 minutes). Zscaler recommends changing it to a larger value, such as 86,400 seconds (24 hours).
[See image.](#seeimageservicenow-civ)
- Click **Submit**.
-
On the **Application Registries** page, in the **Name** column, click the name of the configured OAuth client application. In this example, it's Zscaler SaaS Application Tenant.
[See image.](#seeimageservicenow-cvi)
The **Application Registries** window appears.
-
In the **Application Registries** window, click the **Lock** icon for **Client Secret**.
[See image.](#seeimageservicenow-cvii)
-
[]Copy the client secret. You need it for Step ii of [d. Add ServiceNow as a Tenant](#servicenow-step-dii).
[See image.](#seeimageservicenow-cviii)
[]![The Application Registry menu in the ServiceNow portal.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registry-Menu.png)
[]![The New button on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Button.png)
[]![The Create an OAuth API endpoint for external clients option on the OAuth application page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Create-an-OAuth-API-Endpoint-for-External-Clients.png)
[]![The configured Application Registries New Record window.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-New-Record-Window.png)
[]![The OAuth client application name in the Name column on the Application Registries page.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Name-Column.png)
[]![The Lock icon for the Client Secret in the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Application-Registries-Client-Secret-Lock-Icon.png)
[]![The visible Client Secret on the Application Registries window of the OAuth client application.](/downloads/zia/adding-saas-application-tenants/ServiceNow-Client-Secret.png)
[]To add ServiceNow as a SaaS application tenant:
-
[]Under **Register the OAuth Application**:
- **Client ID**: Enter the client ID you copied in [c. Configure an OAuth Client Application](#servicenow-step-civ).
- **Client Secret**: Enter the Client Secret you copied in [c. Configure an OAuth Client Application](#servicenow-step-cviii).
- **Instance URL**: Enter the URL used to log in to your ServiceNow instance.
- **User ID**: Enter the user ID of the user account used to configure the OAuth client application.
- **User Password**: Enter the password of the user account used to configure the OAuth client application.
[See image.](#seeimageservicenow-dii)
-
Under **Enter the ServiceNow Admin Email ID**, enter your admin email ID used to log in to your ServiceNow instance.
[See image.](#seeimageservicenow-diii)
-
Under **Authorize the SaaS Application**, click **Authorize**.
[See image.](#seeimageservicenow-div)
[]![The Register the OAuth Application section on the Add SaaS Application Tenant page.](/downloads/zia/adding-saas-application-tenants/ZIA-Register-the-OAuth-Application.png)
[]![The ServiceNow Admin Email ID field in the Enter the ServiceNow Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-ServiceNow-Admin-Email-ID.png)
[]![The Authorize button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Authorize-ServiceNow.png)
[]
Zscaler and Slack are technology partners. To learn more about the Zscaler and Slack integration, see the [Zscaler and Slack Deployment Guide](/zscaler-technology-partners/zscaler-and-slack-deployment-guide).
To configure Slack:
- Under **Enter the Slack Admin Email ID**, enter your admin email ID used to log in to the Slack portal.
[See image.](#seeimageslack-b)
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials**.
[See image.](#seeimageslack-c)
The Slack portal appears.
- Log in to Slack.
- Review the required permissions for the Zscaler service to access Slack, click **Allow**.
- In the ZIA Admin Portal, under **Authorize Access to a Slack Bot**, click **Provide Admin Credentials**.
[See image.](#seeimageslack-f)
The Slack portal appears.
- Review the required permissions for the Zscaler service to send notifications to users through a custom Slack bot, and click **Allow**.
[]![The Slack Admin Email ID field in the Enter the Slack Admin Email ID section.](/downloads/zia/adding-saas-application-tenants/ZIA-Enter-Slack-Admin-Email-ID.png)
[]![The Provide Admin Credentials button in the Authorize the SaaS Application section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-SaaS-Application-Provide-Admin-Credentials-Slack.png)
[]![The Provide Admin Credentials button in the Authorize Access to a Slack Bot section.](/downloads/zia/adding-saas-application-tenants/ZIA-Authorize-Access-Slack-Bot-Provide-Admin-Credentials.png)
[]To configure Smartsheet:
- [a. Generate the Smartsheet API Access Token](#generate-smartsheet-token)
- [b. Add Smartsheet as a Tenant](#add-smartsheet-tenant)
[]To configure Smartsheet as a SaaS tenant, you must have a Smartsheet admin account with an Event Reporting license.
-
Log in to Smartsheet using a valid Smartsheet admin account.
[See image.](#smartsheet-login)
-
In the left-side navigation, click the **Account **icon, then select **Personal Settings**.
[See image.](#smartsheet-personal-settings)
-
In the **Personal Settings** dialog box, select **API Access**.
[See image.](#smartsheet-api-access)
-
In the **Manage API Access Tokens** panel, click the **Generate new access token** button, then enter a name for the token and click **OK**. Zscaler recommends that you add Zscaler to the token name to make it easier to find later.
[See image.](#smartsheet-generate-token)
-
Copy the token to your computer's clipboard. You need it when you add Smartsheet as a tenant in Zscaler.
[See image.](#smartsheet-copy-token)
[]![Smartsheet login](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/smartsheet-login_0.png)
[]![Smartsheet personal settings](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/smartsheet-personal-settings_0.png)
[]![Manage API access token](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/smartsheet-api-access_0.png)
[]![Generate API access token](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/smartsheet-generate-api-token_0.png)
[]![Copy API token](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/smartsheet-copy-api-token_0.png)
[]
-
Under **Authorize the SaaS Application**, add the Smartsheet API access token [you generated and copied to your clipboard](#generate-smartsheet-token).
[See image.](#smartsheet-authorize)
[]![Enter email ID and API token](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/ZIA-Authorize-SaaS-Enter-API-Token_0.png)
[]To configure Trello:
Trello can only be configured for SSPM scan which requires an Advanced SSPM license. If you don't have the correct license, you will see a message to upgrade your license next to the **SSPM Scan** checkbox.
- Log in to the [Trello Power-Ups and Integrations](https://trello.com/power-ups/admin) with your admin credentials.
-
Click **New**.
[See image.](#trello_new)
- Enter your information in the **New Power-Up or Integration** fields. Click **Create** when done.
- Under **API key**, click **Generate a new API key**.
-
In the **Generate API key** window, click **Generate API key**.
[See image.](#trello_apikey)
-
Copy the **API key** and **Secret** for use later and add the ZIA URL in the **Allowed origins** field.
[See image.](#trello_secret)
Required API scopes are as follows:
- read: Reading of boards, organizations, etc. on behalf of the user
- write: Writing of boards, organizations, etc. on behalf of the user
- account: Read member email, writing of member info, and marking notifications read
To learn more, refer to [Authorizing with Trello's REST API](https://developer.atlassian.com/cloud/trello/guides/rest-api/authorization/).
- In the ZIA Admin Portal under **Enter the Trello Admin Email ID**, enter your admin email ID used to log in to Trello.
-
Under **Authorize the SaaS Application**, enter your **Trello API Key** and **Organization ID**.
[See image.](#trello_auth)
You should have copied your API key earlier, and the Organization ID can be found in the address bar of your Trello workspace page.
[See image.](#trello_id)
- Click **Provide Admin Credentials**. Log in with your Trello admin information and click **Allow** to give Zscaler access to the application.
[]![Power-Ups and Integrations page with annotations around the New button](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/trello_new.png)
[]![Authorize the SaaS Application step with fields for API Key and Organization ID in addition to Provide Admin Credentials](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/trello_authorize.png)
[]![Generate API Key window with annotation around Generate API key button](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/trello_apikey.png)
[]![API key page with annotations around the copy buttons for API key and Secret](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/trello_apisecret.png)
[]![Trello workspace URL with annotations around the ID in the URL](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/trello_id.png)
[]To configure Twilio:
Twilio can only be configured for SSPM scan which requires an Advanced SSPM license. If you don't have the correct license, you will see a message to upgrade your license next to the **SSPM Scan** checkbox.
- Log in to the [Twilio Portal](https://www.twilio.com/login) with your admin credentials.
-
Go to **Account-Management** from the top-right corner.
[See image.](#twilio_account)
-
In the left-side navigation, click **API keys & tokens.**
[See image.](#twilio_api)
- Click **Create API Key**. Enter the name, region, and set **Key Type** as **Main**. Click **Create**.
-
Copy the **SID** and **Secret** for use later.
[See image.](#twilio_sid)
- In the ZIA Admin Portal, under **Enter the Twilio Admin Email ID**, enter your admin email ID used to log in to Twilio.
-
Under **Authorize the SaaS Application**, enter the **Account SID** and **Secret** you copied earlier and click **Provide Admin Credentials** to grant Zscaler access to the application.
[See image.](#twilio_auth)
[]![Twilio settings menu with an annotation around Account management](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Twilio_account.png)
[]![Authorize the SaaS Application step with fields for Account SID and Secret in addition to Provide Admin Credentials](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/twilio_auth.png)
[]![Twilio left-side navigation menu with annotation around API keys & tokens](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Twilio_API%20keys.png)
[]![Copy secret key menu with annotations around SID and Secret](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Twilio_secret.png)
[]To configure Webex Teams:
- Both onboarding options for Webex Teams allow you to configure rules for messages, but for file attachments you need to onboard the tenant for Real-time DLP. To learn more about rules and in-line DLP configuration, see [Adding a Collaboration & Online Meetings Rule for Cloud App Control](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control) and [Configuring DLP Policy Rules](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled).
- DLP and Malware scanning SaaS API and Real-time DLP cannot be enabled at the same time. You have the ability to easily switch between the two when editing the tenant. To learn more, see [Editing, Deleting, or Duplicating Items](/zia/editing-deleting-duplicating-items).
- Configuring Webex Teams for the SSPM scan requires Advanced SSPM. If you don't have Advanced SSPM, a message to upgrade appears next to the SSPM scan checkbox.
- [DLP and Malware Scanning SaaS API and SSPM Scan](#WebexDLP)
- [Real-time DLP](#WebexReal)
Onboarding for the SSPM scan requires additional scopes compared to DLP and Malware Scanning. These are applied automatically during the** Authorize the SaaS Application** step in the following instructions. If you want to add SSPM scan to an existing tenant, you need to reauthorize Webex Teams by editing it and revalidating, or deleting the tenant and creating a new one. To learn more, see [About SaaS Application Tenants](/zia/about-saas-application-tenants).
- []Under **Enter the Webex Teams Admin Email ID**, enter your admin email ID used to log in to the Webex portal.
[See image.](#WebexTeams_Admin)
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials**.
[See image.](#WebexTeams_Authorize)
The Webex portal appears.
- Log in to Webex.
- Review the required permissions for the Zscaler service to access Webex Teams, follow the on-screen instructions, and click **Allow**.
- In the ZIA Admin Portal, click **Authorize **if you already have a Cisco connection, or click **Create a Bot** if you don't.
[See image.](#WebexTeams_SlackBot)
The Webex portal appears.
- Sign in and review the required permissions for the Zscaler service to send notifications to users through a custom bot, and click **Allow**.
-
[]Under **Enter the Webex Teams Admin Email ID**, enter your admin email ID used to log in to the Webex portal.
[See image.](#webexreal_admin)
- Under **Authorize the SaaS Application**, click **Provide Admin Credentials**.
- Log in to Webex.
- Review the required permissions for the Zscaler service to access Webex Teams, follow the on-screen instructions, and click **Allow**.
- In the ZIA Admin Portal, click **Authorize**.
[][![Webex Teams tenant admin email ID field](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/WebexTeams_03_AdminEmail05.png)
]
[][![Webex Teams tenant admin email ID field](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/WebexTeams_03_AdminEmail05.png)
]
[][![Authorize the Webex Teams application](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/WebexTeams_04_Authorize04.png)
]
[][![Authorize Access to a Slack Bot](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/WebexTeams_06_WebexTeamsBot.png)
]
[]Workday can only be configured for SSPM scan which requires an Advanced SSPM license. If you don't have the correct license, a message to upgrade your license appears next to the **SSPM Scan** checkbox.
To configure Workday SSPM scan:
- Sign in to your Workday portal.
- In the search bar, enter `Register API Client` and select the result.
-
Enter the following information:
- **Client Name**: Enter the client name.
- **Client Grant Type**: Select **Authorization Code Grant**.
- **Enforce 60 Minute Access Token Expiry**: Select this checkbox.
- **Access Token Type**: Select **Bearer**.
- **Redirection URI**: Enter your Zscaler URL (e.g., `https://admin.zscaler.net`).
- **Refresh Token Timeout (in days)**: Enter `360`.
- **Scope (Functional Areas)**: Select **Staffing**, **System**, and **Tenant Non-Configurable**.
[See image.](#wd_info)
- Click **OK**.
-
Copy the **Client ID**, **Client Secret**, **Workday REST API Endpoint**, **Token Endpoint**, and **Authorization Endpoint**.
[See image.](#wd_endpoint)
-
In the ZIA Admin Portal, under **Register the OAuth Application**, enter your **Client ID**, **Client Secret**, **Workday REST API Endpoint**, **Token Endpoint**, and **Authorization Endpoint**.
[See image.](#wd_register)
- Enter your Workday admin email ID.
-
Under **Authorize the SaaS Application**, click **Provide Admin Credentials** and enter your Workday login details.
[See image.](#wd_auth)
[]![Workday Register API Client page](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/workday_info.png)
[]![Workday API client info page](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/workday_endpoint.png)
[]![ZIA Register the OAuth Application step](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/workday_register.png)
[]![ZIA Authorize the SaaS Application step](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/workday_authorize.png)
[]To configure Zoom:
- [DLP and Malware Scanning SaaS API](#zoom_dlp)
- [SSPM Scan](#zoom_sspm)
- []Sign in to [Zoom](https://zoom.us/signin#/login) with your admin account.
- Go to the [Zoom Marketplace](https://marketplace.zoom.us/).
-
Go to **Develop** > **Build App**.
[See image.](#zoom_buildapp)
- Select **General App** and click **Create**.
-
Go to the **Production** tab and choose **Admin-managed** for the app type. Click **Save**.
[See image.](#zoom_admin)
-
[]Go to the **App Credentials** tab in the left-side navigation and note down your **Client ID** and **Client Secret** for use later.
[See image.](#zoom_clientid)
-
Under **OAuth Redirect URL **and **OAuth Allow Lists**, enter the URL of your Zscaler server.
List of Zscaler URLs:
- `https://admin.zscalerbeta.net`
- `https://admin.zscalertwo.net`
- `https://admin.zscalerthree.net`
- `https://admin.zscaler.net`
- `https://admin.zscloud.net`
- Go to the **App Listing** tab and add **Short Description**, **Long Description**, **Developer Contact Information**, and any other mandatory fields.
-
Go to the **Scopes** tab and add the following scopes:
- account:read:settings:admin
- account:update:settings:admin
[See image.](#zoom_sspm_scope)
- After adding the scopes, add a **Scope Description** and click **Continue**.
-
Go to **Beta Test** in the left-side navigation. If everything has been set up correctly, you will see an **Add App Now** button. Don't select the button, it just indicates you have configured everything. If any required information is missing, this page will show you what is still missing before the **Add App Now** button appears.
[See image.](#zoomsspm_beta)
-
In the ZIA Admin Portal, under **Authorize the SaaS Application**, enter your **Client ID** and **Client Secret** noted down [earlier](#idnote).
In the **Admin Email ID** field, enter the email address of the Zoom user assigned the **Owner** role, and click **Authorize**. For information on Zoom user roles, refer to the [Zoom documentation](https://support.zoom.com/hc/en/article?id=zm_kb&sysparm_article=KB0061789).
[See image.](#zoom_info)
[]![Build App in the Develop dropdown](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_01_BuildApp.png)
[]![Go to the production tab and select Admin-managed](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_03_admin_managed.png)
[]![Copy your client ID and Secret for use later](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_12_clientid.png)
[]![Add scopes.](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_08_scopes.png)
[]![Autorize the SaaS Application, add Client ID and Secret](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_13_authorize.png)
[]![Add App Now button](/downloads/tech-pubs-drafts/zia-draft-articles/adding-saas-application-tenants-doc-51520-zoom/Zoom_sspm_14_button.png)
[]![Configure External Trusted Domain Profiles and User Profiles onboarding step](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Config_domains2.png)
[]![Drop-down menu for selecting External Trusted Domains or Users](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Config_domains_dropdown2.png)
- []Sign in to [Zoom](https://zoom.us/signin#/login) with your admin account.
- Go to the [Zoom Marketplace](https://marketplace.zoom.us/).
-
Go to **Develop** > **Build App**.
[See image.](#zoom_buildapp2)
- Select **General App** and click **Create**.
-
Go to **Production** and choose **Admin-managed** for the app type. Click **Save**.
[See image.](#zoom_admin2)
-
[]Go to the **App Credentials** tab in the left-side navigation and note down your **Client ID** and **Client Secret** for use later.
[See image.](#zoom_clientid2)
-
Under **OAuth Redirect URL **and **OAuth Allow Lists**, enter the URL of your Zscaler server.
List of Zscaler URLs:
- `https://admin.zscalerbeta.net`
- `https://admin.zscalertwo.net`
- `https://admin.zscalerthree.net`
- `https://admin.zscaler.net`
- `https://admin.zscloud.net`
-
On the **Add Feature** page, copy your **Secret Token**.
[See image.](#zoom_secrettoken)
-
Go back to the ZIA Admin Portal and under the **Webhook Integration**, in the **Admin Email ID** field, enter the email address of the Zoom user assigned the **Owner** role. To learn more about Zoom user roles, refer to the [Zoom documentation](https://support.zoom.com/hc/en/article?id=zm_kb&sysparm_article=KB0061789). In the **Secret Token** field, enter the secret token you copied earlier. Click **Initiate Integration**.
[See image.](#zoom_webhook)
- Copy the **Event notification endpoint URL**.
-
Back in Zoom, go to the **Feature** page and enable **Event subscriptions**. Enter a name and paste the **Event notification endpoint URL** you copied earlier and click **Validate**.
[See image.](#zoom_eventsub)
- Click **Add Events** and add the following events:
- Add Chat Message > Chat Message Sent, Updated, and Replied as Event Types
- Chat Channel > Chat Channel Created, Chat Channel Updated, Chat Channel Deleted, Member Invited, Member removed, Member Joined, Member Left
- User Activity > User has signed in, User has signed out
- Click **Done** and **Save**.
- Go to **Information** and add **Short Description**, **Long Description**, **Developer Contact Information**, and any other mandatory fields.
-
Go to **Scopes** and add the following scopes:
- **report:read:list_chat_sessions:admin**
- **report:read:chat_session:admin**
- **team_chat:read:list_user_messages:admin**
- **team_chat:read:list_members:admin**
- **dashboard:read:list_meetings:admin**
- **cloud_recording:read:list_recording_files:admin**
- **report:read:operation_logs:admin**
- **report:read:user_activities:admin**
- **team_chat:delete:user_message:admin**
- **meeting:read:list_past_participants:admin**
- **team_chat:read:user_message:admin**
- **team_chat:read:user_channel:admin**
[See image.](#zoom_dlp_scope)
- After adding the scopes, add a **Scope Description** and click **Continue**.
-
Go to **Beta Test** in the left-side navigation. If everything has been set up correctly, you see an **Add App Now** button. If any required information is missing, this page shows you what is still missing before the **Add App Now** button appears.
[See image.](#zoom_beta2)
- In the ZIA Admin Portal, under **Webhook Integration**, in the **Admin Email ID** field, enter the email address of the Zoom user assigned the **Owner** role. In the **Secret Token** field, enter the secret token you copied earlier. To learn more about Zoom user roles, refer to the [Zoom documentation](https://support.zoom.com/hc/en/article?id=zm_kb&sysparm_article=KB0061789). Click **Initiate Integration**.
-
Under **Authorize the SaaS Application**, enter your **Client ID** and **Client Secret** noted down [earlier](#idnote2).
[See image.](#zoom_info2)
Zoom Integration Details and Limitations
The following list includes details and limitations of the Zoom DLP and Malware Scanning SaaS API integration:
- Inbound messages from external users are not reflected in the API until an internal user sends a message.
- If an external user is not in the contact list of an internal user, the API doesn't return the sender email. Zscaler shows the display name in this case.
- Edited messages can only be given through webhook and need their own handling. Edit history for a message cannot be retrieved, only the latest instance of the message can be scanned.
- Meeting transcriptions and files cannot be retrieved with Zoom on-premise deployments.
- In-meeting chats cannot be scanned unless continuous meeting chat is enabled.
- Transcription scanning can only be done if closed captioning is enabled for the user or globally by the admin in the Settings tab.
- For transcripts, meeting ID is appended in the messageId field with the file ID.
- The DLP/Malware remove functionality removes files and messages.
- For files, messageId is appended in the fileId field.
- The meeting topic is in the channel name field.
- Each sub-account is considered a separate organization and needs its own connector and scan.
- The whiteboard and notes are not scanned.
- Login Fail activity is not reported.
- The Delete functionality cannot be performed on files added by external users.
[]![Build App in the Develop dropdown](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_01_BuildApp.png)
[]![Go to the production tab and select Admin-managed](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_03_admin_managed.png)
[]![App Credentials page to copy your Client ID and Secret for later use](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_12_clientid.png)
[]![Add scopes.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_08_scopes.png)
[]![Authorize the SaaS Application step in ZIA](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_13_authorize.png)
[]![Add App Now button](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_sspm_14_button.png)
[]![Add feature page with annotation around Copy button next to Secret Token](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/Zoom_secrettoken.png)
[]![ZIA Admin Portal Webhook Integration step](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/zoom_webhook.png)
[]![Zoom Event subscription page](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-saas-application-tenants/zoom_eventsub.png)