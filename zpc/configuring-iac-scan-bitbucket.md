# Configuring IaC Scan for Bitbucket
Source: https://help.zscaler.com/zpc/configuring-iac-scan-bitbucket
PDF: https://help.zscaler.com/pdf/com/en/1450141.pdf

You can integrate Zscaler IaC Scan with Bitbucket to scan your IaC templates in Bitbucket repositories for both pull and push requests. IaC Scan continuously scans the templates for security misconfigurations against ZPC security controls and displays the failed checks.
You can perform an IaC scan on the entire repository of a branch or templates that were newly added to the branch. The scan results are displayed within Bitbucket, providing visibility into the IaC policy violations.
Configuring IaC Scan for Bitbucket
To configure the IaC Scan for Bitbucket:
- Go to **Administration** > **Version Control & CI/CD Systems**.
- On the **Version Control & CI/CD Systems** page, click **Add IaC Integration**.
[See image.](#add-bitbucket)
- Under **General Information**:
- For **IaC Scanner Type**, select **Code Repository**.
- For **Platform**, select **Bitbucket**.
[See image.](#select-bitbucketvcs)
- Click **Next**.
- Under **Configuration**, click **Authorize app from Bitbucket**.
- [Complete the authorization on Bitbucket.](#authorize-bitbucket)
- Click **Next**.
- Under **Choose Bitbucket Repositories**, select the checkbox for the repositories that must be enabled for scanning.
The date and time format is displayed as per the user's location.
[See image.](#chooserepos)
- Click **Next**.
- (Optional) Under **Advanced Settings**:
- **Scan on Push**: Click the toggle to scan the code for a push command. The IaC Scan app performs the scan in the background and triggers alert notifications for any policy violations and displays the alerts in the ZPC Admin Portal. To learn more, see [About Alerts](/zpc/about-alerts).
- **Include Paths**: Click the **Edit** icon to include the file path of the specific file or folder that must be scanned. For example, if you define an include path for a single file, then only that file is scanned and all other files and folders within the repository are ignored. [See image.](#filepaths)
- **Fail Check Criteria**: Fail check criteria is applicable to only pull requests based on policy severity. Select the security threshold (Critical, High, Medium, or Low) for the policy from the drop-down list.
You can apply a security threshold to each repository. For example, you can fail a pull request that introduces **Critical** or **High** issues from a repository that is used to deploy to a production environment. If the same pull request has a **Low** threshold and the code must be merged to a repository that is used to deploy in a development environment, then you can pass the request. However, the alert notification is generated in both scenarios.
[See image.](#bitbucket-advanced)
-
Click **Finish**.
Viewing IaC Scan Results
After you enable the selected repositories for scanning, the IaC Scan performs a scan every time you add or update a code and make a pull or push. The IaC Scan identifies security misconfigurations and displays policy violations and remediation steps within the code. You can fix the issues and then merge the code.
You can see the total policies along with passed and failed findings. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource. You can see the policy title and ID, severity, and resource details after the line of code that has issues.
You can also see the remediation steps for resolving the issue.
[See image.](#bit-remedy)
- []Sign in to your Bitbucket account.
- Install the Zscaler IaC Scan.
Only an administrator can install and authorize the IaC Scan. Zscaler recommends that you select **All repositories** so you can later onboard subsequent repositories directly from the ZPC Admin Portal.
- Click **Install & Authorize**.
After completing the installation, you are redirected back to the **Configuration** page in the ZPC Admin Portal.
[![Add a Bitbucket integration](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-addbitbucketintegration.png)
]
[![Select Bitbucket](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-selectbitbucket.png)
]
[![Select the repositories for scanning](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-choose-%20repositories.png)
]
[![Include file paths](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-bitbucket-includepath.png)
]
[![Configure the advanced options](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-bitbucket-advancedsettings.png)
]
[![View the remediation procedure](/downloads/zpc/iac-integrations/version-control-systems/configuring-iac-scan-bitbucket/zpc-bitbucket-remediation.png)
]