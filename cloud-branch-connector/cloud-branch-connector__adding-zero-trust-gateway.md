# Adding a Zero Trust Gateway
Source: https://help.zscaler.com/cloud-branch-connector/adding-zero-trust-gateway
PDF: https://help.zscaler.com/pdf/com/en/1516711.pdf

This article provides information on adding a Zero Trust Gateway in the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [About Zero Trust Gateways](/cloud-branch-connector/about-zero-trust-gateways).
Zero Trust Gateways are in Limited Availability. To enable this feature, contact Zscaler Support.
Adding a Zero Trust Gateway
To add a gateway:
- Go to **Administration** > **Zero Trust Gateway**.
-
Click **Add New Gateway**.
[See image.](#addnewgateway)
The **Add Zero Trust Gateway** window appears.
- In the **Add Zero Trust Gateway** window:
- In the **Configuration** section:
- **Name**: Enter a name for the gateway.
- **Region**: Select the Amazon Web Services (AWS) region where you want to create the gateway. You can only deploy in one region, and you cannot modify it after the gateway is created.
- **Availability Zone ID**: Select the availability zones where you want to create the gateway components. You must select a minimum of two availability zones.
- **Location**: Enter the name of the location to be associated with the gateway. This name is visible in all the policies where the location object is available. This location object is created and synced between Cloud Connector policy pages and Zscaler Internet Access (ZIA) policy pages. To learn more, see [About Locations](/cloud-branch-connector/about-locations).
-
**Location Template**: Select the location template that is used for creating the location associated with the gateway.
[See image.](#configuration)
- In the **Accounts** section, you must provide a list of AWS accounts that are allowed to connect to the gateway being created. Zscaler denies endpoint connection requests from AWS accounts not present in this list. If you do not configure an AWS account while adding a Zero Trust Gateway, you must edit it later before connecting endpoints:
- **Allowed Accounts**: Select the AWS accounts that are permitted to connect to the gateway. The gateway accepts the requests originated by endpoints from the same region as the gateway. The AWS accounts in this drop-down menu were previously added by onboarding them on the Partner Integrations page in the Cloud & Branch Connector Admin Portal. To learn more about adding an AWS account, see [About Amazon Web Services Accounts](/cloud-branch-connector/about-amazon-web-services-accounts).
- **Allowed Accounts Groups**: Select the AWS account groups that are permitted to connect to the gateway. The gateway accepts the requests originated by endpoints from the same region as the gateway. The AWS account groups in this drop-down menu were previously created on the Partner Integrations page in the Cloud & Branch Connector Admin Portal. To learn more about adding an AWS account group, see [About Amazon Web Services Account Groups](/cloud-branch-connector/about-amazon-web-services-account-groups).
-
**Additional AWS Accounts**: If your AWS account has not been onboarded on the Partner Integrations page, enter your 12-digit AWS account ID. The gateway accepts the requests originated by endpoints from the same region as the gateway. You can add up to 128 accounts.
[See image.](#accounts)
-
In the **Review** section, confirm that the information is correct and click **Create**.
[See image.](#review)
The Zero Trust Gateway is created. You can use the service address to register the endpoint. To learn more, see [Registering an Endpoint in Amazon Web Services](/cloud-branch-connector/registering-endpoint-amazon-web-services).
[]
![Clicking the Add New Gateway button on the Zero Trust Gateway page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/adding-zero-trust-gateway/ZTGatewayaddnewgateway.png)
[]
![The Configuration tab on the Add Zero Trust Gateway page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/adding-zero-trust-gateway/ztgatewayconfiguration.png)
[]
![The Accounts tab when adding a Zero Trust Gateway in the Zscaler Cloud & Branch Connector Admin Portal. It contains the description: "The gateway accepts incoming endpoint requests from the list of accounts entered. AWS accounts and account groups onboarded on the Partner Integrations page can be selected. For accounts not onboarded using the Partner Integrations page, enter the 12 digit AWS account ID manually. To learn more about Partner Integrations, refer to the Cloud Connector Partner Integrations documentation."](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/adding-zero-trust-gateway/ztgatewayaccounts2.png)
[]
![The Review tab of the Add Zero Trust Gateway page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/zero-trust-gateway-management/adding-zero-trust-gateway/ReviewZTGW.png)