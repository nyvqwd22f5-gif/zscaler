# Creating a Gen AI Decoy in AWS
Source: https://help.zscaler.com/deception/creating-gen-ai-decoy-aws
PDF: https://help.zscaler.com/pdf/com/en/1531617.pdf

Amazon Web Services (AWS) allows you to build generative AI (Gen AI) applications using various foundation models from leading companies. You can create a Gen AI decoy using the Amazon Bedrock-optimized foundation models. The Gen AI decoys are interactive, and you can customize the decoys to generate fake responses to lure attackers into entering more prompts. You can also log the prompts and responses between the adversary and Gen AI decoy to gain insights into the objectives of the adversaries.
Prerequisites
Before creating a Gen AI decoy in AWS, you must ensure that you have:
- Configured the [integration between AWS and Zscaler Deception](/deception/setting-cloud-deception-aws).
-
Enabled or disabled the [option to log AI prompts and responses](/deception/setting-cloud-deception-aws#zd-integration-aws-decoys) for the AWS account based on your preference.
When logging is enabled, an S3 bucket is created to store prompts and responses from the Gen AI models. This S3 bucket collects prompts and responses from all Gen AI applications in that AWS account, including the legitimate Gen AI applications. However, only those prompts and responses pertaining to the Gen AI decoys created by Deception are sent to the Zscaler Deception Admin Portal. If you want to avoid storing (temporary) prompts and responses from the legitimate Gen AI applications in the S3 bucket, ensure that the Gen AI decoys are deployed in a different AWS account that does not contain any legitimate Gen AI applications.
- Obtained the necessary CloudShell command for the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Creating a Gen AI Decoy
To create a Gen AI decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **GenAI**.
-
Click **Add Decoy**.
[See image.](#add-decoy-button)
The **GenAI Decoy **window appears.
-
In the **GenAI Decoy **window:
- **Name**: Enter a name for the Gen AI decoy application.
- **Account ID**: Select the Account ID associated with the AWS account into which the decoy must be deployed.
-
**Region**: Select the AWS region where the decoy must be deployed.
Ensure that the foundation model you want to deploy is [available in the AWS region](https://docs.aws.amazon.com/bedrock/latest/userguide/models-regions.html).
- **Provider**: Select the provider whose foundation model must be used for creating the decoy.
-
**Model**: Select the foundation model that must be used for creating the decoy. This option appears only after selecting the provider.
Only the foundation models optimized for Amazon Bedrock are supported.
- **Description**: Enter a description for the decoy.
-
**Instructions**: Enter instructions for the Gen AI decoy to customize how it responds to prompts. The instructions are given as Gen AI prompts.
If you use the default instructions, ensure that you replace the placeholder texts with appropriate values.
[See image.](#gen-ai-decoy-window)
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Click the **CloudShell** icon on the navigation bar to launch AWS CloudShell.
[See image.](#cloudshell-icon)
The **AWS CloudShell** window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
Enter the option to deploy Gen AI decoys and press `Enter`.
The deployment script detects the Account ID and deploys the Gen AI decoys to the selected regions.
[See image.](#cloudshell-window)
If you want to add multiple Gen AI to AWS, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the Gen AI decoy is added to AWS. The deployment status is indicated by the icon next to the name of the decoy in the Gen AI decoys table (Deceive > Cloud Deception > AWS > GenAI) within the Zscaler Deception Admin Portal. To learn how to configure lures using Gen AI decoys, see [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys).
[]![Add Decoy button highlighted in the GenAI page](/downloads/deception/deceive/cloud-deception/aws/creating-generative-ai-decoy-aws/deception-add-decoy-button-gen-ai.png)
[]![configuring a generative AI decoy in AWS](/downloads/deception/deceive/cloud-deception/aws/creating-generative-ai-decoy-aws/deception-gen-ai-decoy-window.png)
[]![Option to launch AWS CloudShell in AWS Management Console](/downloads/deception/deceive/cloud-deception/aws/creating-generative-ai-decoy-aws/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![AWS CloudShell window with the option to deploy GenAI decoys highlighted](/downloads/deception/deceive/cloud-deception/aws/creating-generative-ai-decoy-aws/deception-gen-ai-cloud-shell-option.png)