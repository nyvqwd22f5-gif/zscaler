# About the Control Panel
Source: https://help.zscaler.com/unified/about-control-panel
PDF: https://help.zscaler.com/pdf/com/en/1514856.pdf

Advanced SaaS Security Posture Management (SSPM) provides a collection of recommended security posture controls that help organizations proactively identify, monitor, and remediate configuration vulnerabilities and compliance risks across their Software as a Service (SaaS) applications, ensuring continuous protection and alignment with industry standards. By default, all controls are enabled. Each one has a Control Panel that provides a deep dive into the control for a comprehensive picture of its security posture and compliance.
The Control Panel provides the following benefits and enables you to:
- Review and understand the control.
- View and change the severity level of the control, and enable or disable the control.
- Remediate your organization's SaaS security posture from potential threats.
- View the compliance information for the control.
- View assets' status and disable assets that have misconfigured attributes.
The Control Panel consists of the following:
- [Control Panel Header](#Control-Panel-Header)
- [Remediation Tab](#Remediation-Tab)
- [Compliance Tab](#Compliance-Tab)
- [Assets Tab](#Assets-Tab)
- [Audit Log Tab](#Audit-Log)
- [Notes Tab](#Notes-tab)
If the status of a policy is pending, the policy is not displayed on the[ Posture page](/unified/about-posture).
[]On the Control Panel header, you can do the following:
- View basic information such as the control's name, description, status (e.g., **Fail)**, complexity (e.g., **Low**), category (e.g.,** Administrator**), tenant, and last scan time. Hover over the complexity to view a breakdown of the complexity level by categories such as Monitoring and Maintenance, Technical Effort, User Impact, and Documentation and Training.
- View and change the severity level of the control. To learn more, see [Updating the Control Severity](/unified/updating-control-severity). Hover over the severity level to view a breakdown of the severity.
- Enable or disable the control.
![Control Panel Header showing control information](/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/Control_Panel_Complexity.png)
[]On the **Remediation** tab, you can do the following:
- View information about potential security risks if the security posture is not configured per the recommended policy.
- View information about the impact on the user's experience after you remediate the misconfiguration.
- View information about the MITRE ATT&CK  tactic and techniques to understand the threat behavior and attack movement.
- View the steps to remediate your organization's security posture from potential threats. A link redirects you to remediation steps in the application's help documentation.
![Remediation Tab showing threat and remediation information](/downloads/tech-pubs-drafts/zia-draft-articles/about-control-panel-draft-doc-60282/Remediation_Tab_Latest.png)
[]On the **Compliance** tab, you can do the following:
- Search for a compliance framework by its name.
- View a list of all the compliance frameworks the control is mapped to. For each framework, you can view:
- **Name**: The name of the compliance framework.
- **Category**: The category of the controls within the framework. This information helps organizations understand the types of controls to be implemented across different areas of their operations.
- **No.**: The compliance control number assigned to the control within the framework. This number helps organizations reference and implement controls systematically.
![Compliance Tab showing list of compliance frameworks](/downloads/tech-pubs-drafts/zia-draft-articles/about-control-panel-draft-doc-57316/Compliance_Tab.png)
[]On the **Assets** tab, you can do the following:
- View the violation description that informs why the policy failed or what was evaluated.
- View the number of assets by their status. The asset status can be one of the following:
- **Fail**: The assets failed to comply with the policy.
- **Partial**: The assets partially comply with the policy. For example, if a repository in GitHub has multiple branches, and some of the branches are misconfigured, then the status for that repository is Partial.
- **Pass**: The assets comply with the policy.
- **Disabled**: The assets are disabled.
The controls are evaluated based on individual assets or global configuration, depending on the capabilities supported on the SaaS platform.
- Search for an asset.
- Filter the assets by their enablement status, or Pass, Fail, or Partial status.
- Export the assets report to a CSV file.
- View a list of all the assets scanned against the policy. For each asset, you can view:
-
**Asset**: The name of the asset. Click the name to expand and view more details such as general information and evidence. Click **Evidence**, and then click **Copy **to copy the evidence, or** **click **Download** to download it as a JSON file.
[See image.](#Evidence-Copy-and-Download)
- **Status**: The status of the asset.
- Enable or disable the asset.
The assets list is displayed depending on the platform. No assets are displayed for a global configuration.
![Assets Tab showing assets information](/downloads/tech-pubs-drafts/zia-draft-articles/about-control-panel-draft-doc-60282/Assets_Tab_Latest.png)
[]On the **Audit Log** tab, you can view details of all the changes made to the control.
![Audit Log Tab showing list of control changes](/downloads/tech-pubs-drafts/zia-draft-articles/about-control-panel-draft-doc-57316/Audit_Log_Tab.png)
[]On the **Notes **tab, you can add a note to the control that details the reason for an action taken on the control. The person's name who recently added the note and the date and time the note was added display. Additionally, you can comment on notes that other users add.
You must have user or admin permissions to add notes to the control. To learn more, see [About Roles in 3rd-Party App Governance](/unified/about-roles-3rd-party-app-governance).
![Control Panel Notes Tab showing user notes](/downloads/tech-pubs-drafts/zia-draft-articles/about-control-panel-draft-doc-57316/Control_Panel_Notes_0.png)
[]![Screenshot of Evidence Copy and Download Options ](/downloads/zia/policies/saas-security/posture-management/posture-management-advanced/about-control-panel/AssetEvidence_Copy.png)