# Downloading and Running a Remediation Script
Source: https://help.zscaler.com/itdr/downloading-and-running-remediation-script
PDF: https://help.zscaler.com/pdf/com/en/1531631.pdf

You can download a remediation script and run it on PowerShell to remediate vulnerability issues in an Active Directory (AD) domain.
To download and run a remediation script:
- Go to **ITDR** > **Dashboard **> **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
The scan result for the AD domain appears.
- Click an issue in detailed findings and recommendations, affected user or computer, severity chart, or risk analysis chart to view the additional issue details.
-
On the issue details page, under **Remediation Script**, click **Download Remediation Script**.
[See image.](#deception-remediation-script-itdr-download)
The script is downloaded to your local system.
- Copy the remediation script to the primary domain controller.
- Open PowerShell on the primary domain controller with administrative privileges.
- Go to the path where the remediation script is saved.
-
Run the following command to import the script:
`import-module .\<Remediation script>`
-
Run the following command to start remediation:
`Invoke-Remediation`
-
Enter `Y`.
[See image.](#deception-remediation-script-commands)
The remediation is completed.
[See image.](#deception-remediation-script-completed)
[]![Download remediation script](/downloads/deception/identity/downloading-and-running-remediation-script/zscaler-deception-issue-download-remediation-script.png)
[]![Commands to run the remediation script](/downloads/deception/identity/downloading-and-running-remediation-script/zscaler-deception-run-issue-remediation-script-commands.png?1673423757)
[]![Remediation completed](/downloads/deception/identity/downloading-and-running-remediation-script/zscaler-deception-remediation-completed.png)