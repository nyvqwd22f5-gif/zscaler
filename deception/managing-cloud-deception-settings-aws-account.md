# Managing Cloud Deception Settings for an AWS Account
Source: https://help.zscaler.com/deception/managing-cloud-deception-settings-aws-account
PDF: https://help.zscaler.com/pdf/com/en/1531565.pdf

You can edit or delete Cloud Deception settings configured for your Amazon Web Services (AWS) accounts from the Zscaler Deception Admin Portal.
Editing an AWS Account
Depending on whether the configurations are already propagated to AWS, the editing is either a single-step process (if the deployment script was never used on AWS) or a two-step process (if the deployment script was used at least once).
- [Step 1: In the Deception Admin Portal](#edit-aws-account-deception)
- [Step 2: In the AWS Management Console](#edit-aws-account-aws)
Deleting an AWS Account
Depending on whether the configurations are already propagated to AWS, the deletion is either a single-step process (if the deployment script was never used on AWS) or a two-step process (if the deployment script was used at least once).
You can delete AWS deception settings only if no AWS decoys are deployed. If you have already deployed AWS decoys, you must delete all decoys and run the deployment script first before deleting the settings.
- [Step 1: In the Deception Admin Portal](#zd-deception-portal-aws-delete)
- [Step 2: In the AWS Management Console](#zd-aws-portal-delete)
[]To initiate editing in the Deception Admin Portal:​​​​​
- Go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
-
Locate the account that you want to edit, and click the **Edit **icon.
[See image.](#edit-icon-aws-account)
The **AWS Account Setting **window appears.
-
In the **AWS Account Setting **window:
- **Enabled**: Select to modify the status of Cloud Deception for the AWS account.
-
**Enable GenAI Prompt Logging**: Select to modify the status of logging prompts and responses from [generative AI (Gen AI) decoys in AWS](/deception/creating-generative-ai-decoy-aws). The prompts and responses are recorded in the aws `gen ai input` and `aws gen ai ouput` on the [ThreatParse page](/deception/viewing-threatparse-details) with the **AWS GenAI Model was Invoked** rule.
When logging is enabled, an S3 bucket is created to store prompts and responses from the Gen AI models. This S3 bucket collects prompts and responses from all Gen AI applications in that AWS account, including the legitimate Gen AI applications. However, only those prompts and responses pertaining to the Gen AI decoys created by Deception are sent to the Deception Admin Portal. If you want to avoid storing (temporary) prompts and responses from the legitimate Gen AI applications in the S3 bucket, ensure that the Gen AI decoys are deployed in a different AWS account that does not contain any legitimate Gen AI applications.
- **Tags**: Click to configure tags for AWS resources. To learn more, see [Creating and Managing Tags for AWS Resources](/deception/creating-and-managing-tags-aws).
[See image.](#edit-window-aws-account)
- Click **Save**.
[]To complete deletion in the AWS Management Console:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
-
Launch AWS CloudShell.
[See image.](#launch-aws-cloudshell-for-edit)
The **CloudShell **window appears.
-
In the **CloudShell** window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
When prompted to continue with deletion, enter `y` and press `Enter.`
If you enter `n `and press `Enter`, then the deletion process is aborted, and the configuration is enabled again in the Deception Admin Portal.
[See image.](#aws-cloud-shell-options)
[]To initiate deletion in the Deception Admin Portal:​​​​​
- Go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
- Locate the account that you want to delete, and click the **Delete **icon.
[See image.](#zscaler-deception-aws-delete-option)
All decoys are marked for deletion and the configuration is disabled in the Deception Admin Portal.
If you have never run the deployment script on AWS, then the deletion process is completed with this step. If you have already used the deployment script either to sync the settings or deploy decoys, then proceed to [Step 2](/deception/deleting-aws-deception-settings#zd-aws-portal-delete) to complete the deletion process.
[]To complete deletion in the AWS Management Console:
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
-
Launch AWS CloudShell.
[See image.](#zd-powershell-launch-aws)
The **CloudShell **window appears.
-
In the **CloudShell** window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
-
When prompted to continue with deletion, enter `y` and press `Enter.`
If you enter `n `and press `Enter`, then the deletion process is aborted, and the configuration is enabled again in the Deception Admin Portal.
[See image.](#zd-complete-deletion-aws)
All resources created for [setting up Cloud Deception with AWS](/deception/setting-cloud-deception-aws) are deleted.
In some cases, the deployment script might fail to remove the entries of the AWS resources that were marked for deletion in the Deception Admin Portal. For example, manually removing AWS resources deployed by Deception from the AWS cloud can fail to remove entries of resources from the Deception Admin Portal if the resources are interdependent. If the deployment script fails to remove these entries, you need to use the **Force Delete **option.
- [See instructions](#force-delete-aws-settings)
- []In the Deception Admin Portal, go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
-
Click **Force Delete**. This option appears when the deletion process is started.
[See image.](#force-delete-button)
-
Confirm your action.
The AWS resource entries are removed from the Deception Admin Portal.
[]![List of AWS cloud accounts with the option to edit an account highlighted](/downloads/deception/deceive/cloud-deception/aws/managing-cloud-deception-settings-aws-account/deception-edit-aws-cloud-account.png)
[]![Editing AWS settings with some options highlighted](/downloads/deception/deceive/cloud-deception/aws/managing-cloud-deception-settings-aws-account/deception-aws-setting-window.png)
[]![A screenshot capturing the option launch Cloud Shell in AWS](/downloads/deception/deceive/cloud-deception/aws/deleting-aws-deception-settings/zscaler-deception-aws-cloudshell-launch_1%20(2).png)
[]![A screenshot capturing the prompt to continue deletion on AWS Cloud](/downloads/deception/deceive/cloud-deception/aws/deleting-aws-deception-settings/deception-cloud-shell-option-manage-decoys.png)
[]![A screenshot capturing the delete option in AWS Cloud Deception Settings](/downloads/deception/deceive/cloud-deception/aws/managing-cloud-deception-settings-aws-account/deception-delete-aws-cloud-account.png)
[]![A screenshot capturing the option launch Cloud Shell in AWS](/downloads/deception/deceive/cloud-deception/aws/deleting-aws-deception-settings/zscaler-deception-aws-cloudshell-launch_1%20(2).png)
[]![A screenshot capturing the prompt to continue deletion on AWS Cloud](/downloads/deception/deceive/cloud-deception/aws/deleting-aws-deception-settings/deception-cloud-shell-option-manage-decoys.png)
[]
![AWS Force Delete Option](/downloads/deception/deceive/cloud-deception/aws/managing-cloud-deception-settings-aws-account/deception-aws-setting-window-force-delete.png)