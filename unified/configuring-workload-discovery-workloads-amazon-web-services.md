# Configuring Workload Discovery for Workloads in Amazon Web Services
Source: https://help.zscaler.com/unified/configuring-workload-discovery-workloads-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1518866.pdf

The workload discovery service is a Zscaler-managed service that discovers workloads in your Amazon Web Services (AWS) account. The service also fetches associated metadata such as user-defined tags and cloud service provider generated attributes. These user-defined tags and cloud service provider generated attributes are used in security policies.
Zscaler supports the following attributes:
- **GroupId**: The ID of the security group assigned to the attached Elastic Network Interface (ENI). This can identify the AWS Lambda function workload.
- **GroupName**: The name of the security group assigned to the attached ENI.
- **ImageId**: The ID of the image used to launch the instance.
- **PlatformDetails**: The platform. Zscaler also supports AWS Lambda and other services when not used in the context of Amazon Elastic Compute Cloud (EC2).
- **Vpc-id**: The ID of the virtual private cloud (VPC) that the ENI runs in.
- **IamInstanceProfile-Arn**: The Amazon Resource Name (ARN) of the Identify Access Management (IAM) instance profile.
Configuring Workload Discovery Services
To enable workload discovery, onboard your AWS account into the Zscaler Admin Portal. After your AWS account is added to the Admin Portal, create a configuration in your AWS account. To learn more about adding an AWS account, see [Adding an Amazon Web Services Account](/unified/adding-amazon-web-services-account). The following changes are required to add a configuration to your AWS account:
- [Create a Role](#AWSrole)
- [Update the Cloud Connector Role for SQS Permissions](#sqs)
- [Configure EventBridge](#eventbridge)
- [Namespace and Duplicate IP Addresses](#namespace-duplicate-ips)
[]
To create a role, you can either click the **Launch Cloudformation template in AWS console** option while [adding an AWS account](/unified/adding-amazon-web-services-account) in the Admin Portal or you can create it manually. To create a role, you need the following information:
- List of permissions:
- ec2:DescribeVpcs
- ec2:DescribeSubnets
- ec2:DescribeInstances
- ec2:DescribeNetworkInterfaces
- Optional list of permissions:
- ec2:DescribeIamInstanceProfileAssociations
- ec2:DescribeVpcEndpoints
- Trusted role
- External ID
[]You might encounter overlapping Classless Inter-Domain Routings (CIDRs). Adding a namespace makes them unique, so the IP addresses are not duplicates. If Zscaler detects a duplicate IP address, only one IP address is shown and all others are disregarded. You can see the number of duplicate IP addresses in the Admin Portal.
[See image.](#WTDNamespaceDuplicateIPs)
Zscaler offers a zero-touch configuration solution where the security admin does not need to add a configuration in the Cloud & Branch Connector Admin Portal. During deployment in AWS, add a tag to the VPC. The tag key is `zs:namespace` and the value is the name of the namespace you want to assign. The Zscaler discovery service discovers the `zs:namespace` tag through the standard tag discovery process and assigns all the workloads in that VPC to that namespace. The Zscaler discovery service also discovers any Gateway Load Balancer (GWLB) endpoints in that VPC and assigns the endpoint to the namespace. Then, the Zscaler discovery service builds a table. In this table, the discovered endpoint is assigned the namespace. If no GWLB exists or no namespace is defined, workloads are created in the default namespace unless the tag `zs:namespace` is set on the VPC.
[]The default polling time for the workload discovery service is 5 minutes, which means changes can take up to 5 minutes to be distributed for policy enforcement. This polling time is sufficient for the applications of many users. For other users using auto scaling groups (ASGs), Zscaler must be notified immediately. The Zscaler discovery service allows you to use EventBridge to trigger an update within a few seconds of an EC2 notification. You configure a rule in the EventBridge service of your account on the default bus. The rule sends a notification to an EventBridge bus in the Zscaler account assigned to your tenant. You can locate the name of the EventBridge on the account page of the Admin Portal. The format is an ARN. You must replace the `REGION` field, such as in the following example: `arn:aws:events:<``REGION``>:11111111111:event-bus/zscaler-bus-146530-zsdevel.net`.
To configure an EventBridge:
- Log in to the AWS Management Console.
- In the Search field, enter `EventBridge`. Select **Amazon EventBridge**. The Amazon EventBridge page appears.
- On the Amazon EventBridge page, under **Get started**, select **EventBridge Rule**.
- On the **Define rule detail** page, in the **Rule detail** section, configure the following:
- **Name**: Enter a name for the EventBridge.
- **Description - optional**: Enter a description for the EventBridge.
- **Event bus**: Select **default**.
- **Enable the rule on the selected event bus**: Enable this setting.
- **Rule type**: Select **Rule with an event pattern**.
-
Click **Next**.
[See image.](#WTDDefineruledetails)
- On the **Build event pattern** page, configure the following:
-
In the **Event Source** section, select **AWS events or EventBridge partner events**.
[See image.](#WTDSource)
- In the **Sample Event** section, do not configure any settings.
-
In the **Creation method** section, select **Use pattern form**.
[See image.](#WTDCreationmethod)
-
In the **Event pattern** section, configure the following:
- **Event source**: Select **AWS services**.
- **AWS service**: Select **EC2**.
- **Event type**: Select **EC2 Instance State-change Notification**.
- **Event Type Specification 1**: Select **Specific state(s)**.
- **Specific state(s)**: Select **pending**.
- **Event Type Specification 2**: Select **Any instance**.
- Click **Next**.
[See image.](#WTDEventpattern)
- On the **Select target(s)** page, in the **Target 1** section, configure the following:
- **Target types**: Select **EventBridge event bus**.
- **Target types**: Select **Event bus in a different account or Region**.
- **Event bus as target**: Enter the ARN from the Admin Portal. Replace the region field with the region the rule created.
- **Execution role**: Select **Create a new role for this specific resource**.
-
Click **Next**.
[See image.](#WTDTarget1)
- (Optional) Configure tags, then click **Next**.
- Review your settings, then click **Create**.
The workload discovery service communicates through API calls and a publish-subscribe mechanism based on the Amazon Simple Notification Service (SNS) and the Amazon Simple Queue Service (SQS). New tag discoveries are pushed through the SNS-SQS publish-subscribe mechanism to Cloud Connector. The SNS topic is in the Zscaler account, has all relevant changes to an account, and is protected by a resource-based policy. Cloud Connector be able to manage queues, receive messages, and subscribe to SNS. In a new deployment using Terraform, Zscaler adds the permissions. In an existing deployment, you must manually add permissions. For existing deployments, add the following permissions to the Cloud Connector role:
- sqs:DeleteMessage
- sqs:ReceiveMessage
- sqs:GetQueueUrl
- sqs:GetQueueAttributes
- sqs:SetQueueAttributes
- sqs:DeleteQueue
- sqs:CreateQueue
- sns:ListSubscriptions
- sns:Subscribe
- sns:Unsubscribe
[]
[]![The Regions section from the Partner Integrations page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/Namespace%20and%20Duplicate%20IPs.png)
![The Define rule detail page in the AWS Management Console](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/WTD%20Define%20Rule%20Detail.png)
[]
![Selecting Use pattern form as the creation method in the AWS Management Console](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/WTD%20Creation%20method.png)
[]
[]![Selecting AWS events or EventBridge partner events as the event source in the AWS Management Console](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/WTD%20Event%20Source.png)
![The Event pattern page and its details in the AWS Management Console](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/WTD%20Event%20pattern.png)
[]
![The Target 1 page and its details in the AWS Management Console](/downloads/cloud-branch-connector/administration/configuring-workload-tagging-settings-amazon-web-services/WTD%20Target%201.png)
[]