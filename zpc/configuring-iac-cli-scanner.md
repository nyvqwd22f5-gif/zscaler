# Configuring the IaC CLI Scanner
Source: https://help.zscaler.com/zpc/configuring-iac-cli-scanner
PDF: https://help.zscaler.com/pdf/com/en/1392441.pdf

This article provides step-by-step instructions for configuring the Zscaler IaC CLI Scanner on Windows, macOS, and Linux platforms.
The IaC CLI Scanner enables you to scan the IaC templates in your local file system. You can download the latest version of the IaC CLI Scanner binary for the required operating system, and integrate it with the pre-commit hook to automatically scan your IaC files before every commit.
Prerequisites
Ensure you use the [supported operating systems](/zpc/supported-os-versions-iac-scanning) only, otherwise the IaC integration fails.
Configuring the IaC CLI Scanner
To configure the IaC CLI Scanner:
- Go to **Administration **>** Workstations & IDEs**.
- Under **General Information**, select any of the following platforms:
- Windows
- macOS
- Linux
- [Visual Studio](/zpc/configuring-iac-scan-visual-studio)
- [JetBrains](/zpc/configuring-iac-scan-jetbrains-ides)
[See image.](#selectides)
- Under **Configuration**:
- **Select version to download**: Select the IaC CLI Scanner version that you want to download from the drop-down menu.
- **Installation instructions**: Follow the instructions to download and install the binary file on:
- [Windows](#windows)
- [macOS and Linux](#macinstalloptions)
- Click **Next**.
- [Configure the pre-commit hook file](#configure-precommit). To learn more, refer to the [ZPC GitHub repository](https://github.com/ZscalerCWP/iac-pre-commit-hooks).
- Click **Finish.**
Using the IaC CLI Scanner
You can perform an IaC scan from the command-line interface to check for any security misconfigurations in the IaC templates that are stored in your local file system.
To run the IaC CLI Scanner from the command-line interface:
- Open the command prompt window.
- Run the following command to log in to your Zscaler account.
zscanner login
- Enter the region (EU, US, or Custom) where you want to access the ZPC Admin Portal.
- Press `Enter` to open the ZPC login page in your browser.
[See image.](#clilogin)
If your account is configured to use single sign-on (SSO), then you are redirected to the IdP login page.
- Enter the LoginID and password, then click **Sign In**.
You are now logged in and redirected back to the CLI.
- Run any of the following commands depending on your requirements:
- Scan a specific folder:
zscanner scan -d /<folder name>/<folder path>
Before performing the scan, you must check out the repository or directory from the specific branch.
- Scan a single file:
zscanner scan -f file <filename>
- Record any issues and logs into a file:
zscanner scan -f <filename> --log-level debug --log-file test.log
- Scan the IaC template files present in your repository:
zscanner scan --iac-type <template type>
List of Commands
You can use the following commands:
- `login`: Log in to the Zscaler account. If your account is configured to use single sign-on (SSO), then you need to log in to your IdP portal.
- `logout`: Log out of the Zscaler account. When you log out, a new browser opens and displays the logout message. [See image.](#cli-logout)
- `scan`: Detect compliance and security violations in the IaC templates.
- `update`: Update the IaC CLI Scanner to the latest version.
- `version`: Check the IaC CLI Scanner version that is currently used.
- `cleanup`: Clean up all temporary files (from old installations).
- `completion`: Generate the auto-completion script for the specified shell.
- `help`: Learn more about any command.
- `info`: Display the login information.
- `policy list`: Display the list of policies used by the IaC CLI Scanner.
- `config list`: Display the configuration details used by the IaC CLI Scanner.
Updating the IaC CLI Scanner
You can update the IaC CLI Scanner to the latest version.
Whenever a new version of the IaC CLI Scanner is available, the following message is displayed within the CLI: "An updated version <`number`> (Current Version: <`number`>) of the IaC CLI Scanner is available. Please run the `zscanner update` command to update the CLI Scanner."
Viewing the Remediation Steps
After an IaC template is scanned, you can view the scan summary, policy violations along with the severity level, and remediation steps for these violations within the CLI. You can follow the remediation guidelines and resolve the misconfiguration.
[See image.](#remediation)
If you don't want to see the remediation steps, then run the following command:
zscanner scan -d . --show-remediation=false
- []Click the link to download the `iac-scanner-cli.xxx.tar.gz` binary package.
[See image.](#cli-windows)
- Extract the `.tar.gz` file to a folder.
- Copy the `zscanner.exe` file and paste it into a folder that is listed in the `PATH` environment variable, or add the folder path where `zscanner.exe` resides to the `PATH` environment variable.
[See image.](#pathenv)
- [][Install with sudo permissions](#with-sudo)
- [Install without sudo permissions](#without-sudo)
- []Click the link to download the IaC CLI Scanner.
[See image.](#install-mac)
- Open the Terminal and enter the following command to extract the `.tar` file:
- For ARM:
$ tar -xf iac-scanner-cli_2.0.1_darwin_arm64.tar.gz zscanner && rm iac-scanner-cli_2.0.1_darwin_arm64.tar.gz
- For x86:
$ tar -xf iac-scanner-cli_2.0.1_darwin_x86_64.tar.gz zscanner && rm iac-scanner-cli_2.0.1_darwin_x86_64.tar.gz
- Run the following command to install the IaC CLI Scanner:
$ install zscanner /usr/local/bin && rm zscanner
In case you're not able to install the IaC CLI Scanner on any macOS, complete the following steps:
- On your Mac computer, go to **System Preferences** > **Security & Privacy**.
- Under **Allow apps downloaded from**, select **app store and identified developers**, so you have the permissions to install and run the IaC CLI Scanner.
- Click **Allow**.
[See image.](#permissions)
- Run the following command to check and confirm if you can initialize the IaC CLI Scanner:
$ zscanner
- []Click the link to download the `iac-scanner-cli.xxx.tar.gz` binary package.
- Extract the `.tar.gz` file to a folder.
- Copy the extracted binary to a different location.
$ cp <source_path> <destination_path>
-
Set up the `ZSCANNER_HOME` to point to the `destination_path` where the binary is copied and add the same path to the `PATH `variable within the Profile (`.bash_profile`, `.zshrc`, or `.zshenv`).
$ export ZSCANNER_HOME=<destination_path>
$ export PATH=$PATH:$ZSCANNER_HOME
$ source ~/.<profile_file_name>
- []Open the command prompt and run the following command to install the pre-commit hook framework.
pip install pre-commit
-
Add the `.pre-commit-config.yaml `file to the IaC repository that must be scanned.
- Copy the following code provided in the ZPC Admin Portal and add it to this `.yaml` file:
repos:
- repo: https://github.com/ZscalerCWP/iac-pre-commit-hooks
rev: v0.0.1
hooks:
- id: zscaler-iac-scanner
- Run the following command at the command prompt to install the configured pre-commit hook in the IaC repository.
pre-commit install
After installation, the pre-commit hook automatically scans the IaC files on every git commit and displays the results within the code.
- Run the following command to initialize the pre-commit hook to scan all the IaC files.
pre-commit run `--all-files`
[![Install the IaC CLI scanner on Windows](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-windows.png)
]
[![Install the IaC CLI scanner on Mac OS](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-scanner.png)
]
[![Set permissions on the mac machine](/downloads/zpc/administration/integrations/iac-integrations/configuring-iac-cli-scanner/zpc-iac-cli-mac-permissions.png)
]
[![Log in to ZPC](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-login.png)
]
[![View the remediation steps in the CLI](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-remediation.png)
]
[![Paste the file in a folder in the PATH environment variable](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-pastefile.png)
]
[![View the logout message](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-cli-logout.png)
]
[![Select the required platform](/downloads/zpc/version-control-and-cicd-systems/workstations-ides/configuring-iac-cli-scanner/zpc-ides.png)
]