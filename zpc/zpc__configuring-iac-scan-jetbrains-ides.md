# Configuring IaC Scan for JetBrains IDEs
Source: https://help.zscaler.com/zpc/configuring-iac-scan-jetbrains-ides
PDF: https://help.zscaler.com/pdf/com/en/1447561.pdf

The Zscaler Infrastructure-as-Code (IaC) Scan plugin for the JetBrains Integrated Development Environments (IDEs) enables you to scan the IaC Terraform, Kubernetes, Helm, ARM, and CloudFormation templates in the JetBrains IDE platforms and identify security misconfigurations categorized by severity. Scanning the IaC files in the build environment enables you to fix the configuration errors before deploying the code, and ensure that the code is secure and compliant with standard security policies. To install the Zscaler IaC Scan plugin, see the [JetBrains Marketplace](https://plugins.jetbrains.com/plugin/21168-zscaler-iac-scan).
Zscaler IaC Scan plugin can be integrated with the following IDEs:
- [List of IDEs](#ides)
Prerequisites
Make sure you've already installed the required JetBrains IDE on which you want to install and run the Zscaler IaC Scan plugin.
Configuring the IaC Scan Plugin for JetBrains IDEs
To configure the Zscaler IaC Scan plugin for JetBrains IDEs:
- Go to **Administration **>** Workstations & IDEs**.
- Under **General Information**, click the **JetBrains** icon.
[See image.](#ide-platform)
You are directed to the [JetBrains Marketplace](https://plugins.jetbrains.com/plugin/21168-zscaler-iac-scan) to install the Zscaler IaC Scan plugin. You can also install the IaC Scan plugin from within the IDE:
- Log in to the IDE.
- In the left-side navigation, select **Preferences** > **Plugin**.
- Search for Zscaler IaC Scan plugin, then click **Install**.
[See image.](#install)
- When the installation is complete, click the **ZPC** icon on the bottom panel of the IDE, then click the **Tool** icon to authenticate the IaC Scan plugin with the IDE.
[See image.](#zpcicon)
- Select the region (EU or US) where your tenant is onboarded, then click **Login**.
[See image.](#region)
- After selecting the region, you are redirected to the ZPC login page within a browser. Log in using your ZPC admin credentials.
If your account is configured for single sign-on (SSO), then you are redirected to your IdP's login page.
- Return to the JetBrains IDE.
- Click **Project**, then navigate to the required IaC directory or individual file.
- To scan a directory, select the directory, then click the **Scan Directory** icon (![Click the icon to scan a directory](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-scandirectoryicon.png)
).
- To scan an individual file, open the file, then click the **Scan File** icon (![Click the icon to scan a file](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-scanfileicon.png)
).
[See image.](#project)
The policy violations are displayed for files that contain misconfigurations. Click the required policy to view the details such as policy description and ID, resource name and type, template type, file path, and the severity (Critical, High, Medium, Low) of the policy. You can investigate and resolve the issues.
Viewing the Remediation Steps
You can view the policy violations and remediation steps for these violations within the JetBrains IDE window. You can follow the remediation guidelines and resolve the misconfiguration.
[See image.](#remediation)
Logging Out from the Zscaler IaC Scan Plugin
To log out from the IaC Scan plugin click the **Logout** icon (![Sign-out icon](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-signinicon.png)
) in the left-side navigation. A new browser opens and displays the logout message.
[See image.](#logoutmessage)
- []Aqua
- CLion
- DataGrip
- DataSpell
- GoLand
- IntelliJ
- MPS
- PhpStorm
- PyCharm
- Rider
- RubyMine
- WebStorm
[![Select JetBrains](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-jetbrains-ides/zpc-ides.png)
]
[![Select the region](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-jetbrains-selectregion.png)
]
[![Select the project](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-scanprojects.png)
]
[![The ZPC and tool icons](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-zpc-icon.png?1678360173)
]
[![Install the plugin](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-jetbrains-install.png)
]
[![Logout message](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-intellij-platform/zpc-inellij-logout.png)
]
[![View the remediation steps](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-jetbrains-ides/zpc-jetbrains-remediation.png)
]