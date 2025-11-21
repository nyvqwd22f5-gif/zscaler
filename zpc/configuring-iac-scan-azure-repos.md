# Configuring IaC Scan for Azure Repos
Source: https://help.zscaler.com/zpc/configuring-iac-scan-azure-repos
PDF: https://help.zscaler.com/pdf/com/en/1409716.pdf

This article provides step-by-step instructions for integrating the Zscaler IaC Scan app with Azure Repos. The integration enables the IaC Scan app to scan and monitor your Infrastructure-as-code (IaC) files for misconfigurations.
Prerequisites
Only the Azure DevOps organization owner can onboard the Azure organization and accounts. [See image.](#orgowner)
Before proceeding with the integration, you must enable and authorize the ZPC Admin Portal via OAuth to access the Azure organization and accounts.
- On the Azure DevOps console, go to **Organization Settings** > **Security **> **Policies**.
- Under **Application connection policies**, enable the **third-party application access via OAuth**. To learn more, see the [Azure DevOps documentation](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/authentication-guidance?view=azure-devops).
[See image.](#policy)
Configuring the Zscaler IaC Scan App for Azure Repos
To configure the Zscaler IaC Scan app for Azure Repos:
- Go to **Administration **>** Version Control & CI/CD Systems**.
- On the **IaC Integrations** page, click **Add IaC Integration**.
[See image.](#add-azurerepo)
- Under **General Information:**
- For **IaC Scanner Type**, select **Code Repository**.
- For **Platform**, select **Azure Repos**.
[See image.](#select)
- Click **Next**.
- []Under **Configuration**, click **Authorize App from Azure DevOps** to install the IaC Scan app in the Azure DevOps account. The authorization establishes the connection between Azure DevOps and the ZPC Admin Portal to enable IaC scanning of the Azure repositories.
- [Complete the Azure DevOps authorization.](#authorize)
[See image.](#configure)
- Click **Next**.
- Under **Organization**, select the required Azure organization.
[See image.](#orgs)
You can only add one organization at a time and you cannot select organizations that are already onboarded. Repeat the integration steps to add multiple organizations, even if they are within the same Azure account.
- Click **Next**.
- Under **Choose Azure Repositories**, select the checkboxes for the repositories that must be enabled for scanning.
The date and time format displayed is based on the browser locale.
[See image.](#azure-repos)
- Click **Next**.
- (Optional) Under **Advanced Settings**:
- **Scan on Push**: Click the toggle to scan the code for a push command. The IaC Scan app performs the scan in the background and triggers alert notifications for any policy violations and displays the alerts in the ZPC Admin Portal. To learn more, see [About Alerts](/zpc/about-alerts).
- **Include Paths**: Click the **Edit** icon to include the path of the specific folder within the repository that must be scanned. For example, if you define an include path for a single file, then only that file is scanned and all other files and folders within the repository are ignored. You can also use regular expressions (regex) to search for and include files or folders that must be scanned:
- [See regex patterns with examples](#regex-azure)
- **Fail Check Criteria**: Fail check criteria is applicable to only pull requests based on policy severity. Select the security threshold for the policy (Critical, High, Medium, or Low) from the drop-down list.
You can apply a security threshold to each repository. For example, if the fail check criteria is set as **Critical** and **High** and there are only violations with **Medium** or **Low** severity, then the Zscaler IaC Scan does not fail the pull request.
[See image.](#azure-advanced)
- Click **Finish**.
The integrated account is displayed on the **Version Control & CI/CD Systems** page.
Viewing the IaC Scan Results
The IaC Scan app scans the IaC repositories, detects policy violations, and displays the results within the code. You can see the total policies along with passed and failed findings. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource. You can see the policy title and ID, severity, and resource details after the line of code that has issues.
[See image.](#findings)
The ZPC service generates alerts for IaC policy violations. You can view these alerts in the ZPC Admin Portal. You can also configure alert notifications for ZPC to send email notifications to recipients or send the alert data to third-party tools. To learn more, see [About Alerts](/zpc/about-alerts).
Enabling Branch Protection
You can enable the branch protection settings on Azure DevOps to prevent the merging of code with the main branch if the code contains policy violations.
The option to enable branch protection is available after you run the Zscaler IaC scan once on any one pull request.
To enable the branch protection setting:
- Log in to the Azure DevOps UI.
- Go to **Repo** > **Branches**.
- Select the required branch that you want to protect.
- Click the **Settings** icon to the right, then select **Branch Policies**.
[See image.](#branchpolicy)
- Scroll down to the **Status Checks** section.
- Select **Zscaler IaC Scan** from the **Satus to check** drop-down menu.
- Select **Required** under **Policy requirement**.
[See image.](#set)
- Click **Save**.
Resolving Failed Integrations
Use Case 1
There can be scenarios where an Azure Repo integration that was working earlier is disrupted (e.g. when a user accidentally unauthorizes the Zscaler IaC Scan in Azure DevOps or if the authorization token is corrupted in the ZPC Admin Portal). Instead of deleting the integration and repeating the configuration steps again, you can reauthorize the existing integration.
When an integration fails, the **Integration Status** is displayed as *Failed* in the ZPC Admin Portal.
To reauthorize an Azure Repo integration:
- Go to **Version Control & CI/CD Systems**.
- Under **Version Control Systems**, click the **Azure Repos** tab.
- Search for the integration that has failed.
- Hover the mouse over the **Failed** status to see the following tooltip: "`Click here to reauthorize this integration.`"
[See image.](#tooltip)
- Click the tooltip to go to the **Configuration** page.
- Click **Authorize App from Azure DevOps** to re-establish the connection between Azure DevOps and the ZPC Admin Portal, and enable IaC scanning of the Azure repositories.
[See image.](#configpage)
A confirmation message appears indicating that the reauthorization is successful and you are redirected to the **Version Control & CI/CD Systems** page. The **Integration Status** is displayed as "Success" for that integration.
Use Case 2
For failed integrations, the **Integration Status** is displayed as *Failed* in the ZPC Admin Portal. In this case, if you offboard the tenant or unsubscribe from the IaC service entitlement, then the integration is deleted from ZPC but the webhooks are not deleted from the Azure repository. You need to manually delete the webhooks.
If you don't delete the webhooks, then you might not be able to integrate the Azure account whenever you subscribe for the IaC entitlement again.
- []Log in to your Azure DevOps account.
- Go through the list of actions that ZPC can perform on Azure DevOps.
- Click **Accept**.
You are redirected back to the **Configuration** page in the ZPC Admin Portal.
[![Add an AzureRepo integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-azurerepo.png)
]
[![Select code repository and Azure Repo as the platform](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-microsoft-azure/zpc-iac-azure-generalinfo.png)
]
[![Authorize the ZPC IaC Scan app for Azure DevOps organization](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-microsoft-azure-repos/zpc-iac-azure-config.png)
]
[![Choose the Azure repositories for scanning](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-azure-repos.png)
]
[![Select the Azure DevOps organizations for enabling scanning](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-microsoft-azure-repos/zpc-iac-azure-boarded-orgs.png)
]
[![Enable the third-party tool access via OAuth](/downloads/zpc/alerts/adding-iac-alert-rules/zpc-iac-azure-authorizetool.png)
]
[![Select the branch policy](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-microsoft-azure-repos/zpc-iac-azure-moreicon.png)
]
[![Set the policy for branch protection](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-microsoft-azure-repos/status-check.png)
]
[![The organization owner can configure Azure integrations](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-azure-org-owner.png)
]
[![Click the tooltip to re-authorize the integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-reauth-failed-integration.png)
]
[![Re-authorize the integration on the Configuration page](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-reauth-configscreen.png)
]
[![View the scan summary and policy findings](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-azurerepos-scanresult.png)
]
[![Set up the advanced options](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-azure-repos/zpc-azure-advanced.png)
]
[]
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| **Regex Pattern** | **Description** | **Example** |
| ----------------- | --------------- | ----------- |
| `/**/` | Match zero or more directories | If you type `charts/**`, then the following files are included:
`charts/docker.yml`
`charts/stub`
`charts/stub/config.yml`
`charts/server/conf/app1/app.yml` |
| `**/` | Match any directory/directories, start of pattern only | If you type `**/internal/test/**`, then the following files are included:
`root/internal/test/stub.txt`
`internal/test/stub.txt`
`/internal/test/server`
`root/internal/test` |
| `/**` | Match any directory/directories, end of pattern only | If you type `monorepo/**/terraform/**`, then the following files are included:
`monorepo/terraform/doc.tf`
`monorepo/app1/terraform`
`monorepo/app1/terraform/stub.yml`
`monorepo/app1/app2/terraform` |
| `*` | Match any non-separator character | If you type `*repo/**/terraform/**`, then the following files are included:
`monorepo/terraform/doc.tf`
`monorepo/app1/terraform`
`publicrepo/app1/terraform/stub.yml`
`newrepo/app1/app2/terraform` |
| `!` | Excludes all matches from the result set, start of pattern only | If you type `!**/internal/test/**`, then the following files are excluded:
`root/internal/test/stub.txt`
`internal/test/stub.txt`
`/internal/test/server`
`root/internal/test` |