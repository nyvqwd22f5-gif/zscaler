# Configuring IaC Scan for Terraform Cloud
Source: https://help.zscaler.com/zpc/configuring-iac-scan-terraform-cloud
PDF: https://help.zscaler.com/pdf/com/en/1412771.pdf

You can integrate the Zscaler IaC Scan with Terraform Cloud and scan the Terraform workspaces. The workspaces contain run tasks that generate a Terraform plan template. The IaC Scan performs a scan on the Terraform plan template every time a run task is triggered and detects misconfigurations and policy violations. To learn more, see [About Security Policies](/zpc/about-security-policies).
Prerequisites
Ensure you use the [supported operating systems](/zpc/supported-os-versions-iac-scanning) only, otherwise the IaC integration fails.
Configuring the Zscaler IaC Scan for Terraform Cloud
To configure the Zscaler IaC Scan for Terraform Cloud:
- Go to **Administration **> **Version Control & CI/CD Systems**.
- On the **Version Control & CI/CD Systems** page, click **Add IaC Integration**.
[See image.](#add-tfc-integration)
- Under **General Information**:
- For **IaC Scanner Type**, select **CI/CD**.
- For **Platform**, select **Terraform Cloud**.
[See image.](#selecttc)
- Click **Next**.
- Under **Configuration**, [generate an API token on Terraform Cloud.](#tf-steps) The API token authorizes ZPC to access the Terraform workspace and scan the run tasks.
- Paste the API token in the **Enter Your Terraform API Token** field.
[See image.](#configure)
If you want to use another API token for reauthorization at a later point in time, click the **Key** icon for the specific Terraform Cloud account and update the API token. [See image.](#tfc-token)
- Click **Next**.
- Under **Organization Selection**, select the required organization.
You can only add one organization at a time and you cannot select organizations that are already onboarded. Repeat the integration steps to add multiple organizations, even if they are within the same Terraform account.
[See image.](#t-org)
- Click **Next**.
- Under **Choose Workspaces**, select the workspaces that must be enabled for scanning.
[See image.](#tfc-workspace)
- Click **Next**.
- (Optional) Under **Advanced Settings**:
- **Run task**: By default, the post-plan task is enabled for scanning. Click the toggle to enable scanning for the pre-plan task. If you select pre-plan, then the IaC scan occurs in the pre-plan phase instead of the post-plan phase. To learn more, see the [Terraform Documentation](https://developer.hashicorp.com/terraform/cloud-docs/run/states).
- **Fail Check Criteria**: Select the required security threshold (Critical, High, Medium, or Low) that must be applied for the specific workspace.
If the Run task is mandatory, then IaC scan will fail the task if it has policy violations that match any of the security thresholds selected in step b. If the Run task is in advisory mode, then IaC scan will not fail the task even if there are policy violations. To learn more about advisory and mandatory enforcement levels, see the [Terraform Documentation](https://developer.hashicorp.com/terraform/cloud-docs/workspaces/settings/run-tasks).
You can apply a security threshold to each workspace. For example, you can fail a Run task that introduces **Critical** or **High** issues from a workspace that is used to deploy to a production environment. If the same Run task has a **Low** threshold and the code must be merged to a workspace that is used to deploy in a development environment, then you can pass the Run task. However, the alert notification is generated in both scenarios.
[See image.](#tfc-advanced)
- Click **Next**.
- Review the integration details. Click the **Edit** icon if you want to make any changes.
[See image.](#tfc-review)
- Click **Finish**.
The Terraform Cloud integration is successful and the organization is displayed on the **Version Control & CI/CD Systems** page.
- []Log in to the Terraform Cloud.
- Go to **User Settings**.
- Select **Tokens** in the left-side navigation.
- Click **Create an API token**.
You must use only the user API token, otherwise, you cannot proceed with the integration. The user API token allows ZPC to access the repositories for IaC scanning.
[See image.](#apitoken)
- Copy this API token.
Viewing the IaC Scan Results and Alerts
After the Terraform Run task is scanned, you can view the total number of policy violations along with the severity of these violations in the Terraform Cloud UI. You can see the total policies along with passed and failed findings. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource. You can see the policy title and ID, severity, and resource details after the line of code that has issues.
You can also directly navigate to the ZPC Admin Portal from the Terraform Cloud UI to view the IaC alerts that are generated for the specific policy violation.
To view the IaC scan results and alerts:
- In the Terraform Cloud UI, go to **Workspaces** > **Runs** to view the scan results.
- Scroll down to view the policy violations, then click **Details**.
[See image.](#scansummary)
You are redirected to the **Alerts** page in the ZPC Admin Portal if you are already logged in. If not, the ZPC login page is displayed.
- On the **IaC Alerts** tab, click the **Scan ID** to view the alert details.
[See image.](#scanid)
Resolving Failed Integrations
For failed integrations, the **Integration Status** is displayed as *Failed* in the ZPC Admin Portal. In this case, if you offboard the tenant or unsubscribe from the IaC service entitlement, then the integration is deleted from ZPC but the runtasks are not deleted from the Terraform workspace. You need to manually delete the runtasks.
If you don't delete the runtasks, then you might not be able to integrate the organization whenever you subscribe for the IaC service entitlement again.
[![Add a Terraform integration](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-add-terraform.png)
]
[![Select CI/CD Platform and Terraform Cloud](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-select.png)
]
[![Configure the terraform cloud account](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-config.png)
]
[![Choose the workspace for scanning](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraformworkspace.png)
]
[![Update the API token](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraformtoken.png)
]
[![Select the required Terraform organization](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-org.png)
]
[![Generate the API token in the Terraform portal](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-token.png)
]
[![Review the integration details](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-review.png)
]
[![View the scan summary on Terraform Cloud](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-alerts.png)
]
[![View the scan ID and alert details](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-scanidonzpc1.png)
]
[![Set up the advanced options](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-terraform-advancedoptions.png?1680862125)
]