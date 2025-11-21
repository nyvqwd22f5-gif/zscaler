# Configuring the Active Directory Threat Detection Module
Source: https://help.zscaler.com/itdr/configuring-active-directory-threat-detection-module
PDF: https://help.zscaler.com/pdf/com/en/1531667.pdf

The Active Directory (AD) threat detection module provides visibility into credential misuse, entitlement exposures, and privilege escalation activities in an AD. This detection module enables you to monitor the AD domain and privilege accounts for malicious activities and detect the following types of attacks via the endpoint agent:
- [**DCSync**](https://attack.mitre.org/techniques/T1003/006/): An attack that allows an adversary to simulate the behavior of a domain controller and retrieve password hashes from another domain controller in the AD environment.
- [**DCShadow**](https://attack.mitre.org/techniques/T1207/): A kill chain attack in which an adversary registers a fake AD domain controller and uses that to inject malicious AD objects (e.g., credentials) into other domain controllers that are part of the same AD infrastructure.
- **Zerologon (CVE-2020-1472)**: A privilege escalation vulnerability that allows an attacker to exploit a vulnerable domain controller, change the computer account password, and perform further attacks.
- **Session Enumeration**: A reconnaissance method that an adversary uses to gain domain dominance after compromising a system in an AD.
- [**Kerberoast**](https://attack.mitre.org/techniques/T1558/003/): A pervasive attack technique targeting AD service account credentials.
- **LDAP **[**Reconnaissance**](https://attack.mitre.org/tactics/TA0043/): A reconnaissance technique that attackers use to discover users, groups, and computers in an AD. The attackers use LDAP queries to find targets and plan the next stage of the attack.
To configure AD threat detection module for a policy:
- Go to **ITDR **> **Manage **> **Threat Detection**.
-
Locate the threat detection policy you want to use to detect AD attacks, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
-
In the **Threat Detection** window, select** Active Directory**, and enable or disable the following options as necessary:
- **DCSync**: Enable to detect DCSync attacks.
- **DCShadow**: Enable to detect DCShadow attacks.
- **Zerologon**: Enable to detect Zerologon attacks.
- **Session Enumeration**: Enable** **to detect Session Enumeration attacks.
- **Monitor Privileged Accounts**: Enable to monitor privileged accounts.
- **Monitor Decoy Accounts**: Enable to monitor AD decoy user accounts.
- **Kerberoast Detection (Anomaly)**: Enable to detect Kerberoast attacks on non-decoy service accounts.
- **Kerberoast Detection (Decoy)**: Enable to detect** **Kerberoast attacks on decoy service accounts.
- **Suspicious LDAP Activity**: Enable to detect LDAP reconnaissance activities.
[See image.](#deception-itdr-ad-config)
- Click **Save**.
Before you configure an AD threat detection module, make sure that you [scan an AD domain](/itdr/scanning-active-directory) and have at least one scan report.
In some AD threat detection modules, such as monitoring privileged accounts, when a new AD object is identified in the scan, it takes about 60 minutes for the endpoint agents to monitor the accounts for any activities.
[]![The option to edit a threat detection policy](/downloads/itdr/threat-detection-policies/configuring-active-directory-threat-detection-module/itdr-threat-detection-edit-icon.png)
[]![Configuring ITDR Active Directory](/downloads/itdr/threat-detection-policies/configuring-active-directory-threat-detection-module/itdr-ad-threat-detection-policy-window.png)