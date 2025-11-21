# Enabling Session Tracking and Password Analysis on a Server Agent
Source: https://help.zscaler.com/itdr/enabling-session-tracking-and-password-analysis-server-agent
PDF: https://help.zscaler.com/pdf/com/en/1531855.pdf

Session tracking is used to monitor logon activities for privileged accounts in the domain, and password analysis is used to identify compromised or weak passwords.
Enabling Session Tracking
To enable session tracking:
- Go to **Settings** > **Server Agent Settings** > **Domains**.
-
Locate the domain you want, and click the **Edit **icon under the** Actions** column.
[See image.](#edit_icon_for_domains_tab)
- In the dialog window, select **Session Tracking**.
-
Select **Enabled** to enable session tracking.
[See image.](#policy_configuring_for_server_agents)
- Click **Save**.
Session tracking is enabled, and you can view the details on the [AD User Details ](/itdr/viewing-affected-active-directory-user-account-details#itdr-aff-ad-user-session-tracking)page.
Enabling Password Analysis
To enable password analysis:
- Go to **Settings** > **Server Agent Settings** > **Domains**.
-
Locate the domain you want, and click the **Edit **icon under the** Actions** column.
[See image.](#view_edit_icon)
-
In the dialog window, select **Password Analysis**. Set the following options:
- **Enabled**: Select to activate password analysis.
- **Agent**: Select a server agent from the drop-down menu.
- **Frequency**: Select a scan frequency (**Weekly**, **Monthly**, or **Quarterly**) from the drop-down menu.
[See image.](#enable_password_analysis)
- Click **Save**.
Password analysis is enabled, and you can view the details in the [Password Analysis](/itdr/about-password-analysis-dashboard) dashboard.
[]
![View edit icon of domains page](/downloads/deception/settings/server-agents-settings/domains/configuring-server-agent-policy/zscaler-deception-server-agent-domains-edit-icon.png)
[]
![Enable session tracking](/downloads/tech-pubs-drafts/itdr-draft-articles/enabling-session-tracking-password-analysis-or-threat-detection-server-agent/itdr-enable-session-tracking.png)
[]
![View edit icon of domains page](/downloads/deception/settings/server-agents-settings/domains/configuring-server-agent-policy/zscaler-deception-server-agent-domains-edit-icon.png)
[]
![Enable password analysis](/downloads/tech-pubs-drafts/itdr-draft-articles/enabling-session-tracking-password-analysis-or-threat-detection-server-agent/itdr-enable-password-analysis.png)