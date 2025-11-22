# Configuring IaC Scan for Other CI/CD Tools
Source: https://help.zscaler.com/zpc/configuring-iac-scan-other-cicd-tools
PDF: https://help.zscaler.com/pdf/com/en/1402611.pdf

This article provides step-by-step instructions for configuring the Zscaler IaC Scan with other continuous integration and continuous delivery (CI/CD) tools such as TeamCity and Circle CI.
The Zscaler IaC Scan scans and identifies security misconfigurations in the IaC Terraform, Helm, Kubernetes, and CloudFormation templates. You can download and configure a binary script (`zscaler-iac-scan.sh`) on the CI/CD tools. The binary script executes every time you run a build and displays the misconfigurations within the code.
Prerequisites
The administrator must configure the Zscaler IaC Scan binary script for the CI/CD tools.
Ensure you use the [supported operating systems](/zpc/supported-os-versions-iac-scanning) only, otherwise the IaC integration fails.
Configuring the Zscaler IaC Scan for other CI/CD Tools
To configure the Zscaler IaC Scan:
- In the ZPC Admin Portal, go to **Administration**** **> **Version Control & CI/CD Systems**.
- On the **IaC Integrations **page, click **Add IaC Integration**.
[See image.](#add-others)
- Under **General Information**:
- For **Choose** **IaC Scanner Type**, select **CI/CD**.
- For **Choose Platform**, select **Other CI/CD Integrations**.
[See image.](#select-others)
- Click **Next**.
- Under **Configuration**:
- Select the **CI/CD Integration** (TeamCity or Circle CI) from the drop-down menu.
- Enter the local identifier for your CI/CD integration, then click **Confirm**. Enter a unique name. For example, you can provide the name of your organization, IaC repository, etc.
[See image.](#config)
A Client ID and Client Secret Key are generated after confirmation. These values are required to establish a connection between the CI/CD tool and the ZPC Admin Portal.
- Copy the **Client ID** and **Client Secret Key**.
[See image.](#keys)
- Download the binary script (`zscaler-iac-scan.sh`) to your local folder: [Download](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-other-cicd-tools/zscaler-iac-scan.zip) The downloaded file is in ZIP format, so you need to decompress the file and then use the `.sh` script.
- Click **Finish**.
The CI/CD integration is displayed on the **Version Control & CI/CD Systems** page.
Configuring the Binary Script
After completing the IaC integration, configure the binary script on:
- [TeamCity](#teamcity)
- [Circle CI](#circleci)
The binary script executes whenever you make a code commit to the build and displays the scan results in the required format. You can also see the details of the policy violations on the IaC dashboard. To learn more, see [About the IaC Dashboard](/zpc/about-iac-dashboard).
Viewing the IaC Scan Results
When you add or update the code and make a merge request, the IaC Scan action automatically triggers a scan, identifies security misconfigurations, and displays the policy violations within the code. This allows you to fix the configuration errors before deployment, and ensure the code is compliant. To know more, see [About Security Policies](/zpc/about-security-policies).
You can see the total policies along with passed and failed findings. This information indicates if the code is violation-free for the policies evaluated or if none of the policies were evaluated for this resource.
The ZPC service generates alerts for IaC policy violations detected during the scan. You can view the list of alerts and policy violations in the ZPC Admin Portal. To learn more, see [About Alerts](/zpc/about-alerts).
[![Select other CICD platforms](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-other-cicd-tools/zpc-selectothers.png)
]
[![Enter the configuration details](/downloads/zpc/administration/iac-integrations/configuring-iac-scan-other-cicd-tools/zpc-othercicd-config.png)
]
[![Copy the Client ID and Client Secret Key](/downloads/zpc/administration/iac-integrations/configuring-iac-scan-other-cicd-tools/zpc-othercicid-keys.png)
]
[]
- Log in to TeamCity.
- Access your build project where you want to perform the IaC scan.
- Go to **Administration** > **Add Build Step**.
- Paste the script in the **Custom script **field.
- Click **Parameters**.
- Add the following parameters in the same order.
Make sure to specify the parameters in the same sequence that is provided below. If you change the sequence of the parameters, then the script does not execute and shows an error.
- **Client ID**: Enter the Client ID you copied in step 5c above.
- **Client Secret Key**: Enter the Client Secret Key you copied in step 5c above.
- **Operating System**: Enter the operating system (e.g., Windows, macOS, or Linux) where you want to execute the script.
- **Platform Architecture**: Enter the operating system architecture (e.g., x86_64).
- **Region**: Enter the region (e.g., US) where the IaC repository exists.
- **File Path**: Enter the path for the file or directory where the IaC files are saved.
- **Fail Build**: Enter `true` or `false`. If you enter `true`, then you cannot commit the code changes to the build until you fix the errors in the code. If you enter `false`, then you can commit the code changes although the code has errors.
- **Output Format**: The scan results can be displayed in `human (default)`,` JSON`, `YAML`, or `GitHub-Sarif `format. Enter one of these values as required. If you do not choose any format, then the scan results are displayed in the default output format.
You can also execute the binary script at the command prompt.
- Click **Build Step: Command Line**.
- Enter the absolute path of the binary script.
- Enter the parameters mentioned above in the same sequence.
- Click **Save**.
[]
- Log in to Circle CI.
- Access the build project where you want to perform the IaC scan.
- Create a `config.yaml` file, include the binary script and the following 8 parameters in the file:
- **Client ID**: Enter the Client ID you copied in step 5c above.
- **Client Secret Key**: Enter the Client Secret Key you copied in step 5c above.
- **Operating System**: Enter the operating system (e.g., Windows, macOS, or Linux) where you want to execute the script.
- **Platform Architecture**: Enter the operating system architecture (e.g., x86_64).
- **Region**: Enter the region (e.g., US) where the repository exists.
- **File Path**: Enter the path for the file or directory where the IaC files are saved.
- **Fail Build**: Enter `true` or `false`.
- **Output Format**: The report is available in `human (default)`,` JSON`, `YAML`, or `GitHub-Sarif `format. Enter one of these values as required. If you do not choose any output format, then the scan results are displayed in the default output format.
A sample `config.yaml` file is provided below:
version: 2.1
jobs:
scan_check:
docker:
- image: circleci/node:lts
steps:
- checkout
- run:
command: chmod +x ./zscanner.sh
- run:
name: zscanner check
command: ./zscaler-iac-scan.sh  vdyUs63ZfRtjt0ns9fyYFoK0OL0m6Tu3 yAAjOfS_DKqEhFgOZ_Ma1Y09rkDThMgfO9Tfz-GtI5vXf--n9jT0kSQlcpMdQh0s Linux x86_64 US /Users/mbojja/Documents/testing/workspace_scan/network/main.tf true json
workflows:
build_and_test:
jobs:
- scan_check
[![Configure other CICD integrations](/downloads/zpc/iac-integrations/cicd-tools/configuring-iac-scan-terraform-cloud/zpc-others.png)
]