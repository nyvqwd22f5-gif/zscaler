# Creating an IAM Decoy in AWS
Source: https://help.zscaler.com/deception/creating-iam-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531498.pdf

An Identity Access Management (IAM) user in Amazon Web Services (AWS) is a representation of a human user or a workload that uses IAM credentials to access AWS resources. You can create AWS decoy IAM users to detect any attempt to sign in using these decoy user credentials. These decoy users have access to all other AWS decoys. The most effective way to lure attackers using IAM decoys is to add these decoys to a [landmine policy](/deception/about-policies).
Prerequisites
Before creating an IAM decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating an IAM Decoy
To create an IAM decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **IAM**.
-
Click **Add Decoy**.
[See image.](#zd-aws-iam-tab)
The **IAM Decoy** window appears.
-
In the **IAM** **Decoy** window:
- **Name**: Enter a name for the IAM decoy.
-
**Account ID**: Select the Account ID associated with the AWS account in which you want to deploy the decoy.
In AWS, IAM users are common to all regions within an account, so IAM user decoys do not include an option to select a region.
- **Description**: Enter a description relevant to the IAM decoy.
[See image.](#zd-iam-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws)
The **AWS CloudShell** window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy IAM decoys and press `Enter.`
The deployment script detects the Account ID and deploys the IAM decoys to the selected regions.
[See image.](#zd-run-script-aws)
If you want to add multiple IAM decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the IAM decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the IAM decoys table (Deceive > Cloud Deception > AWS > IAM) within the Zscaler Deception Admin Portal. In addition, the **Access Key** value is automatically generated and associated with the IAM user decoys. The **Access Key** value is also shown in the IAM decoys table. To learn how to configure lures using IAM decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the IAM tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-iam-decoy-aws/zidentity-iam-account-add-decoy_1.png)
[]![A screenshot capturing the IAM decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-iam-decoy-aws/zscaler-deception-iam-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-iam-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-iam-decoy-aws/deception-cloud-shell-option-iam-decoys.png)