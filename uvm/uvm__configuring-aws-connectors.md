# Configuring the AWS Connectors
Source: https://help.zscaler.com/uvm/configuring-aws-connectors
PDF: https://help.zscaler.com/pdf/com/en/1531013.pdf

Amazon Web Services (AWS) connectors can ingest data relating to your organization’s findings and resources collected by and stored on your AWS services.
To create the AWS data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#aws-tiles)
There are ten available AWS streams. Select those that are in scope based on your AWS licenses and use cases:
- Accounts: Retrieves metadata about AWS accounts, which includes ID, ARN, email, name, status, joined method (e.g, created or invited), joined timestamp, and tags.
- EC2: Retrieves metadata about EC2 instances, which includes ID, type, public IP address, security groups, and configuration details.
- ECR: Retrieves metadata about Elastic Container Registries (ECR), such as registry ID, image tags, and region name.
- ECR Findings: Retrieves metadata about security vulnerabilities and findings related to container images stored in ECR.
- EKS Clusters API: Retrieves metadata about EKS clusters, which includes name, ARN, endpoint, role ARN, status, tags, and region name.
- Inspector Findings: Retrieves metadata about security vulnerabilities and findings identified by AWS Inspector for organizational resources.
- Network: Retrieves metadata about AWS networking components, such as VPCs, subnets, and security configurations.
- RDS: Retrieves metadata about RDS database clusters, which includes ID, engine, status, endpoint, security groups, availability zone, subnet group, public accessibility, tags, and region name.
- S3 Buckets: Retrieves metadata about S3 buckets, which includes name, creation date, and region name.
- Security Hub API: Retrieves metadata about security findings and insights from AWS Security Hub across connected organizational resources.
AWS resources are mapped as assets, including accounts.
[]
![The AWS Accounts, AWS EC2, AWS ECR, AWS ECR Findings, AWS EKS Clusters API, AWS Inspector Findings, AWS Network, AWS RDS, AWS S3 Buckets, and AWS Security Hub API tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-aws-connectors/aws-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [Secret Key](#param1)
- [Role ARN - Single Account](#param2)
- [Role ARN - Multiple Accounts](#param3)
[]
This authentication method uses an AWS access key and secret key to fetch data from a single AWS account. This method cannot be used for the AWS accounts stream.
The following are required parameters:
- [Access Key and Secret Key](#access-key-secret-key)
- [Region Names](#region-names-1)
[]
To create an AWS access key and secret key:
- Log in to the AWS IAM console.
- On the **Console Home** page, from the top right, select your username.
- From the drop-down menu, select **Security credentials**.
- On the **My security credentials** page, in the **Access keys** section, select **Create access key**. If you already have two access keys, **Create access key** is deactivated. You must delete an access key before you can create a new one.
- On the **Create access key** page, configure the following:
- On the **Access key best practices & alternatives** page, select **Other** and then select **Next**.
- On the **Set description tag - optional** page, optionally enter a description tag value for the access key. This adds a tag key-value pair to your IAM user, which can help you identify and update access keys later.
- Select **Create access key**.
-
On the **Retrieve access keys** page, select either **Show to reveal the value of your user's secret access key** or **Download .csv file**.
This is your only opportunity to save your secret access key.
- Select **Done**.
[]
Enter the region of the AWS service you are retrieving data from.
[]
This authentication method uses a single role ARN that allows you to fetch data from a single account or, if you are an admin with the appropriate access, from all org accounts.
The following are required parameters:
- [Region Names](#region-names-2)
- [Role ARN and External ID](#role-arn-external-id)
[]
Enter the region of the AWS service you are retrieving data from.
[]
The external ID is the optional unique identifier generated when creating a role ARN. It is used as an additional security measure when accessing your account.
To generate a role ARN and an external ID for setting up your AWS source, you must edit and save a CloudFormation JSON file with your required permissions and run the CloudFormation command:
- Open the CloudFormation JSON file.
- Copy the JSON file content into a text editor.
-
In the second action in AvalorPolicy, edit the [permissions list](/uvm/configuring-aws-connectors#single-multiple-role-arn-accounts) to cover those necessary for the data you want to retrieve.
The AWS accounts stream can optionally pull enriched data, and must include the relevant permissions from the [enrichment permissions list](/uvm/configuring-aws-connectors#aws-network-data-retrieval-permissions).
- Save the CloudFormation file locally as `avalor-aws-connector.json`.
- Generate a UUID.
-
Run the following CloudFormation role stack command.
`aws cloudformation create-stack \
--region <REGION> \
--stack-name AvalorStackIntegration \
--capabilities CAPABILITY_NAMED_IAM \
--template-body file://avalor-aws-connector.json \
--parameters ParameterKey=ExternalId,ParameterValue=<Generated UUID>`
Before you run the command, ensure that you do the following:
- Replace **<REGION>** with the region of the AWS service you are retrieving data from.
- Ensure the updated avalor-aws-connector.json file is located in your present working directory (i.e., the directory you are running the command in).
- Replace **<Generated UUID>** with the UUID you created.
After completion, you can find the RoleARNID and the ExternalID in the stack Output tab.
[]
This authentication method uses Role ARNs to allow you to fetch data from multiple accounts.
The following are required parameters:
- Region Names
- Role ARNs List
- (optional) External ID
To securely and efficiently retrieve data from multiple AWS accounts, create an AWS StackSet, which allows you to deploy and manage AWS CloudFormation stacks across multiple AWS accounts and regions from a single account.
Ensure that you are signed in to an organization, or management, account. To create an AWS StackSet:
- [Create a CloudFormation file](#create-cloudformation-file)
- [Create a stack set](#create-stack-set)
- [Create stack instances](#create-stack-instances)
- [List all the accounts in the organization](#list-accounts-organization)
[]
To create a CloudFormation file:
- Generate a UUID.
- Copy and save the content of the CloudFormation JSON file locally as `avalor-aws-connector.json`.
[]
To create a stack set:
-
Run the following command:
`aws cloudformation create-stack-set \
--stack-set-name AvalorStackIntegration \
--template-body file://avalor-aws-connector.json \
--capabilities CAPABILITY_NAMED_IAM \
--permission-model SERVICE_MANAGED \
--parameters ParameterKey=ExternalId,ParameterValue=<Generated UUID> \
--auto-deployment Enabled=true,RetainStacksOnAccountRemoval=false`
Before you run the command, ensure that you do the following:
- Ensure that the updated `avalor-aws-connector.json` file is located in your present working directory (i.e., the directory you are running the command in).
- Replace **<Generated UUID>** with the UUID you created in [Step 1](#create-cloudformation-file).
- To confirm that your stack set was created, run the `aws cloudformation list-stack-sets` command. Your new stack set is listed in the results.
[]
To create stack instances, run the following command:
`aws cloudformation create-stack-instances \
--stack-set-name AvalorStackIntegration \
--deployment-targets OrganizationalUnitIds='["<organization-root-ID>"]' \
--regions '["<region-name>"]'`
Before you run the command, ensure that you do the following:
- Replace **<organization-root-ID>** with your organization root ID to deploy to all accounts in your organization.
- Replace **<region-name>** with one region to specify where the stack instance is created. Specifying a region is required as CloudFormation operates within a regional context. The specified region (e.g., us-east-1) does not limit the scope of IAM resources. They remain global and available in all regions.
[]
To list all accounts in the organization:
- In the organization, or management, account, copy and save CloudFormation JSON file content locally as `avalor-list-account-cf.json`.
-
To create a new stack, run the following command:
`aws cloudformation create-stack \
--stack-name avalor-list-account-stack \
--template-body file://avalor-list-account-cf.json \
--capabilities CAPABILITY_NAMED_IAM \
--parameters ParameterKey=ExternalId,ParameterValue=<Generated UUID>`
Before you run the command, ensure that you do the following:
- Ensure that the updated `avalor-list-account-cf.json` file is located in your present working directory (i.e., the directory you are running the command in).
- Replace **<Generated UUID>** with the UUID you created in [Step 1](#create-cloudformation-file).
You can assume the roles in each account within the organization from your code.
Retrieval
In the source setup Retrieval section, set the (Optional AWS ACCOUNTS) Include The Following Network Data drop-down menu filters and specifications. Select the data types to include in the ingestion scope. When selecting network data, add the relevant permissions to your permissions list in the CloudFormation file. To retrieve network data from all accounts, ensure that you attach the permissions to the root/organization account.
The Include the Following Network Data drop-down menu is applicable in the Network stream.
Roles and Permissions
Depending on which AWS stream you are using, determine the permissions required:
- [Single Role ARN Account and Multiple Role ARN Accounts](#single-multiple-role-arn-accounts)
- [AWS Network Data Retrieval Permissions](#aws-network-data-retrieval-permissions)
[]
The role ARN permissions are required for each AWS stream when using a single role ARN account or multiple role ARN accounts. Determine the permissions set you require to be used when generating your role ARNs.
-
-
-
-
-
-
-
-
-
-
-
-
[](/uvm/configuring-aws-connectors#aws-network-data-retrieval-permissions)
[](/uvm/configuring-aws-connectors#param2)
| **Connector Name** | **Data Retrieved** | **Permissions Required** |
| ------------------ | ------------------ | ------------------------ |
| AWS Security Hub API | Findings | securityhub:GetFindings |
| AWS Inspector Findings | Findings: Lists findings in your AWS environment. | inspector2:ListFindings |
| AWS ECR Findings | Findings: Returns the scan findings on the specified ECR, including severity description and status. | ecr:DescribeImageScanFindings |
| AWS EC2 | Resources: Returns EC2 instances data (e.g., ID, tags, network interfaces, image ID, hypervisor). | ec2:DescribeInstances |
| AWS RDS | Resources: Describes provisioned RDS instances. | rds:DescribeDBInstances |
| AWS ECR | Resources | ecr:ListImagesecr:DescribeImagesecr:DescribeRepositories |
| AWS EKS Clusters API | Resources | eks:ListClusterseks:DescribeCluster |
| AWS S3 Buckets | Resources | s3:ListAllMyBuckets |
| AWS Network | This stream can retrieve any of the following data types:Internet GatewayNat GatewayLoad BalancerVPC CidrVPC SubnetsAddressesNetwork Interfaces | Refer to the AWS Network Data Retrieval table. |
| AWS AccountsUse a single role ARN account for this stream. | Retrieves your organization account details. | organizations:ListAccountsThis permission should be attached to the root/organization account. |
[]
When connecting the AWS network stream, you can retrieve any of the data types from the table by adding the relevant permissions to your permissions list in the CloudFormation file. To retrieve network data from all accounts, ensure that you attach the permissions to the root/organization account.
| **Data Type** | **Permission Required** |
| ------------- | ----------------------- |
| Internet Gateway | ec2:DescribeInternetGateways |
| Nat Gateway | ec2:DescribeNatGateways |
| Load Balancer | elasticloadbalancing:DescribeLoadBalancers |
| VPC CIDR | ec2:DescribeVpcs |
| VPC Subnets | ec2:DescribeSubnets |
| Addresses | ec2:DescribeAddresses |
| Network Interfaces | ec2:DescribeNetworkInterfaces |