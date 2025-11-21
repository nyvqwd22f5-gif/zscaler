# Analyzing Zero Trust Gateway Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-zero-trust-gateway-details
PDF: https://help.zscaler.com/pdf/com/en/1516716.pdf

The Zero Trust Gateway details page provides management and operational information about the selected gateway. You can access the Zero Trust Gateway details page by selecting a gateway on the [Zero Trust Gateway](/cloud-branch-connector/about-zero-trust-gateways) page.
Zero Trust Gateways are in Limited Availability. To enable this feature, contact Zscaler Support.
Analyzing the Zero Trust Gateway Details Page
On the Zero Trust Gateway details page, you can view the following:
- [Gateway](#gateway)
- [Status](#status)
- [Endpoints](#endpoints)
- [Config](#config)
- [Analytics](#analytics)
- [Events](#events)
- [Traffic Test](#traffictest)
[]
On the **Gateway** tab, you can view the following gateway details:
- **Zero Trust Gateway Name**: The name of your gateway. This is the equivalent of a tag identifying the name of a resource.
- **Endpoint Service Name**: The name of the Amazon Web Services (AWS) endpoint service hosted by Zscaler. You need this service address to create an endpoint in your AWS account. This is the service name based in your AWS console.
- **Region**: The name of the AWS region where the gateway is deployed.
- **Availability Zones**: The IDs of availability zones where the gateway is deployed.
- **Location**: The location name of the gateway.
- **Zero Trust Gateway ID**: The Zscaler internal ID that identifies the resource.
- **Allowed Accounts**: The AWS accounts in partner integrations that are permitted to connect to the gateway.
- **Allowed Account Groups**: The AWS account groups in partner integrations that are permitted to connect to the gateway.
- **Account List**: The 12-digit AWS account IDs, added during configuration, that are permitted to connect to the gateway when [adding a Zero Trust Gateway](/cloud-branch-connector/adding-zero-trust-gateway).
- **Public IPs**: The public IP addresses used for the traffic egressing from the Zscaler AWS account for this gateway. One public IP address is used per availability zone.
-
**Operational Status**: The operational status of the gateway (i.e., **Enabled** or **Disabled**).
[See image.](#gatewaydetails)
[]
The **Status** tab displays the status of the Zero Trust Gateway. Zscaler refreshes the status when you refresh the page. The tab displays the following information about AWS availability zones:
- **Internet**: The ability of the gateway to reach Zscaler Internet Access (ZIA).
- **Local Egress**: The ability of the gateway to forward direct traffic.
- **Private Applications**: The ability of the gateway to reach Zscaler Private Access (ZPA).
The corresponding status can be one of the following:
- **Healthy**: The backend traffic in the availability zone is functioning as expected.
- **Unhealthy**: The traffic is being dropped because there is no healthy backend processing.
- **Degraded**: The traffic might have lost redundancy, but it is still being forwarded.
[See image.](#statusdetails)
[]
On the **Endpoints** tab, you can view a list of endpoints and their details:
- **Endpoint ID**: The ID of the endpoint connected to the gateway. This endpoint is allowed to send traffic to the gateway.
- **AWS Account ID**: The ID of the AWS account associated with the endpoint.
- **Accepted On**: The date and time when the gateway accepted the endpoint.
- **Namespace**: The namespace associated with the endpoint. The workload discovery service configured in partner integrations discovers the namespace. The account ID of the virtual private cloud (VPC) endpoint must be onboarded to the partner integration. The namespace is based on the VPC tag with the key (`zs:namespace`). This field is only available if the workload discovery service and partner integrations are enabled. To learn more about namespaces, see [Understanding Namespaces for Amazon Web Services and Microsoft Azure Accounts](/cloud-branch-connector/understanding-namespaces-amazon-web-services-and-microsoft-azure-accounts).
-
**VPC**: The VPC connected to the gateway where the endpoint is deployed or configured. This field is only available if the workload discovery service and partner integrations are enabled.
[See image.](#endpointsdetails)
[]
The **Config** tab displays a table with the following details about ZIA configuration versions that have been activated:
- **Version**: The version of the Zscaler configuration that was activated.
- **Submitted On**: The date and time the configuration was activated.
- **Active**: The configuration that is applied to all Cloud Connectors. A new configuration push automatically creates a new version.
- **Inactive**: The configuration not applied to the Cloud Connectors which can be reviewed for historical data.
The gateway can reject a configuration that you activate if it makes the gateway unable to function properly. The most recent configuration versions are typically active. If the latest configuration version is not active, the gateway might have rejected the configuration. You can compare two configuration versions by selecting the checkboxes and clicking **Compare Versions**.
[See image.](#configdetails)
[]
On the **Analytics** tab, you can select **Timeframe**, **Stat**, and **Type** to display values from CloudWatch related to the gateway load balancer (GWLB) of your gateway.
You can configure settings for the graph to display the following:
- **Timeframe**: Select a time frame to view data within that range. The graph automatically selects the number of data points based on the time frame you select.
- **Stat**: Select **Average**, **Max**, or **Sum** to view the average, maximum, or total amount of data. Statistics match the statistics in AWS CloudWatch. If the stat for that type is not calculated, the graph returns no value.
-
**Type**: Select a type to modify what data the graph displays:
- **Processed Bytes**: The total number of bytes that the GWLB processed. This includes traffic sent to and from the destination, but not traffic from health checks.
- **Active Connection**: The total number of concurrent connections from client to destination.
- **Reset Count**: The total number of TCP counts that the GWLB sends when there is no backend processing available.
[See image.](#analyticsdetails)
[]
On the **Events** tab, you can select a **Timeframe** to view events that occurred within the range:
- **Event**: The event that occurred (e.g., **Accepted connection for VPC Endpoint** or **Removed connector for VPC Endpoint**).
- **Category**: The category of the event (e.g., **VpcEndpoint**).
- **Type**: The type of event that occurred.
- **Start Time**: The date and time when the event started.
-
**Status**: The status of the event.
[See image.](#eventsdetails)
[]
On the **Traffic Test** tab, you can check whether the endpoint can send the traffic through the Zero Trust Exchange (ZTE). You can also send egressing traffic out through the Zscaler service in ZIA. You can test your forwarding and ZIA policies by creating a traffic test. Zscaler sets up a virtual environment in the Zscaler AWS account and sends traffic through the endpoint to execute the test. The result of the test appears as the output of the AWS curl command. A test created in one gateway is available in all the gateways created in that Cloud Connector account in all regions.
If you navigate to the Zero Trust Gateways page or the Endpoints page while the test environment is active, a connected VPC endpoint that is the Zscaler account is shown.
In the **Test Environment** section, click **Create** to create a test environment. After approximately 5 minutes, the test environment is created. The test environment lasts for one hour. During that hour, an endpoint appears on your gateway with the Zscaler account as its associated account. If you need more time, click **Renew** and the test environment lasts for one more hour. When the test environment is in the `CREATE_COMPLETE` state, you can run the test.
[See image.](#traffictestdetails1)
In the **Tests** section, click **Create Test** to save configuration parameters, which allows you to define AWS curl parameters. In the **Create a New Test** window:
- **Name**: Enter a name for the test.
- **Description (Optional)**: Enter a description for the test.
- **Protocol**: Enter `HTTP` or `HTTPS` as the protocol for the test.
- **URL**: Enter the URL of the website you are testing.
- **Commands (Optional)**: Enter the AWS curl command parameters to test and fetch information about a website.
- **Verbose (-v)**: Select the checkbox to enable verbose, which instructs the curl command to provide information on the website being tested.
-
**Insecure (-k)**: Select the checkbox to enable insecure, which instructs the curl command to not verify the certificate.
[See image.](#createanewtest)
In the table, you can view the following for each test:
- **ID**: The ID of the traffic test.
- **Name**: The name of the traffic test.
- **URL**: The URL associated with the traffic test.
- **Type**: The type of traffic test performed.
- **Description**: The description of the traffic test.
You can also edit, delete, or run a test after a test environment has been created. If a test environment has not been created, run is not an option and the icon does not appear.
[See image.](#traffictestdetails2)
[]
![The Gateway tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgatewaydetailsgatewaytab.png)
[]
![The Status tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal. A row of information for a gateway named usw1-az1 shows Internet: Healthy, Local Egres: Healthy, Private Applications: Healthy.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwystatusdetails2.png)
[]
![The Endpoints tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwyendpointsdetails.png)
[]
![The Config tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal. A table with columns for Version, Submitted On, Active, and Inactive.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwyconfigdetails.png)
[]
![The Analytics tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal. A line graph. The y-axis shows values from 1500000 to 26184117. The x-axis shows times from 15:00 to 00:00 at intervals of one hour. Timeframe is set to Current Day, Stat is set ot Sum, and Type is set to Processed Bytes.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwyanalyticsdetails2.png)
[]
![The Events tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal. The Timeframe drop-down menu shows Current Week: 01/19/2025-01/24/2025. Below the menu, a table with columns for Event, Category, Type, Start Time, and Status. Two example events appear in the table.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwyeventdetails.png)
[]
![The Create button on the Traffic Test tab viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwytraffictestdetails1.png)
[]
![The Traffic Test tab details viewed when analyzing Zero Trust Gateway details in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/analyzing-zero-trust-gateway-details/ztgtwytraffictestdetails2.png)
[]
![The Create a New Test window that appears after selecting Create Test in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/zero-trust-gateway-management/analyzing-zero-trust-gateway-details/ztgwcreateanewtest.png)