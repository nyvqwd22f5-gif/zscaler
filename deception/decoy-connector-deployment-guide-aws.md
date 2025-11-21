# Decoy Connector Deployment Guide for AWS
Source: https://help.zscaler.com/deception/decoy-connector-deployment-guide-aws
PDF: https://help.zscaler.com/pdf/com/en/1531275.pdf

This deployment guide provides information on prerequisites, how to deploy a Decoy Connector on Amazon Web Services (AWS), how to configure the network interface, and how to connect the Decoy Connector to the Zscaler Deception Admin Portal.
Prerequisites
Before deploying a Decoy Connector, Zscaler strongly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- Ensure that you have inbound access to TCP port 22 to the Decoy Connector's management IP address.
-
Ensure that you have outbound access to TCP port 443 from the Decoy Connector's management IP address to the following hosts:
- Deception Admin Portal
- Aggregator
- ib.smokescreen.io
- rs.smokescreen.io
If required, you can [configure proxy for a Decoy Connector](/deception/configuring-proxy-settings-decoy-connector) and pass the network connections through the proxy server. However, you must turn off all inspection features for the hosts in the preceding list and also ensure that the proxy provides unfiltered access to TCP port 443 for these destinations.
- Ensure that you have:
- An AWS account with admin privileges to do the following:
- View the AWS Account ID.
- Create Amazon EC2 instances.
- Create and manage security groups.
- Access T3.small (or larger) instance type.
- 50 GB disk storage. An SSD-backed storage is recommended.
Deploying a Decoy Connector on AWS
Follow these steps to deploy a Decoy Connector on AWS:
- [Step 1: Deploy the Decoy Connector on AWS](#deloy-decoy-connector-aws)
- [Step 2: Add and Connect the Decoy Connector to the Deception Admin Portal](#connect-decoy-connector)
[]To deploy a Decoy Connector on AWS:
- [a. Launch an EC2 instance using the Deception Admin Portal AMI.](#launch-ec2-aws)
- [b. Create an additional network interface on AWS.](#create-network-interface-aws)
- [c. Attach the network interface to the EC2 instance.](#attach-network-interface-aws)
[]Share your AWS account ID and the region in which you want to create decoys with the Zscaler Deception team. The Deception team then shares an Amazon Machine Image (AMI) on your AWS account. You can use this AMI to create an Amazon EC2 instance.
- Log in to the AWS Management Console.
- Click **EC2**.
-
In the left-side navigation, go to **Images** > **AMIs**.
[See image.](#navigate-ami-aws)
-
On the **Amazon Machine Images (AMIs)** page, select **Private images** from the drop-down menu.
[See image.](#select-private-ami-option)
-
Select the AMI that is shared by the Deception team, and then click **Launch instance from AMI**.
[See image.](#select-zscaler-ami)
- On the **Launch an instance **page:
-
(Optional) In the **Name and tags** section, click **Add additional tags**, and enter the following:
-
**Key: **Enter `Name`.
Zscaler recommends adding a **Name **tag to identify the instance in the future.
- **Value**: Enter `Decoy Connector`.
- **Resource types**: Select **Instances**, **Volumes**, and **Network Interfaces**.
[See image.](#add-name-tag)
Repeat these steps to add more tags as required.
-
In the **Instance type **section, click the **Instance type** drop-down menu and select an instance type. Zscaler recommends selecting a t3.small or larger instance type.
[See image.](#select-t3-small-instance)
-
In the **Key pair (login)** section, select an existing key pair from the **Key pair name **drop-down menu. Alternatively, you can create a new key pair by clicking **Create new key pair**.
[See image.](#configure-key-pair)
-
In the **Network settings **section, click **Edit**,** **and configure the following:
- **VPC**: Select a network VPC from the drop-down menu.
- **Subnet**: Select a subnet from the drop-down menu.
- **Firewall (security groups)**: Click **Create security group **or **Select existing security group **to use an existing security group that allows inbound access to port 22.
[See image.](#configure-instance-details)
-
In the **Configure storage **section, click **Edit**, and configure the following:
- (Optional) **Encrypted**: Select **Encrypted **from the drop-down menu.
- (Optional) **KMS Key**: Select a KMS key for EC2 instance.
[See image.](#add-storage)
-
Review the details in the **Summary **section and click **Launch instance**.
[See image.](#review-launch-ec2-instance)
-
Verify that the **Instance state** is running.
[See image.](#instance-running)
The EC2 instance must have two or more network interfaces. A minimum of two interfaces is required for the Decoy Connector and one interface for the management IP. Also, each additional interface can host only one network decoy.
[]Based on the type of the instance used, AWS limits the number of network interfaces you can attach to it. For example, if you use a T3 small instance, you can attach only three network interfaces. To learn more, see [Interface Limitations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html#AvailableIpPerENI).
- In the AWS Management Console, click **EC2**.
-
In the left-side navigation menu, go to **Network & Security** > **Network Interfaces**.
[See image.](#navigate-network-interface)
-
On the **Network interfaces** page, click **Create network interface**.
[See image.](#create-network-instance)
- On the **Create network interface** page:
- In the Details section, configure the following:
- **Description**: Enter a description for the network interface.
- **Subnet**: Select the **Subnet** in which you must create a subnet.
-
**Private IPv4 address**: Select **Auto-assign **to allow Amazon EC2 to select an IPv4 address from the subnet or select **Custom** to enter your preferred IPv4 address for the network interface.
[See image.](#configure-network-interface-details)
-
In the **Security groups** section, select one or more security groups to which the network interface must be associated.
[See image.](#configure-security-group)
Zscaler recommends an **Allow All** security group so that Deception can send alerts on any traffic that is destined for a decoy.
- Click **Create network interface**.
[]Repeat the following steps for each additional network interface that you want to attach to the Decoy Connector EC2 instance.
- In the AWS Management Console, click **EC2**.
-
In the left-side navigation menu, click **Instances**.
[See image.](#navigate-instances-aws)
-
Select the EC2 instance that is created for the Decoy Connector.
[See image.](#select-instance)
-
On the **Instances** page, go to **Actions** > **Networking** > **Attach network interface**.
[See image.](#attach-network-interface-option)
-
Select the network interface that you created.
[See image.](#attach-network-interface)
- Click **Attach**.
- After you attach the additional network interfaces, stop the EC2 instance and then start it again.
[]You need to [add the Decoy Connector and connect it to the Deception Admin Portal.](/deception/adding-connecting-decoy-connector-admin-portal)
[]![The left-side navigation in AWS with the AMIs option](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-select-ami.png)
[]![The AMIs page in AWS with the option to view private images](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-select-private-images.png)
[]![AMIs page in AWS with the option to launch an instance](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-launch-aws-instance.png)
[]![Selecting instance type for an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-select-t3_0.png)
[]![Configuring networking settings for an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-network-settings-aws-dc_0.png)
[]![Adding a storage volume for an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-storage-dc_0.png)
[]![Configuring names and tags for an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-tags.png)
[]![Summary of an EC2 isntance before launching the instance](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-summary.png)
[]![Configuring key pair for an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-key-pair-aws-dc.png)
[]![Instances page in AWS with the EC2 instance created for the Decoy Connector](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-instance-running.png)
[]![Left-side navigation in AWS with the Network interfaces option](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-left-side-navigation-network-interfaces_0.png)
[]![Network interfaces page in AWS with the option to create a network interface](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-create-network-interface.png)
[]![Configuring a network interface in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-network-interface-aws-dc.png)
[]![Selecting a security group for the network interface](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-security-groups.png)
[]![Left-side navigation AWS with the Instances option](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-instances.png)
[]![Instances page in AWS with the instance created for Decoy Connector](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-select-instance.png)
[]![Instances page in AWS with the option to attach a network interface](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-attach-option.png)
[]![Attaching network interface with an EC2 instance in AWS](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-amazon-web-services/deception-aws-dc-attach-ni.png)