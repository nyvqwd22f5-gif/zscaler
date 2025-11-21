# Configuring IaC Scan for Visual Studio Code
Source: https://help.zscaler.com/zpc/configuring-iac-scan-visual-studio-code
PDF: https://help.zscaler.com/pdf/com/en/1392271.pdf

The Zscaler Infrastructure-as-Code (IaC) Scan extension for the Visual Studio Integrated Development Environment (VS IDE) enables you to scan the IaC Terraform, Kubernetes, Helm, and CloudFormation templates in VS Code and identify security misconfigurations. The Zscaler IaC Scan extension supports scanning individual IaC files and directories in the workspace. Scanning the IaC files in the build environment enables you to fix the configuration errors before committing the code for deployment, and make sure the code is secure and compliant with standard security policies. To install the Zscaler IaC Scan Extension, see the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Zscaler.zscaler-iac-scan).
Key Features
The Zscaler IaC Scan extension for VS has the following capabilities:
- Scans IaC Terraform, Helm, Kubernetes, Azure Resource Manager (ARM) and CloudFormation templates with built-in policies for Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP) resources.
- Supports creating exemptions for policies within a template.
- Highlights policy violations with severity for failed resources.
Configuring the Zscaler IaC Scan Extension for Visual Studio
To configure the Zscaler IaC Scan extension for VS:
- Go to **Administration **>** Workstations & IDEs**.
- Under **General Information**, click the **Visual Studio** icon.
[See image.](#selectide)
You are directed to the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Zscaler.zscaler-iac-scan) to install the IaC Scan extension.
- After successful installation of the IaC Scan extension, a Zscaler icon appears in the VS IDE’s left navigation menu. Click the Zscaler icon.
[See image.](#Zscaler_icon)
- Click **Sign In**.
[See image.](#signin_button)
- Access the Zscaler IaC Scan’s login command by pressing `CMD/CTRL+SHIFT+P` and search for "Zscaler IaC Scan: Login".
- Select the required region (EU, US, or Custom) where your tenant resides.
[See image.](#region)
- After selecting the region, you are redirected to the Zscaler login page within a browser. Log in using your ZPC admin credentials.
[See image.](#loginpage)
If your account is configured to use single sign-on (SSO), then you are redirected to your IdP's login page.
- After successful login, you are redirected back to the Visual Studio IDE where you must complete the login flow setup:
- In the dialog window that appears, click ** Open Visual Studio Code**.
[See image.](#open_vscode)
- In the dialog window that appears, click **Open**.
[See image.](#vscode_extn)
- The logged in user's email address appears at the bottom of the window after the extension opens the URI.
[See image.](#email_statusbar)
Using the Zscaler IaC Scan Commands
The Zscaler IaC Scan extension provides a set of commands. Press `CTRL+SHIFT+P` on Windows, or `CMD+SHIFT+P` on macOS, then enter `Zscaler IaC Scan` to search for and use the commands.
![Use the required Zscaler IaC commands](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-vs-signin.png)
- **Scan File: **Scans the currently opened file in the VS IDE editor. Scan File is also triggered automatically when you save the file.
- **Scan Workspace: **Scans all IaC files in the current Visual Studio workspace.
- **Open Settings: **Opens the Settings page.
- **Clear Scan Results: **Clears all problems and warnings generated for the IaC resources.
- **Install/Update: **Installs or updates the Zscaler IaC binary, which is used by the extension to run the IaC scans.
- **Sign Out: **Log out from VS Code. When you log out, another browser opens and displays the logout message. [See image. ](#vs-logout)
Viewing Policy Violations
After running the scan on the IaC templates, policy violations are displayed on the **Problems** tab of the VS IDE window.
![View the policy violations](/downloads/zpc/iac-integrations/iac-scanning/configuring-iac-scan-visual-studio/zpc-view-policyviolations.png)
Viewing Remediation Steps
After an IaC template is scanned, you can view the policy violations and remediation steps for these violations within the VS IDE window. You can follow the remediation guidelines and resolve the misconfiguration.
To view the remediation:
- You can do either of the following steps:
- Click anywhere within the code to view the pop-up menu, then Select **View Remediation** for the specific policy violation.
[See image.](#remedy-code)
- Click within the **Problems** tab to view the pop-up menu, then select **View Remediation **for the specific policy violation.
[See image.](#remedy-menu)
The remediation steps are displayed on another tab within the IDE.
[See image.](#remedy-steps)
Skipping Policies
You can use the IaC extension to automatically add rules to skip the required policies:
- Hover over the violating resource and select **Quick Fix**...
[See image.](#quickfix)
- Add a skip comment for the specific policy ID.
[![Add skip rule by selecting Quick Fix option](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-vsc-fix-problem.png?1647953036)
]
[![View the Zscaler icon in VS Code](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-vsc-zicon.png)
]
[![View the sign-in button in VS Code](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-vsc-signin.png?1647948936)
]
[![Select the region where your tenant resides](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-region-vscode.png)
]
[![Log in to the ZPC Admin Portal](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-login-screen.png)
]
[![Message prompting to open VS Code](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-open-vscode.png)
]
[![Allow the extension to open the URI](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-open-vscode-extn.png?1647950955)
]
[![Login email displayed in the status bar of VS Code](/downloads/zwp/administration/integrations/iac-integrations/configuring-iac-scan-visual-studio-code/zwp-iac-vsc-email.png)
]
[![Select View Remediation for the specific policy violation](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-vscode-remed-problemtab.png)
]
[![View the remediation steps to resolve the policy violation](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-vscode-remediationsteps.png)
]
[![View the remediation steps menu within the code](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-vscode-remed-code.png)
]
[![View the logout message](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-visual-studio/zpc-vscode-logout.png)
]
[![Click the Visual Studio icon](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-scan-jetbrains-ides/zpc-ides.png)
]