# Configuring the Defense Evasion Module
Source: https://help.zscaler.com/deception/configuring-defense-evasion-module
PDF: https://help.zscaler.com/pdf/com/en/1531302.pdf

The Defense Evasion module enables you to create fake security processes on endpoint machines to trap adversaries who attempt to stop security processes, such as antivirus, endpoint detection and response (EDR), data loss prevention (DLP), etc.
The Defense Evasion module is supported for Windows and macOS endpoints only.
To configure defense evasion for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy defense evasion detection on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window, click **Defense Evasion**.
-
Under the **Fake Security Processes **section:
- Select **Enabled** to deploy fake security processes on endpoints using the landmine policy.
- Enter the fake **Process Name**.
- Enter the fake **Process Path**.
[See image.](#zd-defense-evasion)
- Click **Save**.
The configured process can take more than two minutes to restart after it is stopped.
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-defense-evasion-module/deception-landmine-policy-edit-one.png)
[]![Configuring Defense Evasion in a landmine policy for Windows and macOS enpoints](/downloads/deception/deceive/landmine-decoys/policies/configuring-defense-evasion-module/zscaler-deception-defense-evasion-policy.png)