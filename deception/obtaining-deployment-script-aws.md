# Obtaining the Deployment Script for AWS
Source: https://help.zscaler.com/deception/obtaining-deployment-script-aws
PDF: https://help.zscaler.com/pdf/com/en/1531567.pdf

Zscaler Deception relies on a deployment script to propagate changes and sync settings between Deception and Amazon Web Services (AWS). You can obtain the deployment script using one of the following methods:
- [Automated Download Method](#zd-direct-download-script-aws)
- [Manual Download Method](#zd-manual-download-script-aws)
To learn about the functions performed by the deployment script, see [Understanding the Functions of the Deployment Script (AWS)](/deception/understanding-functions-aws-deployment-script).
[]Using this method, you can obtain a CloudShell command that automatically downloads and runs the deployment script when executed via AWS CloudShell. To obtain the command:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
- Click **Download Deployment Script**.
-
In the **Download Script Deployment** window that appears, copy the command from the **Automated: Run the following command in AWS CloudShell **section and save it for later use.
[See image.](#zd-download-script-window-direct-aws)
[]Using this method, you can download the deployment script as a ZIP file, upload it to the AWS cloud, and run the script using a bash command obtained from the Zscaler Deception Admin Portal. To obtain the command and script:
- Go to **Deceive **> **Cloud Deception **> **AWS **> **Settings**.
- Click **Download Deployment Script**.
- In the **Download Script Deployment** window:
-
Click **Download**.
[See image.](#zd-scrip-download-aws)
- The deployment script is downloaded to your system.
-
Copy the command from the **Manual: Download the script and run the following command in AWS CloudShell** section, and save it for later use.
[See image.](#zd-download-script-window-manual-aws)
- Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
-
Click the **CloudShell** icon on the navigation bar.
[See image.](#zd-launch-powershell-aws)
- In the **CloudShell** window:
-
Click the **Actions **drop-down menu, then select **Upload file**.
[See image.](#zd-aws-upload)
- Choose the deployment script file (.zip) that you downloaded to your system to upload it to AWS.
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-copy-aws-script.png)
[]![A screenshot capturing the option to download deployment script](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-download-aws-manual-script.png)
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/aws/obtaining-deployment-script-aws/zscaler-deception-copy-aws-manual-script.png)
[]![A screenshot capturing the option to launch CloudShell in AWS](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-aws-cloudshell-launch.png)
[]![A screenshot capturing file upload option on AWS CloudShell](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-upload-zip.png)