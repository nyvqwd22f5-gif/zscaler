# Configuring IaC Scan for GitHub
Source: https://help.zscaler.com/zpc/configuring-iac-scan-github
PDF: https://help.zscaler.com/pdf/com/en/1391376.pdf

This article provides step-by-step instructions for integrating the Zscaler IaC Scan app with GitHub.
The Zscaler IaC Scan app scans and identifies security misconfigurations in the IaC Terraform, Kubernetes, Helm, ARM, and CloudFormation templates in the GitHub repositories. Whenever you add or update the code and make a pull request or use the push command to commit the code, the IaC Scan app automatically scans the IaC templates, identifies policy violations, and displays the scan results within the code. The scan allows you to detect and fix configuration errors before code deployment and ensure the code is secure and compliant with security policies. To learn more, see [About Security Policies](/zpc/about-security-policies).
Prerequisites
The organization administrators must install and authorize the Zscaler IaC Scan app to access the IaC source code repositories on GitHub. After completing the authorization, any user with the required permissions can enable the specific repositories for scanning in the Zscaler Posture Control (ZPC) Admin Portal.
Configuring the Zscaler IaC Scan App for GitHub
To configure the Zscaler IaC Scan app for GitHub:
- Go to **Administration **> **Version Control & CI/CD Systems**.
- On the **IaC Integrations** page, click **Add IaC Integration**.
[See image.](#add-github)
- Under **General Information:**
- For **IaC Scanner Type**, select **Code Repository**.
- For **Platform**, select **GitHub**.
[See image.](#select-github)
- Click **Install GitHub App**. You are directed to the GitHub portal.
- [Complete the installation and authorization on GitHub.](#github-authorize)
- Under **Choose GitHub Repositories**, select the checkbox for the repositories that must be enabled for scanning.
The date and time format is displayed as per the user's location.
[See image.](#github-repos)
- Click **Next**.
- (Optional) Under **Advanced Settings**:
- **Scan on Push**: Click the toggle to scan the IaC files in the default (main/master) branch. Alerts that are triggered for any policy violations are displayed in the ZPC Admin Portal. To learn more, see [About Alerts](/zpc/about-alerts).
- **Include Paths**: Click the **Edit** icon to include the file path of specific files or folders that must be scanned. For example, if you define an include path for a single file, then only that file is scanned and all other files and folders within the repository are ignored. You can also use regular expressions (regex) to search for and include multiple files or folders that must be scanned:
- [See regex patterns with examples](#regex-pattern)
[See image.](#filepaths)
- **Fail Check Criteria**: Fail check criteria is applicable to only pull requests based on policy severity. Select the security threshold (Critical, High, Medium, or Low) for the policy from the drop-down list. Scan results are posted on GitHub for all the selected options.
You can apply a security threshold to each repository. For example, you can fail a pull request that introduces **Critical** or **High** issues from a repository that is used to deploy to a production environment. If the same pull request has a **Low** threshold and the code must be merged to a repository that is used to deploy in a development environment, then you can pass the request. However, the alert notification is generated in both scenarios.
[See image.](#github-advanced)
- Click **Finish**.
- On GitHub, go to **Settings > GitHub apps** and verify that the Zscaler IaC Scan app is installed.
Enabling Branch Protection
You can add a branch protection rule on GitHub to enforce a workflow, such as review and approval before code commit, etc. To learn more, see the [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule).
To create a branch protection rule:
- On the GitHub portal, navigate to the main page of the repository.
- Click the **Settings** tab.
- Under **Code and automation**, click **Branches**, then **Add branch protection rule**.
[See image.](#add-rule)
- For **Branch name pattern**, enter the branch name or pattern you want to protect.
- Under **Protect matching branches**, select the required option.
- Click **Create**.
[See image.](#ruleoptions)
- []Sign in to your GitHub account.
- On the **Install & Authorize Zscaler IaC Scan** page, select the account where you want to install the IaC Scan app.
Only an organization administrator can install and authorize the IaC Scan app to scan all the repositories or specific repositories. Zscaler recommends that you select **All repositories** so subsequent repositories are automatically added to the list of repositories displayed in the ZPC Admin Portal. However, you still need to choose specific repositories that must be included for scanning.
- Click **Install & Authorize**.
[See image.](#install-github)
After completing the installation, you are redirected back to the **Configuration** page in the ZPC Admin Portal.
Viewing the IaC Scan Results
The IaC scan results are displayed within the code, so you can easily evaluate and resolve the issues.
- On the GitHub portal, navigate to the repository, then select **Pull requests**.
- Click **Details**.
[See image.](#detailsbutton)
You can view the following:
- The line of code that has violations along with the policy title and ID, severity, and resource details.
[See image.](#policydetails)
- The total policies evaluated along with passed and failed findings are displayed. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource.
[See image.](#nofindings)
- Remediation steps for resolving the issue.
[See image.](#remediationsteps)
The ZPC service generates alerts for IaC policy violations. You can view these alerts in the ZPC Admin Portal. You can also configure alert notifications for ZPC to send email notifications to recipients or send the alert data to third-party tools. To learn more, see [About Alerts](/zpc/about-alerts).
[![Add a GitHub integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github.png)
]
[![Select GitHub under general information](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-github/zwp-add-iac-integ-generalinfo.png)
]
[![View the policy details](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-viewpolicydetails.png)
]
[![View the policy violations](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-policydetails.png)
]
[![Select the GitHub repositories for scanning](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-repos.png)
]
[![Set up the advanced options](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-advanced.png)
]
[![Zero policy findings](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-nofindings.png)
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
[![View the remediation procedure](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-iac-github-remediation.png)
]
[![Install and authorize GitHub for IaC scanning](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-installiacscan-github.png)
]
[![Include file paths of repositories](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-filepaths.png)
]
[![Add a branch protection rule](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-addbranchprotection.png)
]
[![Select the rule options](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-github/zpc-github-protectionrule.png)
]