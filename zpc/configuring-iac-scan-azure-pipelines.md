# Configuring IaC Scan for Azure Pipelines
Source: https://help.zscaler.com/zpc/configuring-iac-scan-azure-pipelines
PDF: https://help.zscaler.com/pdf/com/en/1409721.pdf

This article provides step-by-step instructions to configure the Zscaler IaC Scan for Azure Pipelines.
The IaC Scan plugin scans and identifies security misconfigurations and policy violations in the IaC Terraform, Kubernetes, Helm, ARM, and CloudFormation templates for Azure pipeline jobs, and displays the scan results in the Azure console output.
Prerequisites
Ensure you use the [supported operating systems](/zpc/supported-os-versions-iac-scanning) only, otherwise the IaC integration fails.
Configuring the Zscaler IaC Scan Plugin for Azure Pipelines
To configure the Zscaler IaC Scan plugin for Azure:
- Go to **Administration**** **>**Version Control & CI/CD Systems**.
- On the **IaC Integrations **page, click **Add IaC Integration**.
[See image.](#add-azurepipeline)
- Under **General Information**:
- For **IaC Scanner Type**, select **CI/CD**.
- For **Platform**, select **Azure Pipelines**.
[See image.](#select)
- Click **Next**.
- Under **Configuration**:
- Enter the unique name for the Azure Pipeline, then click **Confirm**.
[See image.](#configname)
A Client ID and Client Secret Key are generated after confirmation. These values are required to authorize the Zscaler IaC Scan plugin to access the Azure Pipeline jobs.
[See image.](#copy)
- Copy the **Client ID** and **Client Secret Key**.
- [Complete the configuration steps on Azure DevOps.](#azureconfig)
- Return to the **Configuration** page in the ZPC Admin Portal, and click **Finish**.
The Azure DevOps account is displayed on the IaC Integrations page. However, the status of this account is displayed as **Pending**. When you complete the configuration steps explained above, the status changes to **Success** and the Azure DevOps URL is displayed for the account.
Viewing the IaC Scan Results for Azure Pipelines
ZPC generates a graphical report that contains details of the IaC scan results and policy violations detected in an Azure Pipeline job. You can see this report on Azure DevOps and also download the report as a CSV or PDF file.
To view the IaC scan results on Azure DevOps:
- Log in to Azure DevOps.
- In the left-navigation menu, click **Pipeline** to view the list of recently run Pipeline jobs.
- Click the required Pipeline job.
[See image.](#jobs)
- Click the **Zscaler IaC Scan** tab to view the report with the following details:
- **Scan Status**: The total number of scans and status (Passed, Failed, Skipped).
- **Severity**: The overall severity level of the policy violations (Critical, High, Medium, or Low).
- **F****ailed**, **Skipped**, and **Passed** tabs: The number of policies that were failed, skipped, and passed during the IaC scan. For each policy, you can see:
- **Policy Name**: The policy title. Click the arrow next to the policy to view:
- **Resource**: The name of the resource (e.g., the name of the AWS S3 bucket).
- **Resource Type**: The type of resource (e.g., `aws_s3_bucket`).​​​
- **File**: The name of the file that was scanned.
- **Line**: The line within the code that has misconfigurations.
- **Scan Status**: The status of the scan (Failed, Skipped, or Passed).
- **Policy ID**: The unique identification number for the security policy.
- **Severity**: The severity level of the policy violation (Critical, High, Medium, or Low).
[See image.](#report)
[![Add an Azure Pipeline integration](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-azure-pipelines/zpc-azurepipeline.png)
]
[![Select Azure Pipeline from the list of CI/CD tools](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-iac-selectazure-pipeline.png)
]
[![Add the configuration details](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-iac-config-azure-pipeline1.png)
]
[![Copy the client ID and client secret key](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-iac-azure-pipeline2.png)
]
[![Add the configuration parameters to the YAML file](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-yaml-parameters.png)
]
[![Sample YAML script](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-sample-yaml.png)
]
[![Add the client id and secret key to Azure Key Vault](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-azure-keyvault.png)
]
[![View the list of Pipeline jobs](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-azure-pipelines.png)
]
[![View the IaC scan results](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-microsoft-azure-pipeline/zpc-azure-scan-report.png)
]
[![Select the region where your tenant resides](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-azure-pipelines/zpc-region-azure.png)
]
- []Sign in to your Azure DevOps account.
Make sure you've downloaded the Zscaler IaC Scan plugin from the Visual Studio Marketplace and installed in the required Azure organization. To learn more, see the [Azure Documentation](https://docs.microsoft.com/en-us/azure/devops/marketplace/install-extension?view=azure-devops-2020&tabs=browser).
- Select **Pipelines** in the left-navigation menu, then select the Pipeline you want to edit. To learn how to create a new Pipeline, see the [Azure Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=java%2Ctfs-2018-2%2Cbrowser).
- Use the [task assistant](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/yaml-pipeline-editor?view=azure-devops#use-task-assistant) to add tasks to the YAML pipeline. Click **Show assistant **to view the list of tasks in Azure DevOps. All third-party tools, including the Zscaler IaC Scan plugin, are called Tasks in Azure DevOps.
- Select Zscaler IaC Scan from the list.
- Fill in the required configuration parameters:
- **Region**: Select the region (EU, US, or Custom) where your tenant resides.
[See image.](#region)
- **Client ID**: Paste the value you copied on the ZPC Admin Portal.
- **Client Secret**: Paste the value you copied on the ZPC Admin Portal.
If you want to secure the Client ID and Client Secret, you can add the values to the Azure Key Vault and specify the parameters in the YAML pipeline. [See image.](#keyvault) To learn more, see the [Azure DevOps Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/release/key-vault-in-own-project?view=azure-devops&tabs=portal).
- **IaC Directory to scan**: Enter the name of the directory that must be scanned. If you don’t add a directory, then the entire repository is scanned.
- **IaC File to scan**: Enter the name of the IaC file that must be scanned.
- **Output format**: Enter the format (JSON, YAML, SARIF, or human) for displaying the scan results.
- **Fail build**: Select the checkbox to fail the build when misconfigurations and policy violations are detected in the code.
[See image.](#parameters)
- Click **Add**.
- The parameters are added to the YAML pipeline. Click on **Settings** within the script to edit the parameters if required.
[See image.](#yaml)