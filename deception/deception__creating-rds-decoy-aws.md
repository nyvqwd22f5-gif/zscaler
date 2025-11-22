# Creating an RDS Decoy in AWS
Source: https://help.zscaler.com/deception/creating-rds-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531500.pdf

The Relational Database Service (RDS) in Amazon Web Services (AWS) is a web service that allows you to set up and host relational databases (MySQL or PostgreSQL) on the cloud. You can create RDS decoy databases (public or private) based on MySQL or PostgreSQL to lure adversaries that are looking for databases to disrupt services or steal data. Optionally, the credentials of the master user of the database along with the URL can be added to a [landmine policy](/deception/about-policies) as a lure.
Zscaler Deception uses Amazon RDS's db.t3.micro instance type to create RDS decoys. To learn more about Amazon RDS instance types, refer to the [AWS Documentation](https://aws.amazon.com/rds/instance-types/).
Prerequisites
Before creating an RDS decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating an RDS Decoy
To create an RDS decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **RDS**.
-
Click **Add Decoy**.
[See image.](#zd-rds-aws-tab)
The **RDS Decoy** window appears.
-
In the **RDS Decoy** window:
- **Name**: Enter a name for the RDS database decoy.
-
**Account ID**: Select the Account ID associated with the AWS account in which you want to deploy the decoy.
A Virtual Private Cloud (VPC) is created for each account where you deploy a VM Image decoy, and it is shared across all of your regions within the account.
- **Region**: Select the AWS region in which you want to deploy the decoy.
- **Description**: Enter a description relevant to the RDS database decoy.
- **Engine Type**: Select a database type (**MySQL **or **PostgreSQL**) from the drop-down menu.
- **Engine Version**: Select a supported version of the database engine from the drop-down menu.
[See image.](#zd-rds-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws-rds)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy RDS database decoys and press `Enter`.
The deployment script detects the Account ID and deploys the RDS decoys to the selected regions.
[See image.](#zd-run-script-aws-rds)
If you want to add multiple RDS decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the RDS database decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the RDS decoys table (Deceive > Cloud Deception > AWS > RDS) within the Zscaler Deception Admin Portal. In addition, the **URI **value is automatically generated and associated with the public RDS decoys during the subsequent health check. The **URI **value is also shown in the RDS decoys table. To learn how to configure lures using RDS database decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the RDS tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-rds-decoy-aws/zscaler-deception-rds-decoy-add_0.png)
[]![A screenshot capturing the RDS Decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-rds-decoy-aws/zscaler-deception-rds-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-vm-image-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-rds-decoy-aws/deception-cloud-shell-option-rds-decoys.png)