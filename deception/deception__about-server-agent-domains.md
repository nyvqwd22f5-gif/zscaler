# About Server Agent Domains
Source: https://help.zscaler.com/deception/about-server-agent-domains
PDF: https://help.zscaler.com/pdf/com/en/1531612.pdf

The Server Agent Domain feature provides a centralized view of all domains and their associated domain controllers. This feature allows you to monitor the status of domain controllers and their configured capabilities. You can configure server agent policies and assign server agents to manage the [deployment of Active Directory (AD) decoys](/deception/about-active-directory-decoys).
Server agent domains provide the following benefits and enable you to:
- View the real-time status of domain controllers.
- Configure the server agent policy and assign a server agent to manage the deployment of AD decoys.
About the Domains Page
On the Domains page (Settings > Server Agent Settings > Domains), you can do the following:
- View the list of domains. For each domain, you can see:
- **Domain**: The name of the domain.
- **Total DCs**: The total number of domain controllers assigned to the domain.
- **Active**: The number of active domain controllers.
- **Inactive**: The number of inactive domain controllers.
- **Not Installed**: The number of domain controllers where the server agent is not installed.
- **Capabilities Installed**: The capabilities installed on the domain controllers.
- [Enable AD decoy deployment on a server agent](/deception/configuring-server-agent-policy).
![View server agent domains page](/downloads/deception/settings/server-agents-settings/domains/about-server-agent-domains/zscaler-deception-server-agent-domains.png)