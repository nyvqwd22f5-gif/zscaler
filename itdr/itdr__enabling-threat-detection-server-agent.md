# Enabling Threat Detection on a Server Agent
Source: https://help.zscaler.com/itdr/enabling-threat-detection-server-agent
PDF: https://help.zscaler.com/pdf/com/en/1531874.pdf

The threat detection feature detects threats on the domain controller (DC) using a server agent. Zscaler ITDR identifies these threats and enriches the data with contextual information to make it easier to investigate and take required action. The following contexts are available for an attacker and target user:
- **Group memberships**: The list of Active Directory groups the user is part of.
- **Entra role assignments**: The list of role assignments for the user in the Entra ID.
- **Basic info**: Username, User Principal Name (UPN), Password Last Set, Organizational Unit (OU), Title, Department, etc.
- **AD Entra posture checks**: The list of AD and Entra posture checks that the user is present in.
- **Credex user info**: The list of credential exposures that the user is present in.
- **Password analysis**: The results of the user's password analysis.
- **User past threat detections**: The list of the user's past threat detections.
To enable threat detection on your server agent domain:
- Go to **Settings** > **Server Agent Settings** > **Domains**.
-
Locate the domain you want, and click the **Edit **icon under the** Actions** column.
[See image.](#click-edit)
-
In the dialog window, select **Threat Detection **and enable or disable the following options as necessary:
- **Enable All: **To detect all attacks.
- **Brute Force: **To detect brute force attacks.
- **Malicious Dpapi Usage: **To detect malicious export of Data Protection API (DPAPI) domain backup key.
- **Suspicious Group Additions: **To detect suspicious group membership additions.
- **Suspected Kerberoasting: **To detect kerberoasting attacks.
- **Suspected Kerberoasting (Encryption Downgrade): **To detect kerberoasting via encryption downgrade.
- **Suspected Asrep Roasting: **To detect AS-REP roasting attacks.
- **Suspicious Adminsdholder Modification: **To detect Admin Security Descriptor Holder (AdminSDholder) modifications.
- **Suspected Dcsync: **To detect DCSync attacks.
- **Suspected Dcshadow: **To detect DCShadow attacks.
- **Account Reconnaissance**: To detect account reconnaissance attacks.
- **Password Spray**: To detect password spray attacks.
- **External IP Authentication (DC)**: To detect login attempts from public IP addresses for credential theft, brute force attacks, or reconnaissance targeting exposed DCs.
- **Kerberos Service Ticket Anomaly**: To detect anomalous Kerberos ticket requests. This requires identifying abnormal events by first establishing a baseline of normal behavior for two weeks.
[See image.](#enable-threatdetection)
- Click **Save**.
[]
![The Server Agent Settings Domains page with the list of domains configured with annotation around edit icon.](/downloads/tech-pubs-drafts/itdr-draft-articles/enabling-session-tracking-password-analysis-or-threat-detection-server-agent/server-agent-domain-page.png)
[]
![The Threat Detection tab with the list of available. threat detections](/downloads/itdr/settings/server-agents-settings/domains/enabling-threat-detection-server-agent/itdr-enabling-threat-detection.png)