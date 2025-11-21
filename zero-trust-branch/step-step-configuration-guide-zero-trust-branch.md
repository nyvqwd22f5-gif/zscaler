# Step-by-Step Configuration Guide for Zero Trust Branch
Source: https://help.zscaler.com/zero-trust-branch/step-step-configuration-guide-zero-trust-branch
PDF: https://help.zscaler.com/pdf/com/en/1532103.pdf

This guide takes you through the configuration steps you need to complete before using Zscaler Zero Trust Branch for your organization.
Before you begin configuring Zero Trust Branch, Zscaler recommends reading the following articles:
- [What Is Zero Trust Branch?](/zero-trust-branch/what-zero-trust-branch)
- [Usage Guidelines for Zero Trust Branch Appliances](/zero-trust-branch/usage-guidelines-zero-trust-branch-appliances)
Configuring Zero Trust Branch
To configure a Zero Trust Branch appliance, complete the following steps:
- [Step 1: Update Administrator and Role Management Information](#Admin)
- [Step 2: Deploy the Appliance](#Deploy)
- [Step 3: Configure Policies](#Policies)
- [Step 4: Configure Network Services](#network-services)
- [Step 5: Configure High Availability and Resilience](#high-availability)
- [Step 6: Set Up Identity-Aware Connectivity](#identity-aware-svcs)
- [Step 7: Configure Network Segmentation and Isolation](#segmentation-isolation)
- [Step 8: Perform Network Monitoring and Analytics](#monitor-analytics)
- [Step 9: Handle Appliance Maintenance and Lifecycle Management](#maintenance-lifecycle)
[]Zero Trust Branch uses ZIdentity as its sole identity and authentication management service, and Zero Trust Branch has predefined roles.
To learn more, see:
- [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups)
- [Understanding Zero Trust Branch Access Roles](/zero-trust-branch/understanding-zero-trust-branch-access-roles)
[]Deployment steps include creating a site, testing connectivity, activating the site, and verifying traffic flow.
To learn more, see [Deploying a Zero Trust Branch Appliance](/zero-trust-branch/deploying-zero-trust-branch-appliance).
[]Now that the appliance is up and running, configure policies to secure traffic and control its flow.
- [DNS Policies](#Forwarding)
- [Firewall Policies](#Firewall)
- [Routing Policies](#Routing)
[]You can use DNS policies to define rules that control DNS requests and responses to your Zero Trust Branch sites.
To learn more, see:
- [What Are Site DNS Policies?](/zero-trust-branch/what-site-dns-policies)
- [Configuring DNS Site Policies](/zero-trust-branch/configuring-site-dns-policies)
[]Zero Trust Branch allows you to create network-isolation and endpoint-isolation policies to mitigate lateral threat movements.
To learn more, see:
- [Understanding Firewall Policies](/zero-trust-branch/understanding-firewall-policies)
- [Configuring Firewall Policies](/zero-trust-branch/configuring-firewall-policies)
[]You can create routing policies to control traffic from branch sites to specific destinations based on defined criteria, ensuring secure and optimized routing.
To learn more, see:
- [Understanding Routing Policies](/zero-trust-branch/understanding-routing-policies)
- [Configuring Routing Policies](/zero-trust-branch/configuring-routing-policies)
[]Network services manage IP addressing and access to the internet.
- [Dynamic Host Configuration Protocol (DHCP)](#dhcp)
- [Domain Name Server (DNS)](#dns)
[]Zero Trust Branch appliances rely on a DHCP server to assign IP addresses and other network settings. Your site acts as either a DHCP server or as a DHCP relay, depending on the template used to create the site. When configured as a DHCP relay, Zero Trust Branch receives client requests and forwards them to DHCP servers across secure WAN links.
[]Zero Trust Branch appliances allow admins to define and enforce DNS policies that regulate the handling of DNS queries originating from branch sites. These policies enable precise control over DNS requests and responses, ensuring adherence to security and compliance requirements.
To learn more, see [Configuring Site DNS Policies](/zero-trust-branch/configuring-site-dns-policies).
[]Use the following features to ensure that your Zero Trust Branch appliances are continuously accessible and reliable, and operate at the highest level possible.
- [Zero Trust Branch High Availability Clusters](#ha)
- [Virtual Router Redundancy Protocol (VRRP)](#vrrp)
- [Routed Tunnels](#rt)
[]A Zero Trust Branch high availability (HA) cluster consists of two identical Zero Trust Branch appliances (or *nodes*). One node is the primary node and has the active role. The other node is the secondary node and has the standby role. If the primary node fails, the secondary node takes over as the primary, active node.
To learn more, see [Creating a Zero Trust Branch High Availability Cluster](/zero-trust-branch/creating-zero-trust-branch-high-availability-cluster).
[]VRRP allows multiple Zero Trust Branch appliances to share a virtual IP address, minimizing downtime and enhancing overall reliability and security.
To learn more, see [Configuring a High Availability Site with Virtual Router Redundancy Protocol](/zero-trust-branch/configuring-ha-site-vrrp).
[]Zero Trust Branch allows secure remote site connectivity over routed tunnels via border gateway protocol (BGP).
To learn more, see [Configuring Zero Trust Branch Site-to-Site Connectivity Over Routed Tunnels](/zero-trust-branch/configuring-zero-trust-branch-over-routed-tunnels).
[]Zscaler Private Access (ZPA) leverages the ZPA App Connector to securely connect users and applications in branch offices to private applications hosted in other branch environments.
To learn more, see [Understanding Private Application Connectivity for Branches](/zero-trust-branch/understanding-private-app-connectivity-branches).
[]Zero Trust Branch supports features for network segmentation, control, and security.
- [Airgap Solutions: Airgap-Lite and Airgap+](#airgap)
- [NAC-MAC Authentication](#nac-mac)
- [Ransomware Kill Switch](#ransomware)
[]Zero Trust Branch offers several solutions tailored to meet the unique security and isolation requirements of highly sensitive or regulated organizations. These solutions, which you select when you add or edit an asset, address varying levels of network isolation and functionality needs.
To learn more, see:
- [Understanding Protection Solutions](/zero-trust-branch/understanding-protection-solutions)
- [Configuring Airgap-Lite Mode for Assets](/zero-trust-branch/configuring-protection-mode-assets)
- [Managing Your Assets](/zero-trust-branch/managing-your-assets)
[]NAC-MAC authentication is a network access control (NAC) method that allows access based on MAC address lists.
To learn more, see [Uploading a NAC-MAC Authentication List](/zero-trust-branch/uploading-nac-mac-authentication-list).
[]The Zscaler Ransomware Kill Switch is a one-click attack surface-reduction tool integrated into Zero Trust Branch. It empowers you to rapidly contain ransomware threats without disrupting critical business operations.
To learn more, see:
- [Understanding the Ransomware Kill Switch](/zero-trust-branch/understanding-ransomware-kill-switch)
- [Configuring the Ransomware Kill Switch for a Site](https://help.zscaler.com/zero-trust-branch/configuring-ransomware-kill-switch-site)
[]Zero Trust Branch supports a variety of ways to view and analyze traffic, review interface health, and monitor and manage your network.
- [Traffic Analytics](#traffic-analytics)
- [Interface Health Monitoring](#interface-monitoring)
- [Integration with SIEM and Other Monitoring Tools](#siem-tools)
- [SNMP Configuration (v2/v3)](#snmp-config)
[]Zero Trust Branch provides extensive visibility into lateral traffic, which allows you to monitor and troubleshoot your packet logs and flow logs.
To learn more, see:
- [Viewing Traffic Flow Charts](/zero-trust-branch/viewing-traffic-flow-charts)
- [Monitoring & Logs](/zero-trust-branch/monitoring-and-logs)
[]Zero Trust Branch offers support for multiple WAN links and can automatically switch traffic upon detecting failures. This is achieved by tracking key metrics on the WAN interface, such as loss, latency, and jitter, and using "best link" traffic distribution within the routing policy rule.
For more information, see [Interface Monitoring](https://help.zscaler.com/zero-trust-branch/interface-monitoring).
[]Zero Trust Branch integrates with third-party and Zscaler services to extend visibility, automate response workflows, and enrich analytics across your enterprise systems. The supported integrations include tools for monitoring, security orchestration, IT service management, and analytics.
To learn more, see:
- [About Integrations](/zero-trust-branch/about-integrations)
- [Configuring SIEM Integration](/zero-trust-branch/configuring-siem-integration)
[]Zero Trust Branch supports the Simple Network Management Protocol (SNMP) standard for network monitoring and management. Both SNMPv2 and SNMPv3 are supported.
To learn more, see [Managing SNMP Configurations](/zero-trust-branch/managing-snmp-configurations).
[]Zero Trust Branch upgrades provide new features, bug fixes, and performance and security improvements. Zscaler Support works with you to troubleshoot issues you might encounter with your Zero Trust Branch appliances.
- [Software Upgrades](#upgrades)
- [Return Merchandise Authorization (RMA)](#rma)
[]A rich set of upgrade options are available from the **Sites **page in the Zero Trust Branch Admin Portal. An **Upgrade available** button indicates that a site is eligible for upgrade.
[]Zscaler Support works with you to troubleshoot and diagnose Zero Trust Branch appliance issues remotely. If the issue cannot be resolved remotely or is determined to be a hardware fault, Zscaler offers comprehensive advanced replacement services.
To learn more, see [Return Merchandise Authorization Process and Policy](/zero-trust-branch/return-merchandise-authorization-process-and-policy-ztb).