# About Active Directory Posture
Source: https://help.zscaler.com/itdr/about-active-directory-posture
PDF: https://help.zscaler.com/pdf/com/en/1531620.pdf

Attackers compromise an Active Directory (AD) and then move to other systems, gaining high-level privileges. A security compromise of AD can destabilize the integrity of your identity management infrastructure. Active Directory Posture enables you to identify issues or risks related to AD, such as AS-REP roasting, Kerberoasting, accounts with weak permissions, etc. You can assign a Windows endpoint agent to scan the AD domain for identity misconfigurations.
Zscaler ITDR collects AD object (user and computer) attributes, such as objectSid, description, pwdLastSet, department, etc. After an AD domain is configured for scanning, attribute collection is enabled by default. The Windows endpoint agent assigned for scanning the AD domain collects the attributes. ITDR leverages these attributes to provide context for the misconfigurations detected in AD.
Active Directory Posture enhances your ITDR experience by enabling you to:
- Scan your AD domains via an endpoint agent to discover identity misconfigurations.
- Remediate AD security vulnerabilities and disrupt attack paths.
About the Active Directory Posture Page
On the Active Directory Posture page (ITDR > Manage > Active Directory Posture), you can do the following:
- View a list of AD domains that are scheduled for scanning. For each AD domain, you can view:
- **Domain Name**: The name of the AD domain.
- **Scan Frequency**: The scheduled scan frequency (**Daily**, **Weekly**, **Monthly**, or **Quarterly**).
-
**Agents**: The endpoint agents that run the scan.
If an endpoint agent has not checked in for more than 7 days, it is removed from the scan and its **Current State** status is set to **Error**.
- **Info**: The last and upcoming scan dates.
- **Last Scan Status**: The last scan status (**Scan Completed**, **Processing scan data**, **Unable to connect to the domain**, **Scan Timed Out**, **Scan Canceled**, or **Scan** **Failed)**.
- **Current State**: The current scan status. The statuses are as follows:
- **Active**: The scan is enabled.
- **Disabled**: The scan is disabled.
- **Waiting**: Waiting to connect to the endpoint agent, so that the agent can start the AD scan.
- **Scanning**: The scan is in progress.
- **Error**: The endpoint agent is uninstalled or deleted.
- [Scan an AD domain](/itdr/scanning-active-directory).
- [Stop an ongoing scan](/itdr/stopping-ongoing-scan).
- View the **Attribute Collection** status (enabled by default), scheduled scan frequency (**Weekly** or **Monthly**), last scan status and date, and upcoming scan date.
- Enable or disable [change detection](/itdr/about-active-directory-change-detection) to detect and monitor active changes in your AD domain.
- [Edit or delete a scan](/itdr/editing-or-deleting-scan).
- [Trigger an on-demand scan](/itdr/triggering-demand-scan).
![The Active Directory Posture page](/downloads/itdr/itdr/active-directory-posture-scan/about-active-directory-posture/AD%20collection.png)