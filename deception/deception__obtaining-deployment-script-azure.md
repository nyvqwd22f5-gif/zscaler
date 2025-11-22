# Obtaining the Deployment Script for Azure
Source: https://help.zscaler.com/deception/obtaining-deployment-script-azure
PDF: https://help.zscaler.com/pdf/com/en/1531566.pdf

Zscaler Deception relies on a deployment script to propagate changes and sync settings between Deception and Microsoft Azure. You can obtain the deployment script using one of the following methods:
- [Automated Download Method](#zd-direct-download-script)
- [Manual Download Method](#zd-manual-download-script)
[]Using this method, you can obtain a PowerShell command that automatically downloads and runs the deployment script when executed via Azure's Cloud Shell. To obtain the command:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Settings**.
- Click **Download Deployment Script**.
-
In the **Download Script Deployment** window that appears, copy the command from the **Automated: Run the following command in Azure Cloud Shell** section and save it for later use.
[See image.](#zd-download-script-window-direct)
[]Using this method, you can download the deployment script as a PSM1 file, upload it to the Azure cloud, and run the script using a PowerShell command obtained from the Zscaler Deception Admin Portal. To obtain the command and script:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Settings**.
- Click **Download Deployment Script**.
- In the **Download Script Deployment** window:
-
Click **Download**.
[See image.](#zd-scrip-download)
The deployment script is downloaded to your system.
-
Copy the command from the **Manual: Download the script and run the following command in Azure Cloud Shell** section, and save it for later use.
[See image.](#zd-download-script-window-manual)
- Sign in to the [Azure Portal](https://portal.azure.com).
-
Click the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-launch-powershell-azure)
- In the **Cloud Shell** window:
-
Click the **Upload/Download Files **icon, then select **Upload**.
[See image.](#zd-azure-upload)
- Choose the deployment script file (.psm1) that you downloaded to your system to upload it to Azure.
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/azure/obtaining-deployment-script-azure/zscaler-deception-copy-azure-script-automated.png)
[]![A screenshot capturing the option to download deployment script](/downloads/deception/deceive/cloud-deception/azure/obtaining-deployment-script-azure/zscaler-deception-download-azure-script-manual.png)
[]![A screenshot capturing the Download Deployment Script window](/downloads/deception/deceive/cloud-deception/azure/obtaining-deployment-script-azure/zscaler-deception-copy-azure-script-manual.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/prerequisites-azure-decoy-deployment/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing file upload option on Azure Cloud Shell](/downloads/deception/deceive/cloud-deception/azure-decoys/prerequisites-azure-decoy-deployment/zd-azure-shell-upload.png)