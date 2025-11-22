# Creating a DynamoDB Decoy in AWS
Source: https://help.zscaler.com/deception/creating-dynamo-db-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531502.pdf

DynamoDB is a NoSQL, key-value pair database in Amazon Web Services (AWS). You can create DynamoDB decoy databases to lure adversaries that are looking for databases to disrupt services or steal data.
Prerequisites
Before creating a DynamoDB decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating a DynamoDB Database Decoy
To create a DynamoDB database decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **DynamoDB**.
-
Click **Add Decoy**.
[See image.](#zd-ddb-tab-aws)
The **DynamoDB Decoy** window appears.
-
In the **DynamoDB** **Decoy** window:
- **Name**: Enter a name for the DynamoDB database decoy.
- **Account ID**: Select the AWS Account ID associated with the AWS account in which you want to deploy the decoy.
- **Region**: Select the AWS region in which you want to deploy the decoy.
- **Description**: Enter a description relevant to the DynamoDB database decoy.
- **Partition Key**: Enter the name of the partition key for the DynamoDB database decoy.
- **Partition Key Type**: Select the data type of the partition key from the drop-down menu.
- **Sort Key**: Enter the name of the sort key for the DynamoDB database decoy.
- **Sort Key Type**: Select the data type of the sort key from the drop-down menu.
[See image.](#zd-ddb-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws-ddb)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy DynamoDB database decoys and press `Enter`.
The deployment script detects the Account ID and deploys the DynamoDB decoys to the selected regions.
[See image.](#zd-run-script-aws-ddb)
If you want to add multiple DynamoDB database decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the DynamoDB database decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the DynamoDB database decoys table (Deceive > Cloud Deception > AWS > DynamoDB) within the Zscaler Deception Admin Portal. To learn how to configure lures using DynamoDB database decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the DynamoDB tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-dynamo-db-decoy-aws/zscaler-deception-add-dynamo-db_0.png)
[]![A screenshot capturing the DynamoDB decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-dynamo-db-decoy-aws/zscaler-deception-dynamo-db-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-dynamo-db-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-dynamo-db-decoy-aws/deception-cloud-shell-option-dynamo-db-decoys.png)