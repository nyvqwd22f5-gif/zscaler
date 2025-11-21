# Adding an Active Directory Domain
Source: https://help.zscaler.com/deception/adding-active-directory-domain
PDF: https://help.zscaler.com/pdf/com/en/1531331.pdf

To integrate decoy users and computers with an Active Directory (AD), you must first add and configure an AD domain in the Zscaler Deception Admin Portal. You can add and configure an AD domain with or without credentials. Zscaler recommends configuring an AD domain with credentials, as this is a prerequisite for a few features.
You can deploy AD decoy users and computers in AD domains managed by a server agent. Deploying AD decoys in domains managed by server agents provides the following benefits:
- Automates AD decoy deployment without the need to manually download and run deployment scripts.
- Streamlines event log collection without the need to configure trigger scripts for forwarding AD event logs. All server agents installed on a domain controller (DC) automatically monitor events and forward logs to the Deception Admin Portal.
- Improves the effectiveness of AD decoys by automatically refreshing them. The server agent periodically simulates activities on the AD decoy user and computers by performing password resets, login actions, etc., every few months. This ensures that decoys appear active and frequently used, mimicking legitimate assets.
To learn more, see [About Server Agent Domains](/deception/about-server-agent-domains).
Prerequisites
Before adding an AD domain, make sure that the following prerequisites are met:
- When you add an AD domain without credentials, you must have the following AD details:
- Domain name
- FQDN or hostname of the primary domain controller
- Network Basic Input/Output System (NetBIOS) name of the AD
- When you add an AD domain with credentials, you must have the following AD details:
- Domain name
- FQDN of the primary DC
- NetBIOS name of the AD
- Credentials to an AD user with the following permissions to:
- Add computer objects to an AD
- Query LDAP on domain controllers
- The Root CA certificate of the primary domain controller
- Connectivity from one of the Decoy Connectors to the AD domain controller over TCP port 636 (LDAP).
Adding and Configuring an AD Domain
You can add an AD domain using a server agent. To learn more, see [Installing a Server Agent](/deception/installing-server-agent).
To add an AD domain:
- Go to **Deceive** > **Active Directory Decoys** > **Domains**.
-
Click **Add Domain**.
[See image.](#deception-ad-add-domain-option)
-
In the **Domain Details** window:
- **Domain Name**: Enter the full FQDN name of the AD domain where the decoys are deployed.
- **Domain Controller**: Enter the FQDN or hostname of the primary domain controller.
- **Domain NetBIOS Name**: Enter the NetBIOS name of the AD domain where the AD decoys are deployed.
- **Decoy Connector as Receiver for Alerts**: Enable to send all alerts to the selected Decoy Connector instead of to the Deception Admin Portal.
- **Decoy Connector**: Select a Decoy Connector from the drop-down menu to which the alerts are sent.
- **Enable Enumeration Detection**: Enable to activate the enumeration detection feature for the AD domain.
-
**Credentials to Add Computers to Active Directory**: You can add computer objects to an AD domain with or without credentials. Enable to add computer objects to an AD domain with credentials and enter the following details:
- **Username**: Enter a username. The user must have permission to add computer objects to the domain and make LDAP queries to the domain controller.
- **Password**: Enter a password for the specified username.
- **Domain CA Certificate(.crt)**: Click **Upload** to [upload the domain CA Certificate](/deception/exporting-root-ca-certificate-active-directory-certificate-service) (.crt file) to enable a secure LDP connection in the PEM format.
If this setting is disabled, you must add the computer objects without credentials via a PowerShell script.
[See image.](#deception-ad-domain-config)
-
Click **Save**.
The AD domain is added to the **Domains** table.
[See image.](#deception-ad-domain-added)
AD domains added via server agents are appended with the **Managed by Server Agent** label. You cannot edit or delete these domains.
[]![The Add Domain option](/downloads/deception/deceive/active-directory-decoys/adding-active-directory-domain/zscaler-deception-ad-add-domain.png)
[]![Configure an AD domain](/downloads/deception/deceive/active-directory-decoys/adding-active-directory-domain/zscaler-deception-config-ad-domain-3.png)
[]![AD domain added](/downloads/deception/deceive/active-directory-decoys/adding-active-directory-domain/zscaler-deception-ad-domain-added-3.png)