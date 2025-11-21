# Configuring the Workload Discovery Service for Microsoft Azure Accounts
Source: https://help.zscaler.com/cloud-branch-connector/configuring-workload-discovery-service-microsoft-azure-accounts
PDF: https://help.zscaler.com/pdf/com/en/1507561.pdf

This article provides information on how to onboard a Microsoft Azure account to enable workload discovery services within the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [About Microsoft Azure Accounts](/cloud-branch-connector/about-microsoft-azure-accounts).
Workload discovery services for Azure are in Limited Availability (LA). To learn more, contact Zscaler Support.
Prerequisites
Before you configure an Azure account, ensure that the following prerequisites are met:
- [Configure your IAM roles and permissions in Azure](/cloud-branch-connector/configuring-iam-roles-and-permissions-microsoft-azure).
- Ensure that the managed identity is updated with the list of Cloud Connectors you want to deploy. To learn more, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).
- Verify your region is supported. To learn more, see [Analyzing Microsoft Azure Account Details](/cloud-branch-connector/analyzing-microsoft-azure-account-details#regionsworkloadinventory).
- Create a resource group in Azure where your event grid topic for your Azure account is hosted.
- Create a storage account for Cloud Connector to create storage queues to receive messages from the event grid. The Cloud Connector requires a storage account.
- If you are using the event grid to distribute tags, create a partner configuration in Azure. For security reasons, Zscaler must authorize the partner configuration prior to onboarding.
- [To create a partner configuration in Azure:](#createptpd)
Adding an Azure Account
To add an Azure account:
- Sign in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration** > **Partner Integrations** > **Azure**.
-
Click **Add Account**.
[See image.](#addazureaccount)
The **Add Azure Account window** appears.
- In the **Add Azure Account** window:
- On the **Credentials** tab:
- **Account Name**: Enter a name for the Azure account used in the service principal credential. It does not have to be the same name used in the Azure portal.
- **Directory (tenant) ID**: Enter the Directory (tenant) ID used in the service principal credential. Use the Directory (tenant) ID from Azure.
- **Client/Application ID**: Enter the client/application ID used in the service principal credential. Use the Application (client) ID from Azure.
-
**Client/Application Secret**: Enter the client/application secret used in the service principal credential. Use the client secret from Azure.
To learn more about obtaining the **Directory (tenant) ID**, **Client/Application ID**, and **Client/Application Secret** credentials, see [Configuring IAM Roles and Permissions for Microsoft Azure](/cloud-branch-connector/configuring-iam-roles-and-permissions-microsoft-azure).
[See image.](#credentials)
- On the **Subscription Groups** tab:
- **Region**: Select the region(s) you want the Zscaler service to read the resource tag from.
-
**Subscriptions**: Select the subscription(s) you want the service to read the resource tag from.
[See image.](#subscriptiongroups)
-
On the **Groups & Namespace** tab:
-
**Cloud Connector Groups**: (Optional) Select the Cloud Connector group(s) to which to send the mapping of IP address to tag.
Ensure that the Cloud Connector groups you select receive the workload traffic from the subscriptions and regions you choose on the **Subscription Groups** tab. If you do not select a Cloud Connector group, the workload discovery service only discovers assets but cannot use the tags in policies. It can only view the policy.
- **Namespace (Optional)**: Enter a namespace to limit the IP addresses sent to the Cloud Connector. This ensures that duplicate IP addresses do not map incorrectly. If you have a duplicate CIDR block in your virtual networks (VNets) in the same subscription, you can partition the subscription tags to make one partition the namespace. You can then send the traffic to the Cloud Connector group, because in the Cloud Connector group you cannot see duplicate IP addresses.
[See image.](#groupsandnamespace)
- On the **Add** **Event Grid** tab:
- **Regions**: Select the regions where you want Zscaler to create the event grid topics. The event grid topics are used to notify the Zscaler service of real-time tag updates to ensure that real-time tag mapping updates in the Zscaler service.
- **Subscriptions**: Select a subscription where Zscaler creates an instance of the partner topic and partner destination.
-
**Resource Groups**: Select a resource group where Zscaler creates an instance of the partner topic and partner destination.
The event grid is optional and depends on storage account creation in Azure. The queue that the Cloud Connector creates depends on the storage account for Cloud Connector to be able to create the queue. The Zscaler service can only attempt to create a partner topic and a partner destination after you provide the **Resource Group** and **Subscription ID**.
[See image.](#eventgrid)
- On the **Storage Account** tab:
- **Regions**: All regions selected on the **Event Grid** tab are listed. Select a subscription and storage account for each region.
- **Subscriptions**: Select a subscription where your storage account is located.
- **Storage Account**: Select a storage account where the Cloud Connector creates a storage queue for the event grid. To learn more about creating a storage account, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal).
-
**Prefix**: (Optional) Enter a prefix to name and create a storage queue. This prefix is added to the name of the queue so you can organize the queues.
[See image.](#storageaccount)
-
On the **Review** tab, confirm that the information is correct and click **Save and Next**.
[See image.](#review)
Post-Configuration Requirements
If you are using the event grid, the following post-configuration requirements are mandatory. After you configure an Azure account in the Cloud & Branch Connector Admin Portal, ensure that the following requirements are met:
- [Activate the partner topic and/or partner destination](#activateptpd)
- [Create the system topic](#systemtopic)
[]
Activating the partner topic allows you to receive tags soon after activation. Activating the partner destination allows you to send messages from your account to the Zscaler service when changes are happening.
To activate the partner topic and/or partner destination:
- Sign in to the [Azure portal](https://portal.azure.com).
- In the **Search resources, services, and docs (G+/) field**, enter `event grid`.
- From the drop-down menu, select **Event Grid**. The **Event Grid** page appears.
-
On the **Event Grid** page, from the left-side navigation, select **Partner configurations**. The **Partner configurations** page appears.
[See image.](#partnerconfig3)
- On the **Partner configurations** page, select the **Resource group** you created. On the **Resource group** page:
-
Copy your **Resource Group** and **Subscription ID** to be shared with the Zscaler service when [Adding a Microsoft Azure Account](/cloud-branch-connector/adding-microsoft-azure-account). The Zscaler service can only attempt to create a partner topic and a partner destination after you provide the **Resource Group** and **Subscription ID**.
[See image.](#partnerconfig4c)
-
From the **Resources** list, select the partner topic or partner destination.
[See image.](#partnerconfig4b)
-
On the **Event Grid Partner Topic** or **Event Grid Partner Destination** page, on the **Overview** tab, click **Activate**.
[See image.](#partnerconfig4a)
The partner topic and/or partner destination is activated. After the partner destination is activated, you must configure the system topic to send messages in the partner destination.
You must go to the resource group for every region you are activating and activate the partner topic and/or partner destination in that region.
[]
Creating the system topic allows you to send messages in the partner destination and alerts the Zscaler service that a change has occurred in your subscription so that tags are immediately extracted. You can either manually create the system topic or use the Terraform template.
To create the system topic:
- Sign in to the [Azure portal](https://portal.azure.com).
- In the **Search resources, services, and docs (G+/) field**, enter `event grid`.
- From the drop-down menu, select **Event Grid**. The **Event Grid** page appears.
-
On the **Event Grid** page, from the left-side navigation, under **Azure service events**, select **System topics**. The **Event Grid | System topics** page appears.
[See image.](#systemtopicstep4)
-
On the **Event Grid | System topics** page, click **Create**.
[See image.](#systemtopicstep5)
- On the **Event Grid System Topic** page, configure the following:
- On the **Basics** tab:
- In the **Topic Details** section:
- **Topic Types**: From the drop-down menu, select **Azure Resource Notifications - Resource Management events**.
-
**Subscription**: From the drop-down menu, select your subscription.
Only one system topic can be created per subscription.
[See image.](#systemtopicstep6a-i)
- In the **System Topic Details** section:
- **Resource group**: From the drop-down menu, select your resource group created as a prerequisite.
- **Name**: Enter a name for the system topic.
-
**Location**: **Global** is selected by default and you cannot change it.
[See image.](#systemtopicstep6a-ii)
- In the **Identity** section, leave the settings unchanged.
- On the **Tags** tab, leave the settings unchanged.
- On the **Review + create** tab, click **Create**.
-
On the system topic **Deployment** page, after the deployment succeeds, click **Go to resource**. Alternatively, in the top-right corner, click **Go to resource**. Your **Event Grid System Topic** page appears.
[See image.](#systemtopicstep7)
-
On your **Event Grid System Topic** page, from the left-side navigation, under **Entities**, select **Event Subscriptions**. The **Event Subscriptions** page appears.
[See image.](#systemtopicstep8)
-
On the **Event Subscriptions** page, click **Event Subscription**.
[See image.](#systemtopicstep9)
- On the **Create Event Subscription** page, configure the following:
- On the **Basics** tab:
- In the **Event Subscription Details** section:
- **Name**: Enter a name for the event subscription.
-
**Event Schema**: From the drop-down menu, select **Cloud Event Schema v1.0**.
[See image.](#systemtopicstep10a-i)
- In the **Topic Details** section, you can view the **Topic Type**, **Source Resource**, and **Topic Name** details.
-
In the **Event Types** section, from the **Filter to Event Types** drop-down menu, select the **Resource Created or Updated** checkbox.
[See image.](#systemtopicstep10a-iii)
- In the **Endpoint Details** section:
- **Endpoint Type**: From the drop-down menu, select **Partner Destination**.
-
**Endpoint**: Click **Configure an endpoint**. The **Select Partner Destination** window appears.
[See image.](#systemtopicstep10a-iv-1)
- In the **Select Partner Destination** window:
- **Subscription**: Select your subscription. This is the subscription you provided when [adding an Azure account](/cloud-branch-connector/adding-microsoft-azure-account#eventgrid) in the Cloud & Branch Connector Admin Portal.
- **Resource group**: Select your resource group. This is the resource group you provided when [adding an Azure account](/cloud-branch-connector/adding-microsoft-azure-account#eventgrid) in the Cloud & Branch Connector Admin Portal.
-
**Partner Destination**: From the drop-down menu, select the partner destination.
Select **Confirm Selection**.
[See image.](#systemtopicstep10a-iv-2)
- On the **Filters** tab, leave the settings unchanged.
- On the **Additional Features** tab, leave the settings unchanged.
- On the **Delivery Properties** tab, leave the settings unchanged.
- Click **Create**.
After your deployment succeeds, Zscaler can send and receive event notifications for a designated subscription.
[]
![Selecting the Resource group you created on the Partner configurations page of the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/activating-partner-topic-microsoft-azure/partnerconfig9.png)
[]
![Activating the Partner Topic or Partner Destination on the Overview tab of the Event Grid Partner Topic page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/activating-partner-topic-microsoft-azure/PT9.png)
[]
![Selecting your Partner Topic or Partner Destination from the list in your Resource group in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/activating-partner-topic-microsoft-azure/partnerconfig9aii.png)
[]
![Copying your Subscription and Subscription ID from your Resource group](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/activating-partner-topic-microsoft-azure/partnerconfig9ai_0.png)
[]
![Selecting System topics from the Event Grid page left-side navigation in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic4.png)
[]
![Selecting Create on the System topics page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic5.png)
[]
![Entering the topic details in the Topic Details section on the Basics tab of the Event Grid System Topic page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic6ai.png)
[]
![Entering the system topic details in the System Topic Details section on the Basics tab of the Event Grid System Topic page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic6aii.png)
[]
![Clicking Go to resource on the system topic Deployment page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic7.png)
[]
![Selecting Event Subscriptions from the Event Grid System Topic page left-side navigation in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic8.png)
[]
![Selecting Event Subscription on the Event Subscriptions page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic9.png)
[]
![Entering the event subscription details in the Event Subscription Details section on the Basics tab of the Create Event Subscription page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic10ai.png)
[]
![Entering the event type details in the Event Types section on the Basics tab of the Create Event Subscription page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic10aiv1.png)
[]
![Entering the endpoint details in the Endpoint Details section on the Basics tab of the Create Event Subscription page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic10aiii.png)
[]
![Configuring the partner destination in the Select Partner Destination window on the Create Event Subscription page of the Microsoft Azure Portal ](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/authorizing-event-grid-access-microsoft-azure/systemtopic10aiv2.png)
[]
- Sign in to the [Azure portal](https://portal.azure.com).
- Navigate to the **Event Grid** page.
-
On the Event Grid page, from the left-side navigation, select **Partner configurations**.
[See image.](#ptpdstep3)
-
On the **Partner configurations** page, click **Create**.
[See image.](#ptpdstep4)
The **Create Partner Configuration** page appears.
- On the **Create Partner Configuration** page, on the Basics tab:
-
Under **Project Details**:
- **Subscription**: Your subscription is set in this field, but you can change it.
- **Resource group**: From the drop-down menu, select your resource group.
[See image.](#ptpdstep5a)
- Under **Partner Authorizations**:
-
**Default maximum partner authorization expiration time (in days)**: Enter the number of days to create an authorization that lasts for the specified time period. During this time period, the Zscaler service attempts to create a partner topic and a partner destination in your tenant. After expiry, this authorization is invalid, and the Zscaler service cannot create a partner topic or partner destination in your tenant. Zscaler only requires this authorization to create the partner topic or partner destination. If the authorization expires after the Zscaler service has created the partner topic or partner destination in your tenant, the partner topic or partner destination remains operational.
If the user who creates the authorization in Azure and the user who creates the Azure account in the Cloud & Branch Connector Admin Portal are different, enter a number of days that allows both users to coordinate the amount of time necessary to share credentials. If you create new accounts over the course of a year, you can give a one-time authorization of 365 days or give an authorization before every new account is created for 7 days at a time. If the same user creates the authorization in Azure and the Azure account in the Cloud & Branch Connector Admin Portal, Zscaler recommends setting the authorization expiration to 7 days as no coordination is required.
-
Click **Partner Authorization**.
[See image.](#ptpdstep5b)
The **Add partner authorization to create resources** window appears.
Zscaler is working on being added to the Microsoft verified partner list. Currently, you must add Zscaler as a non-verified partner.
-
In the **Add partner authorization to create resources** window, select the **Authorize non-verified partner** checkbox, and then configure the following:
- **Partner registration ID**: Enter `2cec046f-4373-41c7-a749-f99efe2e8800`.
- **Authorization expiration time**: Configure the expiration time as necessary.
- **Authorization expiration time UTC**: This field displays the expiration time in Coordinated Universal Time (UTC).
[See image.](#ptpdstep5biia)
- Click **Add**.
-
On the **Basics** tab, click **Review + create**.
[See image.](#ptpdstep6)
-
On the **Review + create** tab, click **Create**.
[See image.](#ptpdstep7)
The partner configuration authorization is created.
[]
![Selecting Partner configurations from the Event Grid page left-side navigation in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig3.png)
[]
![Selecting Create on the Event Grid Partner configurations page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig4.png)
[]
![Entering the project details in the Project Details section on the Basics tab of the Create Partner Configuration page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig5a.png)
[]
![Configuring the partner authorization and selecting Partner Authorization in the Partner Authorizations section of the Basics tab on the Create Partner Configuration page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig5bii.png)
[]
![Selecting the Authorize non-verified partner checkbox and configuring the settings in the Add partner authorization to create resources window in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig5bii-ii.png)
[]
![Selecting Review + create on the Basics tab of the Create Partner Configuration page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/PT4e.png)
[]
![Selecting Create on the Review + create tab of the Create Partner Configuration page in the Microsoft Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/partnerconfig7.png)
[]
![Add Account button on the Azure tab of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-workload-discovery-service-microsoft-azure-accounts/AddAzureAccount-GCP.png)
[]
![The Add Azure Account Credentials tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/credentials.png)
[]
![The Add Azure Account Subscription Groups tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/subscriptiongroups.png)
[]
![The Add Azure Account Groups and Namespace tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/groupsandnamespace.png)
[]
![The Add Azure Account Event Grid tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-workload-discovery-service-microsoft-azure-accounts/addeventgrid.png)
[]
![The Add Azure Account Storage Account tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/storageaccount_0.png)
[]
![The Add Azure Account Review tab](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-microsoft-azure-account/review_0.png)