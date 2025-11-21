# Managing AWS Decoys
Source: https://help.zscaler.com/deception/managing-aws-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531510.pdf

You can manage your Amazon Web Services (AWS) decoys from the Zscaler Deception. All decoys created from the Zscaler Deception Admin Portal are tabulated under their respective decoy category tabs. Each table shows the details associated with each decoy in the category and also shows its deployment status. You can also edit or delete decoys by using the respective options from the decoys table.
Checking Deployment Status
At the time of integration, Deception deploys a health check lambda function on AWS. This function periodically checks all decoy resources deployed on AWS and updates their status to the Deception Admin Portal every 15 minutes. You can check the deployment status indicated by the icon next to the name of the decoy in the decoys table. The following icons are used to show the status of the decoys:
- ![Green status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-green-status-icon.png)
– Indicates a deployed state.
- ![Orange status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-orange-status-icon.png)
– Indicates an inactive state. This means the decoy no longer exists on AWS or one of its properties used to reference does not exist. This happens when the decoy or its resources are manipulated directly from AWS.
- ![Grey status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-grey-icon.png)
– Indicates a pending deployment state. This means that the decoy has been created or modified in the Deception Admin Portal, but the deployment script to propagate changes to the AWS cloud has not been initiated.
- ![Red status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-red-status-icon_0.png)
– Indicates a pending deletion state. This means that the decoy has been deleted from the Deception Admin Portal, but the deployment script to propagate changes to the AWS cloud has not been initiated.
[See image.](#zd-decoy-aws-status)
Editing or Deleting AWS Decoys
You can edit or delete the AWS decoys that you configured in the Deception Admin Portal. Such changes made to the AWS decoys in the Deception Admin Portal are propagated to the AWS cloud only after running the deployment script on the AWS CloudShell.
Prerequisites
Obtain the CloudShell command using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws)
- [Manual Download Method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws)
Editing an AWS Decoy
To edit an AWS decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS**.
-
Select the relevant decoy category tab. For example, if you want to edit an IAM user decoy, select the **IAM **tab.
[See image.](#zd-edit-decoy-tab)
- Make sure that the decoy you want to edit is in the **Not Deployed** state, and then click the **Edit **icon for the decoy.
- Modify the decoy details as per your requirements.
- Click **Save**.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Launch CloudShell by clicking the **CloudShell **icon on the top navigation bar.
[See image.](#zd-launch-cloudshell-aws-edit)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
- Enter the option to deploy the preferred decoy and press `Enter`.
[See image.](#zd-aws-script-run-setup-edit)
Upon successful execution of the script, the changes are propagated to the AWS cloud.
[]Deleting an AWS Decoy
To delete an AWS decoy:
- Go to **Deceive **> **Cloud Deception **> **AWS**.
-
Select the relevant decoy category tab. For example, if you want to delete an IAM user decoy, select the **IAM **tab.
[See image.](#zd-delete-decoy-tab)
- Locate the decoy you want to delete, and click the **Delete **icon.
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/) as an administrator.
-
Launch CloudShell by clicking the **CloudShell **icon on the top navigation bar.
[See image.](#zd-launch-cloudshell-aws-del)
The **AWS CloudShell **window appears.
-
In the **AWS CloudShell **window:
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-aws#zd-direct-download-script-aws) or [manual download method](/deception/obtaining-deployment-script-aws#zd-manual-download-script-aws).
- Enter the option to deploy the preferred decoy and press `Enter`.
[See image.](#zd-aws-script-run-del)
Upon successful execution of the script, the changes are propagated to the AWS cloud.
[]![A screeshot capturing the IAM tab in AWS Cloud Deception](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/deception-aws-edit-decoy.png)
[]![A screeshot capturing the IAM tab in AWS Cloud Deception](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/deception-aws-delete-decoy.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/deception-cloud-shell-option-manage-decoys.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/zscaler-deception-aws-cloudshell-launch_1%20(1).png)
[]![A screenshot capturing the deployment script running in AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/deception-cloud-shell-option-manage-decoys.png)
[]![A screenshot capturing status of AWS decoys](/downloads/deception/deceive/cloud-deception/aws/managing-aws-decoys/deception-aws-decoy-statuses.png)