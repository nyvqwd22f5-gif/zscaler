# Step-by-Step Configuration Guide for Zscaler Deception
Source: https://help.zscaler.com/deception/step-step-configuration-guide-zscaler-deception
PDF: https://help.zscaler.com/pdf/com/en/1531471.pdf

This guide takes you through the configuration steps you need to complete to begin using Zscaler Deception for your organization.
Before you begin configuring Deception, Zscaler recommends reading the following articles:
- [What Is Zscaler Deception?](/deception/what-zscaler-deception)
- [Understanding the ](/deception/understanding-zscaler-deception-architecture)[Zscaler Deception](/deception/what-zscaler-deception)[ Architecture](/deception/understanding-zscaler-deception-architecture)
Configuring Deception
To configure Deception, complete the following steps:
- [Step 1: Log In to the Zscaler Deception Admin Portal](#deception-step-by-step-log-in)
- [Step 2: Configure Users & Roles](#deception-step-by-step-user-roles)
- [(Optional) Step 3: Configure Single-Sign-On Authentication](#deception-step-by-step-config-sso)
- [Step 4: Launch Your Deception Campaign](#deception-step-by-step-launch-deception)
- [Step 5: Configure SIEM Integration](#deception-step-by-step-siem-integration)
- [Step 6: Configure Alert Notifications](#deception-step-by-step-alerts)
[]After your organization is provisioned for Deception, you will receive an email with the following details:
- Link to your Deception instance
- Link to set your password
- Security code
Click the password link to set your password and the two-factor authentication (2FA) code. To learn more, see [Accessing and Navigating the Zscaler Deception Admin Portal](/deception/accessing-and-navigating-zscaler-deception-admin-portal).
[]Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to add [users](/zidentity/adding-users) and [roles](/zidentity/adding-zidentity-admin-roles). Contact Zscaler Support to subscribe to ZIdentity.
You can provision users who can access the Deception Admin Portal. Users can access and manage different modules in the portal based on the roles assigned to them. To learn more, see [About Users & Roles](/deception/about-users-roles).
[]Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to [configure primary and secondary external identity providers (IdPs)](/zidentity/configuring-okta-external-idp). ZIdentity supports both SAML and OpenID configurations.
You can enable single sign-on (SSO) to your Deception Admin Portal via SAML or OpenID. To learn more, see the following articles:
- [Configure SAML for SSO](/deception/configuring-saml-single-sign)
- [Configure SAML for SSO using Okta](/deception/configuring-saml-okta-single-sign)
- [Configuring SAML for Microsoft Azure Active Directory Single Sign-On](/deception/configuring-saml-azure-active-directory-single-sign)
- [Configuring SAML for Active Directory Federation Services](/deception/configuring-saml-active-directory-federation-services)
- [Configure OpenID for SSO](/deception/configuring-openid-single-sign)
- [Configure OpenID for SSO using Okta](/deception/configuring-openid-single-sign-using-okta)
- [Configure OpenID for SSO using Google](/deception/configuring-openid-single-sign-using-google)
[]You can configure and deploy decoys across your public-facing assets, Zero Trust Network, Internal, Landmine, Active Directory (AD), etc. to detect advanced threats that might have bypassed existing defenses. You can create and deploy the following decoys based on the use case:
- [Threat Intelligence Decoys](#deception-step-by-step-ti)
- [Zero Trust Network Decoys](#deception-step-by-step-zpa)
- [Internal Network Decoys](#deception-step-by-step-internal-network)
- [Cloud Decoys](#cloud-deception)
- [Landmine Decoys](#deception-step-by-step-landmine)
- [Active Directory Decoys](#deception-step-by-step-active-directory)
[]Threat Intelligence (TI) decoys provide analytics of an attacker's activity early in the reconnaissance phase of the kill chain. These decoys generate organization-specific intelligence about reconnaissance attempts and subsequent attacks against your public-facing assets. To learn more, see the following articles:
- [About Threat Intelligence Decoys](/deception/about-threat-intelligence-decoys)
- [Creating a Threat Intelligence Decoy](/deception/creating-threat-intelligence-decoy)
- [Creating Threat Intelligence Decoys Based on Recommendations](/deception/creating-threat-intelligence-decoy-based-recommendations)
[]A Zero Trust Network decoy uses the Zscaler Private Access (ZPA) service built on a Zero Trust Network Access (ZTNA) platform to detect scanning and lateral movement activities in your network environment. To learn more, see the following articles:
- [About Network Decoys](/deception/about-network-decoys)
- [Using Network Decoy Personalities and Services](/deception/using-network-decoy-personalities-and-services)
- [Creating a Zero Trust Network Decoy](/deception/creating-zero-trust-network-decoy)
- [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy)
[]Internal network decoys detect scanning and lateral movement activities in your network. They mimic real assets on your network. You can deploy network decoys in business-critical network segments that host production servers, demilitarized zones (DMZ), key applications, databases, and cloud environments. To learn more, see the following articles:
- [About Decoy Connectors](/deception/about-decoy-connectors)
- [Configuring a Decoy Connector Management Network](/deception/configuring-decoy-connector-management-network)
- [Adding and Connecting a Decoy Connector to the Deception Admin Portal](/deception/adding-connecting-decoy-connector-admin-portal)
- [Configuring Proxy Settings for a Decoy Connector](/deception/configuring-proxy-settings-decoy-connector)
- [Configuring a Subnet](/deception/configuring-subnet)
- [About Network Decoys](/deception/about-network-decoys)
- [Using Network Decoy Personalities and Services](/deception/using-network-decoy-personalities-and-services)
- [Creating an Internal Decoy](/deception/creating-internal-network-decoy)
- [Configuring Services on a Network Decoy](/deception/configuring-services-network-decoy)
[]Cloud decoys lure and detect attacks and adversarial activities in your public cloud environment, such as Microsoft Azure and Amazon Web Services (AWS). You can lure and detect attacks originating from your own organization or outside your organization by deploying decoy resources that mimic legitimate Azure or AWS resources. To learn more, see:
- [Azure Decoys](#azure-decoys)
- [AWS Decoys](#aws-decoys)
- [][About Cloud Deception with Azure](/deception/about-cloud-deception-with-azure)
- [Setting Up Cloud Deception with Microsoft Azure](/deception/setting-cloud-deception-microsoft-azure)
- [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys)
- [Managing Azure Decoys](/deception/managing-azure-decoys)
- [][About Cloud Deception with AWS](/deception/about-cloud-deception-with-aws)
- [Setting Up Cloud Deception with AWS](/deception/setting-cloud-deception-aws)
- [Configuring Lures Using AWS Decoys](/deception/configuring-lures-using-aws-decoys)
- [Managing AWS Decoys](/deception/managing-aws-decoys)
[]Landmine decoys detect attacks against your endpoints and lure adversaries on your endpoints to other decoys in your environment. They can be decoy files, credentials, processes, and application lures on endpoints. You can create landmine decoys based on policies. A landmine agent fetches these policies and verifies if they apply to an endpoint, and then deploys the decoys. To learn more, see the following articles:
- [About Landmine Decoys](/deception/about-landmine-decoys)
- [Deploying Endpoint Deception With Zscaler Client Connector for Windows](/deception/deploying-endpoint-deception-zscaler-client-connector-windows)
- [Installing a Landmine Agent on Windows](/deception/installing-landmine-agent-windows)
- [Installing a Landmine Agent on Linux](/deception/installing-landmine-agent-linux)
- [Installing a Landmine Agent on macOS](/deception/installing-landmine-agent-macos)
- [About Landmine Policies](/deception/about-policies)
- [Creating a Landmine Policy](/deception/creating-landmine-policy)
[]Active Directory (AD) decoys detect attackers running reconnaissance and privilege escalation in your active directory environment. You can create decoy AD users and computers to detect enumeration activity or malicious access. To learn more, see the following articles:
- [About Active Directory Decoys](/deception/about-active-directory-decoys)
- [Adding an Active Directory Domain](/deception/adding-active-directory-domain)
- [Creating a Decoy Active Directory User](/deception/creating-decoy-active-directory-user)
- [Configuring and Downloading a Trigger Script](/deception/configuring-and-downloading-trigger-script)
- [Running the Decoy Deployment Script on an Active Directory](/deception/running-decoy-deployment-script-active-directory)
[]You can configure a Service Connector to forward logs in real time. Security Information and Event Management (SIEM) integration provides visibility in a centralized console and allows your security teams to leverage the solution's existing security investigation workflows. To learn more, see the following articles:
- [About SIEM Integrations](/deception/about-siem-integrations)
- [About Service Connectors](/deception/about-service-connectors)
- [Configuring a Service Connector](/deception/configuring-service-connector)
- Configuring SIEM integration for the following supported platforms:
- [ArcSight](/deception/siem-configuration-guide-arcsight)
- [IBM QRadar](/deception/siem-configuration-guide-ibm-qradar)
- [Microsoft Azure Sentinel](/deception/siem-configuration-guide-microsoft-azure-sentinel)
- [Netmonastery DNIF](/deception/siem-configuration-guide-netmonastery)
- [Splunk](/deception/siem-configuration-guide-splunk)
- [Syslog](/deception/deception-and-syslog-server-deployment-guide)
- [Sumo Logic](/deception/siem-configuration-guide-sumo-logic)
[]You can enable and configure alert notifications to generate emails when a warning or critical security event occurs in the Deception Admin Portal.
You can configure the email alert notifications per user. Notifications are sent to the user when there is an issue with the decoys, license, or system. Notifications are not sent if something happens on the decoys. To learn more, see [Enabling Email Alert Notifications for a User](/deception/about-users-roles#deception-enable-email-notifications-events).
You can add Orchestrate rules to create alerts when something happens on the decoys. To learn more, see the following articles:
- [About Orchestration Rules](/deception/about-orchestration-rules)
- [Creating an Orchestration Rule](/deception/creating-orchestration-rule)