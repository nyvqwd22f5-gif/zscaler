# Configuring IaC Scan for GitLab
Source: https://help.zscaler.com/zpc/configuring-iac-scan-gitlab
PDF: https://help.zscaler.com/pdf/com/en/1392311.pdf

This article provides step-by-step instructions for integrating the Zscaler IaC Scan app with GitLab.
The Zscaler IaC Scan app scans and identifies security misconfigurations in the IaC Terraform, Helm, Kubernetes, and CloudFormation templates within GitLab. When you add or update the code and make a merge request, the IaC Scan app automatically triggers a scan of the IaC templates, identifies policy violations, and displays the scan results within the code. This allows you to fix the configuration errors before deployment, and ensure your code is secure and compliant with the security policies. To know more, see [About Security Policies](/zpc/about-security-policies).
You can configure only one GitLab integration per tenant.
Prerequisites
The administrator with an owner role can onboard the GitLab accounts and authorize the IaC Scan app to scan the IaC repositories.
Configuring the Zscaler IaC Scan App for GitLab
To configure the Zscaler IaC Scan app for GitLab:
- Go to **Administration **> **Version Control & CI/CD Systems**.
- On the **IaC Integrations** page, click **Add IaC Integration**.
[See image.](#add-gitlab)
- Under **General Information:**
- For **IaC Scanner Type**, select **Code Repository**.
- For **Platform**, select **GitLab**.
[See image.](#select-gitlab)
- Click **Next**.
- Click **Authorize Zscaler GitLab App**.
[See image.](#authorize)
- [Complete the authorization on GitLab.](#gitlabauthorize)
- Click **Next**.
- Under **Choose GitLab Repositories**, you can view the onboarded GitLab account and the list of repositories within this account. Select the checkbox for the repositories that must be enabled for scanning.
The date and time format is displayed as per the user's location.
[See image.](#gitlab-repo)
- Click **Next**.
- (Optional) Under **Advanced Settings**:
- **Scan on Push**: Click the toggle to scan the code for a push command. The IaC Scan app performs the scan in the background and triggers alert notifications for any policy violations and displays the alerts in the ZPC Admin Portal. To learn more, see [About Alerts](/zpc/about-alerts).
- **Include Paths**: Click the **Edit** icon to include the path of the specific folder within the repository that must be scanned. For example, if you define an include path for a single file, then only that file is scanned and all other files and folders within the repository are ignored. You can also use regular expressions (regex) to search for and include files or folders that must be scanned:
- [See regex patterns with examples](#regex-gitlab)
- **Fail Check Criteria**: Fail check criteria is applicable to only merge requests based on policy severity. Select the security threshold (Critical, High, Medium, or Low) for the policy from the drop-down list.
You can apply a security threshold to each repository. For example, you can fail a merge request that introduces **Critical** or **High** issues from a repository that is used to deploy to a production environment. If the same merge request has a **Low** threshold and the code must be merged to a repository that is used to deploy in a development environment, then you can pass the request. However, the alert notification is generated in both scenarios.
[See image.](#gitlab-advanced)
- Click **Finish**.
- []Sign in to your GitLab account.
- On the **GitLab Authorization** page, click **Authorize**.
After completing the authorization, you are redirected back to the **Configuration** page in the ZPC Admin Portal.
Viewing the IaC Scan Results
After you enable the selected repositories for scanning, the IaC Scan app performs a scan every time you add or update a code and make a merge request. The IaC Scan app identifies security misconfigurations and displays policy violations and remediation steps within the code. You can fix the issues and then merge the code.
You can see the total policies along with passed and failed findings. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource. You can see the policy title and ID, severity, and resource details after the line of code that has issues.
[See image.](#findings)
You can also see the remediation steps for resolving the issue.
[See image.](#gitlab-remediation)
The ZPC service generates alerts for the specific policy violations detected during the scan. You can view the list of alerts and policy violations in the ZPC Admin Portal. You can view these alerts in the ZPC Admin Portal. You can also configure alert notifications for ZPC to send email notifications to recipients or send the alert data to third-party tools. To learn more, see [About Alerts](/zpc/about-alerts).
Resolving Failed Integrations
Use Case 1
There can be scenarios where a GitLab integration that was working earlier has been disrupted (e.g. When a user accidentally unauthorizes the Zscaler IaC Scan in GitLab or if the authorization token is corrupted in the ZPC Admin Portal). Instead of deleting the GitLab account and repeating the configuration steps again, you can reauthorize the existing integration.
When an integration fails, the **Integration Status** is displayed as “Failed” in the ZPC Admin Portal.
To reauthorize a GitLab integration:
- Go to **Version Control & CI/CD Systems**.
- Under **Version Control Systems**, click the **GitLab** tab.
- Search for the integration that has failed.
- Hover the mouse over the **Failed** status to see the following tooltip: "`Click here to reauthorize this integration.`"
[See image.](#tooltip)
- Click the tooltip to go to the **GitLab Authorization** page.
- Click **Authorize Zscaler GitLab App **to re-establish the connection between GitLab and the ZPC Admin Portal, and enable IaC scanning of the GitLab repositories.
[See image.](#configpage)
A confirmation message appears indicating that the reauthorization is successful and you are redirected to the **Version Control & CI/CD Systems** page. The **Integration Status** is displayed as "Success" for that integration.
Use Case 2
For failed integrations, the **Integration Status** is displayed as *Failed* in the ZPC Admin Portal. In this case, if you offboard the tenant or unsubscribe from the IaC service entitlement, then the integration is deleted from ZPC but the webhooks are not deleted from the GitLab repository. You need to manually delete the webhooks.
If you don't delete the webhooks, then you might not be able to integrate the GitLab account whenever you subscribe for the IaC entitlement again.
[![Add a GitLab integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-gitlab.png)
]
[![Authorize Zscaler IaC Scan](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-authorisegitlab.png)
]
[![Click the tooltip to re-authorize the integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-gitlab-failedstatus.png)
]
[![Select GitLab ](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-select-gitlab.png)
]
[![View the scan summary and policy findings](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-gitlab-scanresult.png)
]
[![Select the GitLab repositories](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-gitlab-selectrepo.png)
]
[![Set up the advanced options](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-gitlab-advanced.png)
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
[![View the remediation procedure](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-gitlab/zpc-iac-gitlab-remediation.png)
]