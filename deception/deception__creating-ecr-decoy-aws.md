# Creating an ECR Decoy in AWS
Source: https://help.zscaler.com/deception/creating-ecr-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531501.pdf

An Elastic Container Registry (ECR) is a service in Amazon Web Services (AWS) that hosts Docker or Open Container Initiative (OCI) images. You can create an AWS ECR decoy (public or private) to detect the following attack paths:
- Pull: Adversaries look for images in the container registry to access the files to extract credentials or steal application code.
- Push: Adversaries can attempt supply chain attacks by pushing a vulnerable image to a container registry for persistence.
You can also use a [landmine policy](/deception/about-policies) to lure attackers to ECR decoys by adding URLs and credentials.
Prerequisites
Before creating an ECR decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating an ECR Decoy
To create an ECR decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **ECR**.
-
Click **Add Decoy**.
[See image.](#zd-ecr-tab-aws)
The **ECR Decoy** window appears.
-
In the **ECR Decoy** window:
- **Name**: Enter a name for the ECR decoy.
- **Account ID**: Select the Account ID associated with the AWS account in which you want to deploy the decoy.
- **Visibility**: Select **Public** from the drop-down menu** **if you want the ECR decoy to be accessible to anyone using the URI. Otherwise, select **Private** to limit access to the ECR decoy to internal adversaries.
- **Description**: Enter a description relevant to the ECR decoy.
[See image.](#zd-ecr-aws-decoy-add)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#zd-launch-cloudshell-aws-ecr)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
- Enter the option to deploy ECR decoys and press `Enter`.
[See image.](#zd-run-script-aws-ecr)
If you want to add multiple ECR decoys to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the ECR decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the ECR decoys table (Deceive > Cloud Deception > AWS > ECR) within the Zscaler Deception Admin Portal. In addition, the **URI **value is automatically generated and associated with the public ECR decoys. The **URI **value is also shown in the ECR decoys table. To learn how to configure lures using ECR decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![A screeshot capturing the ECR tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-ecr-decoy-aws/zscaler-deception-add-ecr-decoy.png)
[]![A screenshot capturing the ECR decoy window](/downloads/deception/deceive/cloud-deception/aws/creating-s3-decoy-aws/zscaler-deception-ecr-decoy-window.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-ecr-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/creating-ecr-decoy-aws/deception-cloud-shell-option-ecr-decoys.png)