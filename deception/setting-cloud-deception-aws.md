# Setting Up Cloud Deception with AWS
Source: https://help.zscaler.com/deception/setting-cloud-deception-aws
PDF: https://help.zscaler.com/pdf/com/en/1531508.pdf

This integration guide provides information on prerequisites and how to integrate Amazon Web Services (AWS) with Zscaler Deception to set up Cloud Deception by deploying various AWS-specific decoy resources.
Prerequisites
Before you set up Cloud Deception with AWS, ensure that you have:
- Access to an AWS Account with an Administrator role.
- AWS region information.
Setting Up Cloud Deception with AWS
Follow these steps to set up Cloud Deception with AWS:
- [Step 1: Configure the Integration between AWS and Deception](#zd-integration-aws-decoys)
- [Step 2: Configure the AWS Decoys](#zd-aws-decoys-setup)
- [Step 3: Configure Lures Using AWS Decoys](#zd-lures-aws)
[]To integrate AWS with Deception:
- Log in to the Zscaler Deception Admin Portal.
- Go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
- On the **Settings **page:
- Click **Add Account**.
-
In the **AWS Account Setting** window:
- Select **Enabled**.
- **Region**: Select the region of your AWS account from the drop-down menu.
- **Account ID**: Enter the account ID of the AWS account to which you want to deploy the decoys.
- **DB Option and Parameter group suffix**: Enter a value to use as a suffix with the option group and parameter group for [Relational Database Service (RDS) decoys](/deception/creating-rds-decoy-aws). This is required to prevent name conflicts.
-
(Optional) Select the **Enable GenAI Prompt Logging** option if you want to log the prompts and responses from the generative AI (Gen AI) decoys. The prompts and responses are recorded in the `aws gen ai input` and `aws gen ai ouput` on the [ThreatParse page](/deception/viewing-threatparse-details) with the **AWS GenAI Model was Invoked** rule.
When logging is enabled, an S3 bucket is created to store prompts and responses from the Gen AI models. This S3 bucket collects prompts and responses from all Gen AI applications in that AWS account, including the legitimate Gen AI applications. However, only those prompts and responses pertaining to the Gen AI decoys created by Deception are sent to the Zscaler Deception Admin Portal. If you want to avoid storing (temporary) prompts and responses from the legitimate Gen AI applications in the S3 bucket, ensure that the Gen AI decoys are deployed in a different AWS account that does not contain any legitimate Gen AI applications.
- (Optional) Click **Tags **and configure tags for AWS resources. To learn more, see [Creating and Managing Tags for AWS Resources](/deception/creating-and-managing-tags-aws).
[See image.](#zd-aws-settings-page)
- Click **Save.**
-
After the settings are updated, click **Download Deployment Script**.
[See image.](#zd-dds-button)
The **Download Deployment Script **window appears.
- In the **Download Deployment Script** window, obtain the CloudShell command using one of the following methods:
- [Automated Download Method](#zd-direct-download-script-aws-setup)
- [Manual Download Method](#zd-manual-download-script-aws-setup)
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar.
[See image.](#zd-launch-cloudshell-aws)
The **AWS CloudShell **window appears.
- In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/setting-cloud-deception-aws#zd-direct-download-script-aws-setup) or [manual download method](/deception/setting-cloud-deception-aws#zd-manual-download-script-aws-setup).
-
Enter the option to sync settings and press `Enter`.
[See image.](#zd-aws-script-run-setup)
Typically, your AWS account includes a Virtual Private Cloud (VPC) in each AWS region. However if no default VPC is found in the selected region, the deployment script prompts you to create a new VPC. To create a new VPC using the deployment script, you need to run the script again and append the `--cidr-block` parameter with the IP address range in CIDR notation. The following examples show how to use the `--cidr-block` parameter with the automated download and manual download scripts:
- [Create VPC using the automated download script](#zd-example-vpc-automated)
- [Create VPC using the manual download script](#zd-example-vpc-manual)
Upon successful execution of the script, all necessary resources are created on AWS and the information is communicated to the Deception Admin Portal. The script also installs a health function app that polls the AWS account every 15 minutes to check and update the health status of the deployed decoys. The following table lists all resources created or retrieved from AWS by the deployment script:
| Resource | Description |
| -------- | ----------- |
| Account ID | AWS Account ID |
| Security Group ID | An identifier of the security group created by the deployment script. |
| Logging Bucket | Created by the deployment script for logging resources. |
| Cloud Trail | Created by the deployment script for gathering logs (CloudTrial). |
| Log Access IAM User | An IAM user created to access logs. |
| Access Key ID | The Access Key ID of the IAM user created by the deployment script. |
| Secret Access Key | The Secret Access Key of the IAM user created by the deployment script. |
| Log Access IAM User Policy | A policy created by the deployment script for the Log Access IAM user. |
| Decoy's Health Check Lambda Function | A lambda function deployed to monitor and update the health status of the deployed decoys to the Deception Admin Portal. |
| Health Check Lambda Function Access Policy | A policy created by the deployment script that is attached to the lambda function for the health check. |
| IAM Decoy User Access Policy | A policy created by the deployment script that is attached to the decoy user to gain access to other decoys. |
[]curl -XGET --header "x-client-auth: SLODXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXFSKOM4FS" https://xxxxxxx.illusionblack.com/api/v2/decoys/cloud-deception/aws/generate-deployment-script > aws_decoy_deployment.zip &&rm -rf aws_decoy_deployment && unzip -o -qq aws_decoy_deployment.zip -d aws_decoy_deployment &&cd aws_decoy_deployment && node build/aws-decoy-deployment.js --cmc-host https://xxxxxxx.illusionblack.com --api-key SLODXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXFSKOM4FS --client-id <xxxxxxx> --cidr-block '10.10.5.0/26'
[]rm -rf aws_decoy_deployment && unzip -o -qq aws_decoy_deployment.zip -d aws_decoy_deployment &&cd aws_decoy_deployment && node build/aws-decoy-deployment.js --cmc-host https://xxxxxxx.illusionblack.com --api-key SLODXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXFSKOM4FS --client-id xxxxxxx --cidr-block '10.10.5.0/26'
[]After successful integration of AWS with Deception, you can deploy various AWS-specific decoy resources. To learn how to configure the AWS decoys, see:
- [IAM Decoys](/deception/creating-iam-decoy-aws)
- [S3 Decoys](/deception/creating-s3-decoy-aws)
- [RDS Decoys](/deception/creating-rds-decoy-aws)
- [ECR Decoys](/deception/creating-ecr-decoy-aws)
- [DynamoDB Decoys](/deception/creating-dynamo-db-decoy-aws)
- [VM Image Decoys](/deception/creating-vm-image-decoy-aws)
- [Gen AI Decoys](/deception/creating-gen-ai-decoy-aws)
[]After deploying the necessary decoys based on your requirements, you can configure the lures for the decoys. To learn how to configure lures using AWS decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]Using this method, you can obtain a CloudShell command that automatically downloads and runs the deployment script when executed via AWS CloudShell. To obtain the command, copy the command from the **Automated: Run the following command in AWS CloudShell **section and save it for later use.
[See image.](#zd-download-script-window-direct-aws-setup)
[]Using this method, you can download the deployment script as a ZIP file, upload it to the AWS cloud, and run the script using a bash command obtained from the Deception Admin Portal. To obtain the command and script:
- In the **Download Script Deployment** window:
-
Click **Download**.
[See image.](#zd-script-download-aws-setup)
The deployment script is downloaded to your system.
-
Copy the command from the **Manual: Download the script and run the following command in AWS CloudShell** section, and save it for later use.
[See image.](#zd-download-script-window-manual-aws-setup)
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
-
Click the **CloudShell** icon on the navigation bar.
[See image.](#zd-launch-powershell-aws-setup)
- In the **AWS CloudShell** window:
-
Click the **Actions **drop-down menu, then select **Upload file**.
[See image.](#zd-aws-upload-setup)
- Choose the deployment script file (.zip) that you downloaded to your system to upload it to AWS.
[]![A screeshot capturing the AWS Settings tab](/downloads/deception/deceive/cloud-deception/aws/setting-cloud-deception-aws/deception-aws-setting-save.png)
[]![A screenshot capturing the AWS Settings Page with Download Deployment Script Button Highlighted](/downloads/deception/deceive/cloud-deception/aws/setting-cloud-deception-aws/deception-aws-deployment-script.png)
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-copy-aws-script_0.png)
[]![A screenshot capturing the option to download deployment script](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-download-aws-manual-script_0.png)
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-copy-aws-manual-script_0.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-aws-cloudshell-launch.png)
[]![A screenshot capturing file upload option on AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-upload-zip.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-aws-cloudshell-launch.png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/setting-cloud-deception-aws/deception-cloud-shell-option-sync-settings.png)