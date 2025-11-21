# About IaC Integrations
Source: https://help.zscaler.com/zpc/about-iac-integrations
PDF: https://help.zscaler.com/pdf/com/en/1392376.pdf

Zscaler Posture Control (ZPC) offers the Zscaler Infrastructure-as-Code (IaC) Scan security feature that enables you to apply security controls on your IaC infrastructure before deployment. The IaC Scan tool scans the IaC templates for misconfigurations and known vulnerabilities that are a potential risk for attacks. The IaC Scan tool leverages more than 100 security policies to check for configuration errors in your code, such as missing database encryption, publicly exposed services, etc., so you can remediate these errors and ensure your code is secure and compliant with the security policies. To know more, see [About Security Policies](/zpc/about-security-policies).
The IaC Scan can be easily integrated with various code repositories, continuous integration (CI) and continuous deployment/delivery (CD) tools, and integrated development environments (IDEs). The IaC Scan is also available as a command line interface tool.
Software entitlements are products that you are allowed to use. You can subscribe for the Zscaler IaC Scan service. If the software entitlement expires or if you've removed or downgraded the subscription (e.g., reverted from ZPC-Advanced to ZPC-Essential version), then you cannot perform the IaC scan.
The key features and benefits of the IaC Scan include:
- Seamless Integration: Easily configure the IaC Scan from the Zscaler Posture Control (ZPC) Admin Portal.
- Automated Scan: Automatically scan the code after each pull or merge request within code repositories and CI/CD tools.
- Onboarding Repositories: Select the required repositories that must be enabled for scanning.
- Detect Policy Violations: Scan the code against standard IaC security policies and identify misconfigurations.
- Real-Time Visibility: View the scan results and details of the policy violations within the code.
- Security Compliance: Ensure the code is compliant with security policies.
Supported Platforms and Templates
The Zscaler IaC Scan provides support for various version control systems and CI/CD platforms, IaC templates, and CLI.
- [Supported Platforms](#platforms)
- [Supported IaC Templates](#templates)
[]About the Version Control & CI/CD Systems Page
On the Version Control & CI/CD Systems page (Administration > Version Control & CI/CD Systems), you can:
- Add IaC Integrations for version control systems and CI/CD Pipelines.
- View the list of integrations for **Version Control Systems** and **CI/CD Pipelines**. For each integration, you can see the following details:
- **Integration Name**: The name of the integration. Click to view the repository details.
- **Integration Type**: The type of integration.
- **Selected Repository Count**: The number of repositories in the account or organization.
- **Integration Status**: The status (Success or Pending) of the integration.
- **Created By**: The email address of the user who added the integration.
Some integration details vary depending on the version control system or the CI/CD system.
- View the repository details.
- **Repository Name**: The name of the repository.
- **Status**: The status (Private of Public) of the repository.
- **Default Branch**: The branch of the repository.
- **Scan on Push**: Whether scan on push option is enabled or not (On of Off).
- **Fail Check Criteria**: Whether the criteria is applied to all the repositories.
- **Actions**: Delete the repository.
[See image.](#repo-details)
- [Edit the integration](/zpc/editing-or-deleting-iac-integration).
- [Delete an integration](/zpc/editing-or-deleting-iac-integration).
- Search for specific details in the searchable columns. [See image.](#search)
![View the IaC integrations](/downloads/zpc/version-control-cicd-systems/about-iac-integrations/zpc-iac-page.jpg)
[]The Zscaler IaC Scan can be integrated with the following platforms:
- **Version Control Systems**
- [GitHub](/zpc/configuring-iac-scan-github)
- [GitLab](/zpc/configuring-iac-scan-gitlab)
- [Azure Repos](/zpc/configuring-iac-scan-microsoft-azure-repos)
- [Bitbucket](/zpc/configuring-iac-scan-bitbucket)
- **CI/CD Tools**
- [GitHub Actions](/zpc/configuring-iac-scan-github-actions)
- [Jenkins](/zpc/configuring-iac-scan-jenkins)
- [TeamCity or CircleCI](/zpc/configuring-iac-scan-other-cicd-tools)
- [Azure Pipelines](/zpc/configuring-iac-scan-microsoft-azure-pipeline)
- [Terraform Cloud](/zpc/configuring-iac-scan-terraform-cloud)
- **Workstation & IDEs**
- [Visual Studio](/zpc/configuring-iac-scan-visual-studio)
- [Windows, macOS, and Linux](/zpc/configuring-iac-cli-scanner)
- [JetBrains IDEs](/zpc/configuring-iac-scan-jetbrains-ides)
[]The Zscaler IaC Scan can be used to scan the following IaC templates:
- AWS Cloud Formation (JSON, YAML)
- Azure Resource Manager (ARM)
ZPC provides support for linked templates. If an ARM template is linked to a remote template, then ZPC downloads the remote template, performs the scan on the remote template and also reports violations that are detected in the linked templates. To know more about linked and nested templates, see the [Microsoft Azure Documentation](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/linked-templates?tabs=azure-powershell).
- Helm
- Kubernetes
- Terraform
- Terraform Plan: All CI/CD Pipelines. However, Terraform Plan is supported in Pipeline mode for Jenkins.
To learn more about the functions that are supported for each template type, see [Supported IaC Templates and Functions](/zpc/supported-iac-templates-and-functions).
[![View the repository details](/downloads/zpc/version-control-cicd-systems/about-iac-integrations/zpc-iac-repodetails.jpg)
]
[![Search for the required data](/downloads/zpc/version-control-cicd-systems/about-iac-integrations/zpc-searchablecolumns.jpg?1675852117)
]