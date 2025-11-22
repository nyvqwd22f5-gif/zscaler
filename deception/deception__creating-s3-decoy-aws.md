# Creating an S3 Decoy in AWS
Source: https://help.zscaler.com/deception/creating-s3-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531499.pdf

The Simple Storage Service (S3) is an object-based storage service on Amazon Web Services (AWS). You can create AWS S3 decoys and associate [file datasets](/deception/about-file-datasets). Optionally, these S3 bucket URLs can be added to a [landmine policy](/deception/about-policies) to add lures to the endpoints. The S3 decoys can detect the following attack paths:
- Public: Adversaries can enumerate public S3 storage accounts by using keywords related to an organization to find exposed storage account containers on the internet in an attempt to steal sensitive data.
- Private: Adversaries with compromised identities of your organization can target storage account containers that are accessible via the compromised identities.
Prerequisites
Before creating an S3 decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating an S3 Decoy
To create an S3 decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **S3**.
-
Click **Add Decoy**.
[See image.](#zd-aws-s3-tab)
The **S3 Decoy **window appears.
-
In the **S3 Decoy** window:
- **Name**: Enter a name for the S3 decoy.
- **Account ID**: Select the Account ID associated with the AWS account in which you want to deploy the decoy.
- **Region**: Select the AWS region in which you want to deploy the decoy.
- **ACL**: Use the drop-down menu to choose your preferred access control list for the container decoy:
- Select **Public **if you want the S3 decoy to be accessible to anyone.
- Select **Private **if you want the S3 decoy to be accessible only to internal adversaries.
- **Description**: Enter a description relevant to the S3 decoy.
- **File Dataset**: Select a file dataset that you want to be hosted within the S3 bucket.
[See image.](#zd-s3-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws-s3)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy S3 decoys and press `Enter`.
The deployment script detects the Account ID and deploys the S3 decoys to the selected regions.
[See image.](#zd-run-script-aws-s3)
If you want to add multiple S3 decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the S3 decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the S3 decoys table (Deceive > Cloud Deception > AWS > S3) within the Zscaler Deception Admin Portal. To learn how to configure lures using S3 decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the S3 tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-s3-decoy-aws/zscaler-deception-s3%20decoys_0.png)
[]![A screenshot capturing the S3 decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-s3-decoy-aws/zscaler-deception-s3-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-s3-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-s3-decoy-aws/deception-cloud-shell-option-s3-decoys.png)