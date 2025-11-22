# Enabling Remediation on a Domain
Source: https://help.zscaler.com/itdr/enabling-remediation-domain
PDF: https://help.zscaler.com/pdf/com/en/1531873.pdf

The remediation feature enables you to run remediations for risky AD identities using a server agent. This helps improve the security posture of the AD domain. To run remediations, you must enable remediation on the server agent domain.
Remediation actions are available on the following dashboards:
- [Active Directory Posture](/itdr/running-remediation-actions-ad-identities)
- [Password Analysis](/itdr/viewing-password-analysis-details-remediate-issues)
- [Active Directory Change Detection](/itdr/running-remediation-actions-change-detection)
To enable remediation on a server agent domain:
- Go to **Settings** > **Server Agent Settings** > **Domains**.
-
Locate the domain you want, and click the **Edit** icon under the **Actions **column.
[See image.](#server-agent-domains-page)
-
In the dialog window, select **Remediation**. Set the following options:
- **Enabled**: Select to enable remediation.
- **Agent**: Select a server agent from the drop-down menu to run the remediation. Only one server agent can be selected to run the remediation action.
[See image.](#domain-drawer)
- Click **Save**.
After enabling, you can run remediation actions on the AD identities and view the [remediation history](https://help.zscaler.com/itdr/v4_29/viewing-ad-remediation-history) or log details for further analysis.
[]![The server agent domain dialog window with list of available actions.](/downloads/itdr/settings/server-agents-settings/domains/enabling-remediation-server-agent/itdr-remediation-tab.png)
[]![The server agent settings page with list of configured domains.](/downloads/itdr/settings/server-agents-settings/domains/enabling-remediation-server-agent/itdr-server-agent-domain-edit.png)