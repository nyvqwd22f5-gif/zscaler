# Best Practice Guide for Active Directory Decoys
Source: https://help.zscaler.com/deception/best-practice-guide-active-directory-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531578.pdf

This best practice guide provides use cases and deployment recommendations for Active Directory (AD) decoys.
AD infrastructure is a critical resource for managing the IT infrastructure in an organization. It is a target for adversaries who perform reconnaissance to map and identify the resources in an organization. After the information is retrieved from the AD, the adversaries move laterally to other assets, thus expanding their initial reach.
To secure your AD infrastructure, you can create and deploy AD decoys, such as decoy service accounts, decoy privileged accounts, decoy dictionary usernames, decoy *nix accounts, etc. AD decoys detect attackers running reconnaissance and privilege escalation. AD decoys reduce the attack surface by detecting and containing attackers before they laterally move within the network. To learn more, see [About Active Directory Decoys](/deception/about-active-directory-decoys).
Zscaler recommends that you deploy a minimum of 10 AD decoys. A typical deployment must contain a minimum of:
- One business-critical, Unix, and well-known user decoy AD account.
- One decoy AD account with a fake password configured as the description.
- Two decoy AD privileged accounts, service accounts, and persona accounts.
- Two decoy AD accounts with a distinct decoy share path.
- Two decoy AD accounts with the Can Password Expire field enabled.
When creating AD decoys:
- Configure decoy names and properties as per the internal naming conventions.
- Place decoys in different OUs that host high-value users.
- Ensure that the logon workstations are configured for operation security (OPSEC) safety for the privileged AD accounts.
- Ensure decoy user and computer objects don't have keywords containing "decoys," "Zscaler," or "Deception".
The following are some of the use cases for AD decoys:
- [Use Case: Deploy Decoy AD Service Accounts to Detect Kerberoasting Attempts](#deception-bp-ad-uc-service-account)
- [Use Case: Deploy Decoy AD Privileged Accounts to Detect Privilege Escalation Techniques](#deception-bp-ad-uc-privi-account)
- [Use Case: Deploy Decoy AD Privileged Service Accounts to Detect Kerberoasting Attempts](#deception-bp-ad-uc-privi-serv-account)
- [Use Case: Deploy Decoy AD Persona Account to Lure Adversaries](#deception-bp-ad-uc-persona-account)
- [Use Case: Deploy Decoy AD User Accounts with Popular Dictionary Usernames to Detect Brute Force Attacks](#deception-bp-ad-uc-dictionary-account)
- [Use Case: Deploy Decoy *NIX User Accounts to Detect AS-REP Roasting Attack](#deception-bp-ad-uc-nix-account)
- [Use Case: Deploy Decoy AD User Accounts That Mimic Business-Critical Applications](#deception-bp-ad-uc-critical-account)
[]Adversaries escalate privileges in an AD environment using Kerberoasting attack. This attack specifically targets service accounts with service principal names (SPN). The Kerberoasting attack abuses the Kerberos protocol to harvest password hashes from service accounts.
Deploying decoy AD service accounts helps you to detect Kerberoasting attacks. This makes the adversary believe that they have obtained hashes to the service account while, at the same time, you are mitigating the risk of Kerberoasting a real service account.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a username that is a combination of location name, service name, and postfix "svc" (e.g, `nysqlsvc`).
- **OU**: Enter the AD service account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Description**: Enter a description that is a combination of location name and service name (e.g., `New York service account for DB`).
-
**Make Account Kerberoastable**: Select a [network decoy](/deception/creating-internal-network-decoy) that represents a DB server with MySQL and PostgreSQL DB services enabled.
[See image.](#deception-bp-ad-service-account-image)
[]Privileged user accounts in AD have powerful rights, privileges, and permissions. Privileged users can perform any critical operations in AD and domain-joined systems. If attackers gain access to these accounts, they’ll steal information and disrupt business operations.
Deploying decoy AD privileged accounts help you detect privilege escalation techniques, such as brute force. Some privileged AD groups include administrators, domain admins, and enterprise admins. Configuring enticing descriptions like passwords or password hints helps you to detect attacks.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a name that mimics an administrator user (e.g., `ADglobaladmin`).
- **OU**: Enter the AD privileged account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Group membership**: Enter the group name of the decoy user (e.g., `Domain Admins`, `Administrators`, etc.). Adversaries often target user accounts that are members of privileged administrative groups.
- **Description**: Enter a fake password description (e.g., `The password is globaladmin-1@$52314`).
-
**Restrict Logon To**: Select a [network decoy](/deception/creating-internal-network-decoy) from the drop-down menu that represents sysadmin workstations to configure the `logonworkstations` attribute for the decoy privilege account.
[See image.](#deception-bp-ad-privi-acc-image)
[]Deploying a Kerberoastable decoy privileged service account lures the adversaries to harvest password hashes. The decoy mitigates the risk of Kerberoasting a real privileged service account.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a name that mimics an administrator user (e.g., `backupadmin`).
- **OU**: Enter the AD privileged service account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Group membership**: Enter the group name of the decoy user (e.g., `Domain Admins`, `Administrators`, etc.).
- **Description**: Enter a fake password description (e.g., `Backup server admin account`).
-
**Restrict Logon To**: To ensure that this account can only log in to the specified destination, select a [network decoy](/deception/creating-internal-network-decoy) from the drop-down menu (recommended for OPSEC safety).
[See image.](#deception-bp-ad-privi-serv-acc-image)
[]Persona accounts are user accounts that represent a specific group. Deploying a decoy AD persona account that represents an administrator or domain admin group lures adversaries to launch an attack while, at the same time, secures your real user account.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a name that mimics an admin account (e.g., `john-adm`).
- **OU**: Enter the admin account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Can Password Expire**: Enable to activate the password expiration feature.
- **Group membership**: Enter the group name of the decoy user (e.g., `Domain Admins`, `Administrators`, etc.).
- **Description**: Enter a fake password description (e.g., `Default password`).
- **Profile Path (File Share Discovery Lure)**: Select a [network decoy](/deception/creating-internal-network-decoy) with Shares service from the drop-down menu to configure the `profilePath` attribute for the decoy user account. Adversaries analyze this attribute to discover file shares.
[See image.](#deception-bp-ad-persona-acc-image)
[]One of the ways adversaries gain access to an AD environment is by identifying a known user account. They perform brute force attack and compromise the AD. They identify accounts using a popular word list of usernames and passwords. Deploying decoy AD user accounts with popular dictionary usernames helps you to detect brute force attacks.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a common name that is found in a dictionary (e.g., `admin01`, `admin02`, `helpdesk`, `azure`, etc.).
- **OU**: Enter the admin account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Group membership**: Enter the group name of the decoy user (e.g., `Domain Admins`, `Administrators`, etc.).
- **Description**: Enter a fake password description (e.g., `The password is 123456`).
[See image.](#deception-bp-ad-dictionary-acc-image)
[]Similar to Kerberoasting, adversaries target domain accounts that do not require authentication to escalate privileges. Deploying decoy *nix user accounts that have authentication disabled lures adversaries and detects AS-REP roasting attacks.
**Recommendations**:
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a username (e.g., `unix`, `rhel`, `centos`, `linux`).
- **OU**: Enter the generic account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Pre-auth Not Required**: Enable to make the user account vulnerable to AS-REP roasting attacks.
- **Description**: Enter the description (e.g., `RHEL server admin`).
[See image.](#deception-bp-ad-nix-acc-image)
[]You can create decoy AD user accounts that mimic sensitive business-critical accounts or applications. These AD decoys can detect attacks against critical accounts.
[Create an AD decoy](/deception/creating-decoy-active-directory-user) with the following configurations:
- **User Name**: Enter a username that is a combination of application or service name and username (e.g, `swiftadmin`).
- **OU**: Enter the Swift account OU.
- **First Name**: Enter the same name as entered in **User Name**.
- **Group membership**: Enter the tier 2 AD model privileged group name (e.g., `Swift admins`).
- **Restrict Logon To**: Select a [network decoy](/deception/creating-internal-network-decoy) (representing Swift user workstation) from the drop-down menu.
See image.
[]![Configure a decoy AD service account](/downloads/tech-pubs-drafts/deception-draft-articles/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-service-account-1.png)
[]![Configure a decoy AD privileged account ](/downloads/tech-pubs-drafts/deception-draft-articles/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-priv-account.png)
[]![Configure an AD privileged service account](/downloads/deception/getting-started/best-practices/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-priv-service-account-1.png)
[]![Configure an AD decoy persona account](/downloads/deception/getting-started/best-practices/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-persona-account-2.png)
[]![Configure decoy AD accounts with dictionary usernames](/downloads/tech-pubs-drafts/deception-draft-articles/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-dictionary-acc.png)
[]![Configure decoy *nix AD user account](/downloads/tech-pubs-drafts/deception-draft-articles/best-practice-guide-active-directory-decoys/zscaler-deception-bp-ad-nix-account.png)