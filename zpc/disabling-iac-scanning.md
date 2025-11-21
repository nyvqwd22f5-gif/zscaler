# Disabling IaC Scanning
Source: https://help.zscaler.com/zpc/disabling-iac-scanning
PDF: https://help.zscaler.com/pdf/com/en/1403386.pdf

You can disable the IaC scanning for selected repositories within GitHub, GitLab, or Azure Repos.
ZPC disables the IaC scanning and removes the selected repository from the IaC integration.
To disable the IaC scanning:
- In the ZPC Admin Portal, go to **Administration **> **Version Control & CI/CD Systems**.
The **IaC Integrations** page appears.
- Under **Version Control Systems**, click the **GitHub**, **GitLab**, or **Azure Repos** tab.
- Click the **View** icon for the account that you wish to edit.
[See image.](#view)
The list of repositories in this account is displayed. By default, the scanning is enabled for all repositories.
- Click the toggle under the **Scanning** column to disable the scanning.
[See image.](#toggle)
- A confirmation message appears. Click **Disable** to proceed.
[See image.](#confirm)
Any scanning that is currently in progress is completed, then the IaC scanning is disabled for the repository.
[![Click the View icon to see the IaC integration details and disable scanning](/downloads/zpc/iac-integrations/disabling-iac-scanning/zpc-iacview-icon.png)
]
[![Disable IaC scanning](/downloads/zpc/administration/iac-integrations/disabling-iac-scanning/zpc-iac-disable-toggle1.png)
]
[![Disable the IaC scanning for the selected repository](/downloads/zpc/iac-integrations/disabling-iac-scanning/zpc-disable-scan-msg.png)
]