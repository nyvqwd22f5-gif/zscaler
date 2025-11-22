# Viewing the Top Vulnerable Entra ID Identities
Source: https://help.zscaler.com/itdr/viewing-top-vulnerable-entra-id-identities
PDF: https://help.zscaler.com/pdf/com/en/1531757.pdf

You can view a list of the top 10 identities that have the highest risks in the Entra ID tenant on the [Entra ID Posture](/itdr/about-entra-id-posture-dashboard) dashboard. Having visibility of these 10 riskiest identities in your Entra ID helps you to prioritize what to focus on first. You can view issue details, such as risk type, user or service principal ID, severity level, etc. You can drill down to a specific identity to further investigate the issues and swiftly remediate the compromised identity.
To view the top vulnerable Entra ID identities:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID Posture **dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#entraID-result)
The scan result for the Entra ID tenant appears.
-
Click **Top 10 Identities**.
[See image.](#itdr-entra-id-top-10-vul-identity-list)
The **Identities** page appears listing the top vulnerable identities. You can view the following information:
- **Identity**: The name of the user or service principal.
- **Type**: Type of identity (**User**, **Service Principal**, etc.).
- **Types of Risks**: The description of all the risk types the identity is vulnerable to. Click the number to view all the risk types.
- **Principal ID**: The user or service principal ID.
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
[See image.](#itdr-entra-id-top-10-vul-details)
You can click **Download Identities** to download the issue details in the Excel format.
You can [double-click an identity to view additional details](/itdr/viewing-affected-entra-id-identity-details), such as posture risk score, failed posture checks, associated Okta user account details, Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) access snapshots, assigned roles, etc.
[]![View top 10 vulnerable identities in Entra ID](/downloads/itdr/dashboard/entra-id/viewing-top-vulnerable-entra-id-identities/itdr-entra-id-top-10-identities-list.png)
[]![View top 10 risky Entra ID identities](/downloads/itdr/dashboard/entra-id/viewing-top-vulnerable-entra-id-identities/itdr-entra-id-top-10-identities-details-2.png)
[]![ The Entra ID Posture dashboard with annotation around Result for and scanned on options.](/downloads/itdr/dashboard/entra-id/viewing-top-vulnerable-entra-id-identities/itdr-entra-id-post-scan-domain-date-without-options.png)