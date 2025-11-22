# Viewing Entra ID Change Detection Issue and Remediation Details
Source: https://help.zscaler.com/itdr/viewing-entra-id-change-detection-issue-and-remediation-details
PDF: https://help.zscaler.com/pdf/com/en/1531760.pdf

[Watch a video on Entra ID Change Detection.](https://fast.wistia.net/embed/iframe/y1qs9e29jz)
When active changes in an Entra ID tenant are detected and listed as a good, bad, or info impact, you can review the impact, view the issue details, and remediate issues.
To view issue and remediation details:
- Go to** ITDR** > **Dashboard** > **Entra ID Change Detection > Default**.
-
Select an Entra ID tenant from the **Result for** drop-down menu.
[See image.](#itdr-entra-id-cd-select-tenant-image)
The changes detected in the Entra ID tenant are listed.
-
Double-click a change, or click the **View** icon under **Actions** to view the details.
[See image.](#itdr-entra-cd-view-icon)
The** Issue Details** window appears with the following details:
- **Change Date**: The date and time when a change is detected in the identity.
- **Issue Name**: The issue name.
- **Change**: The description of the change.
- **Type of Risk**: The type of risk (e.g., **Excessive Privileges**, **Delegation Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **What is the issue?**: The description of the issue.
- **What is the impact?**: The impact status (**Good**, **Bad**, or **Info**).
- **Change Data**: The details of the change that was detected in the identity, such as the operation name, the caller IP address, data source information, and role details.
- **Remediation**: The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**). For every remediation step, you can view:
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: Links to the Microsoft documentation or any other reference documentation. You can click a link to view guidance and best practices for remediation.
- **Raw Event**: The raw event data received from the Entra ID tenant’s log provider. The data includes information such as who initiated the change, when it was initiated, what the change is, what the old value was, and what the new value is. The raw event data is represented in the JSON format that is easy to understand. The code is well-indented and has a key-value pair. Click **Download JSON** to download the JSON file for further investigation.
[See image.](#itdr-entra-cd-issue-remediate-details-image)
[]![Select an Entra ID tenant to view change details](/downloads/itdr/dashboard/entra-id-change-detection/viewing-entra-id-change-detection-issue-and-remediation-details/itdr-custom-result-dropdown.png)
[]![Entra ID Change Detection View icon](/downloads/itdr/dashboard/entra-id-change-detection/viewing-entra-id-change-detection-issue-and-remediation-details/itdr-entraID-view-icon.png)
[]![View Entra ID change detection details](/downloads/itdr/dashboard/entra-id-change-detection/viewing-entra-id-change-detection-issue-and-remediation-details/itdr-about-entra-id-cd-view-change-details.png)