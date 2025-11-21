# Creating a VM Image Decoy in AWS
Source: https://help.zscaler.com/deception/creating-vm-image-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531503.pdf

Virtual machine (VM) images are used on Amazon Web Services (AWS) to launch new instances of your VMs. You can create a VM image decoy snapshot (public or private) that creates an EC2 instance temporarily in AWS, adds a callback script for detection, and creates a snapshot. Adversaries enumerate public [Amazon Machine Images](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html) (AMI) with keywords related to your organization in the AMI Catalog with the intention of stealing and accessing the file system by booting up a VM in their environment to extract credentials and exfiltrate sensitive data.
The EC2 instance is created using the t3.small/t2.small series available in the region of deployment. It persists for a duration for 5 minutes and is terminated after the snapshot is built. To learn more about EC2 instance types, refer to the [AWS documentation.](https://aws.amazon.com/ec2/instance-types/t3/)
Prerequisites
Before creating an AWS decoy, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating a VM Image Decoy in AWS
To create a VM image decoy in AWS:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **VM Image**.
-
Click **Add Decoy**.
[See image.](#zd-vmi-tab)
The **VM Image Decoy** window appears.
-
In the **VM Image Decoy** window:
- **Name**: Enter a name for the VM image decoy.
-
**Account ID**: Select the Account ID associated with the AWS account in which you want to deploy the decoy.
A Virtual Private Cloud (VPC) is created for each account where you deploy a VM Image decoy, and it is shared across all of your regions within the account.
- **Region**: Select the AWS region in which you want to deploy the decoy.
- **Description**: Enter a description relevant to the VM image decoy.
-
**Visibility**: Select **Public** from the drop-down menu** **if you want the VM image to be accessible to anyone. Otherwise, select **Private **to limit access to the VM image to internal adversaries.
If you want to set the **Visibility **to **Public**, ensure that the **Block public access for AMIs** setting in AWS is disabled in your region of deployment before deploying the decoy. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sharingamis-intro.html#enable-block-public-access-for-amis).
[See image.](#zd-vmi-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws-vmi)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy VM image decoys and press `Enter`.
The deployment script detects the Account ID and deploys the VM Image decoys to the selected regions.
[See image.](#zd-run-script-aws-vmi)
If you want to add multiple VM image decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the VM image decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the VM image decoys table (Deceive > Cloud Deception > AWS > VM Image) within the Zscaler Deception Admin Portal. In addition, the **Snapshot ID** and **AMI ID **values are automatically associated with the VM decoys. These values are also shown in the VM image decoys table. To learn how to configure lures using VM image decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the VM Image tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-vm-image-decoy-aws/zscaler-deception-add-vm-image-decoy_0.png)
[]![A screenshot capturing the VM Image decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-vm-image-decoy-aws/zscaler-decetpion-add-vm-image-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-vm-image-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1)_0.png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-vm-image-decoy-aws/deception-cloud-shell-option-vm-image-decoys.png)