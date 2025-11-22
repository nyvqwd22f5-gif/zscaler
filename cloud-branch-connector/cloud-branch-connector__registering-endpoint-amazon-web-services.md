# Registering an Endpoint in Amazon Web Services
Source: https://help.zscaler.com/cloud-branch-connector/registering-endpoint-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1519146.pdf

Zero Trust Gateways allow you to register an endpoint in Amazon Web Services (AWS). Registering your endpoint with the Zscaler service allows you to route and secure your traffic to the Zero Trust Exchange (ZTE).
After you [add a Zero Trust Gateway](/cloud-branch-connector/adding-zero-trust-gateway), you can use the service address to register the endpoint.
- [1. Copy and save the endpoint service name.](#copyendpointservicename)
- [2. Register an endpoint.](#registerendpoint)
- [3. Configure the route table.](#routetable)
[]
To copy the endpoint service name:
-
In the Zscaler Cloud & Branch Connector Admin Portal, on the **Zero Trust Gateway** page, select your gateway by clicking its name.
[See image.](#zerotrustgatewaypage)
-
On the **Gateway** tab, copy and save the **Endpoint Service Name**. You use it when creating an endpoint in AWS.
[See image.](#endpointservicename)
[]
To register an endpoint:
- Sign in to the AWS Management Console.
-
Click **VPC**. The **VPC dashboard** appears.
Endpoints are deployed in the virtual private cloud (VPC). If you want to use centralized deployment, use the transit gateway. To learn more, refer to the [AWS documentation](https://aws.amazon.com/blogs/networking-and-content-delivery/centralized-inspection-architecture-with-aws-gateway-load-balancer-and-aws-transit-gateway/).
-
On the **VPC dashboard**, from the left-side navigation, under **PrivateLink and Lattice**, select **Endpoints**.
[See image.](#step3)
-
On the **Endpoints** page, click **Create endpoint**.
[See image.](#step4)
- On the **Create endpoint** page, configure the following:
- In the **Endpoint settings** section:
- **Name tag**: Enter a name for your endpoint.
-
**Type**: Select **Endpoint services that use NLBs and GWLBs**.
[See image.](#step5a)
- In the **Services** section:
- **Service name**: Paste the **Endpoint Service Name** from the Cloud & Branch Connector Admin Portal and click **Verify service**.
-
**Service Region**: Leave this setting unchanged.
[See image.](#step5b)
-
In the **Network settings** section, under **VPC**, from the **Select a VPC** drop-down menu, select the VPC where you want to deploy the endpoint.
[See image.](#step5c)
-
In the **Subnets** section, select the **Availability Zone** where you want to deploy the endpoint by selecting the checkbox next to the name of the **Availability Zone**.
[See image.](#step5d)
- In the **Tags** section, leave the settings unchanged.
- Click **Create endpoint**.
The endpoint is deployed.
[]
After deploying the endpoint, you must route traffic through it. Traffic passes through the Zero Trust Gateway. To configure the route table, navigate to the **Route tables** page and click **Edit routes** to configure the following:
- **Destination**: (Optional) Enter an IP address.
- **Target**: From the drop-down menu, select **Gateway Load Balancer Endpoint**. Under the **Gateway Load Balancer Endpoint** field, in the drop-down menu, select your endpoint.
Click **Save changes**.
[See image.](#step15)
[]
![Selecting Endpoints under PrivateLink and Lattice on the VPC dashboard page of the AWS Management Console](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep3.png)
[]
![Selecting Create endpoint on the Endpoints page of the AWS Management Console. On this page, there is a table with columns for Name, VPC endpoint ID, Endpoint type, Status, Service name, and Service network. In the upper-right corner, there is a drop-down menu labeled "Actions" and an orange button labeled "Create endpoint."](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep4.png)
[]
![Configuring settings in the Endpoint settings section of the Create endpoint page in the AWS Management Console](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep5a.png)
[]
![Pasting the Service name in the Service settings section of the Create endpoint page in the AWS Management Console](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep5b.png)
[]
![Selecting your VPC from the Network settings section of the Create endpoint page in the AWS Management Console](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep5c.png)
[]
![A table in the AWS Management Console with checkboxes and columns labeled Availability Zone, Subnet ID, Designate IP addresses, IPv4 address, and IPv6 address. The checkbox for the first line of the table is selected.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep5d.png)
[]
![The Edit routes page with columns labeled Destination, Target, Status, and Propagated in the AWS Management Console.](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/awsendpointstep15.png)
[]
![Selecting your Zero Trust Gateway from the Zero Trust Gateway page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/zerotrustgatewaypage.png)
[]
![Copying and saving the Endpoint Service Name on the Gateway tab of your gateway in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/public-cloud-configuration/zero-trust-gateway/registering-endpoint-amazon-web-services/endpointservicename.png)