# Step-by-Step Configuration Guide for ZIA
Source: https://help.zscaler.com/zia/step-step-configuration-guide-zia
PDF: https://help.zscaler.com/pdf/com/en/1401206.pdf

This guide takes you through the configuration steps you need to complete to begin using Zscaler Internet Access (ZIA) for your organization.
Before you begin configuring ZIA, Zscaler recommends reading the following articles:
- [Understanding the ZIA Cloud Architecture](/zia/about-zscaler-cloud-architecture)
- [Accepting the End User Subscription Agreement (EUSA)](/zia/accepting-end-user-subscription-agreement-eusa)
- [Using the Zscaler Help Browser](/zia/using-zscaler-help-browser)
Configuring ZIA
To configure ZIA, complete the following steps:
- [Step 1: Update Company and Administrator Information](#admin)
- [Step 2: Configure Your Authentication and Provisioning Methods](#auth)
- [Step 3: Configure Your Traffic Forwarding](#forward)
- [Step 4: Configure Your Locations](#location)
- [Step 5: Configure Your Policies](#policy)
- [Step 6: Configure Your Analytics](#analytics)
[]To update your company information and configure administrators as applicable, see:
- [About the Company Profile](/zia/about-company-profile)
- [About Administrators](/zia/about-administrators)
- [Adding ZIA Admins](/zia/adding-admins)
- [About Role Management](/zia/about-role-management)
- [Adding Admin Roles](/zia/adding-admin-roles)
[]To implement group and user policies and to leverage the granular reporting capabilities of the service, you must provision users and enable the Zscaler service to authenticate them.
Provisioning involves uploading usernames, groups, and departments to the service database. Enabling authentication allows the Zscaler service to identify the traffic that it receives so it can enforce the configured department, group, and user policies, and provide user and department logging and reporting.
The Zscaler service supports multiple methods for provisioning and authenticating your users.
To learn more, see:
- [Provisioning and Authenticating Users](/zia/provisioning-and-authenticating-users)
- [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-and-authentication-methods)
Of the available methods, Zscaler recommends you use SAML for authentication and SCIM for provisioning. To learn more, see:
- [Understanding SAML](/zia/understanding-saml)
- [Configuring SAML](/zia/configuring-saml)
- [About SCIM](/zia/about-scim)
- [Configuring SCIM](/zia/configuring-scim)
[]Zscaler recommends that organizations forward all internet traffic (traffic for all protocols and destined for all ports) to the Zscaler service so they can secure your internet traffic and apply policies accordingly.
Before you begin traffic forwarding, see:
- [Choosing Traffic Forwarding Methods](/zia/choosing-traffic-forwarding-methods)
- [Best Practices for Traffic Forwarding](/zia/best-practices-traffic-forwarding)
- [Determining Optimal MTU for GRE or IPSec Tunnels](/zia/determining-the-optimal-mtu-for-gre-or-ipsec-tunnels) (if you are using GRE or IPSec tunnels)
There are four preferred ways to forward your traffic:
- [GRE](#gre)
- [IPSec](#ipsec)
- [Zscaler Client Connector](#zapp)
- [PAC Files](#pac)
[]A Generic Routing Encapsulation (GRE) tunnel is ideal for forwarding internet-bound traffic from your corporate network to the Zscaler service. To learn more, see:
- [Understanding Generic Routing Encapsulation (GRE)](/zia/understanding-generic-routing-encapsulation-gre)
- [Configuring GRE Tunnels](/zia/configuring-gre-tunnels)
Configuring locations is a requirement for GRE tunnels. To learn more, see [Step 4](/zia/step-step-configuration-guide-zia#location) in this article.
[]Internet Protocol Security (IPSec) is a suite of protocols that provide network-layer security to a Virtual Private Network (VPN). To learn more, see:
- [Understanding IPSec VPNs](/zia/understanding-ipsec-vpns)
- [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel)
[]By using the Zscaler Client Connector, users can get all the benefits of the Zscaler service for internet traffic, as well as granular, policy-based access to internal resources from a single point. To learn more, see:
- [What is the Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
- [Step-by-Step Configuration Guide for Zscaler Client Connector](/zscaler-client-connector/step-step-configuration-guide-zscaler-client-connector)
[]A proxy autoconfiguration (PAC) file is a text file that instructs a browser to forward traffic to a proxy server, instead of directly to the destination server.
When using PAC files to forward traffic to the Zscaler service, Zscaler recommends that organizations use them in combination with tunneling, Surrogate IP, and the Zscaler Client Connector.
To learn more, see:
- [Understanding PAC Files](/zia/understanding-pac-file)
- [Best Practices for Writing PAC Files](/zia/best-practices-writing-pac-files)
- [Writing a PAC File](/zia/writing-pac-file)
Private Service Edges and Virtual Service Edges
Sometimes, forwarding your traffic to public [ZIA ](/zia/about-zscaler-enforcement-nodes)Public Service Edges is not the right choice for some portions of your organization. If this is the case, you can choose to instead forward it to ZIA Private Service Edges or Virtual Service Edges. To learn more, see:
- [Choosing Between Private Service Edges and Virtual Service Edge](/zia/choosing-between-private-service-edge-and-virtual-service-edge)
- [Understanding Private Service Edges](/zia/understanding-private-service-edge)
- [About Virtual Service Edge](/zia/about-virtual-service-edge)
[]Locations identify the various networks from which your organization sends its internet traffic. To learn more, see:
- [About Locations](/zia/about-locations)
- [Configuring Locations](/zia/configuring-locations)
- [Understanding Sublocations](/zia/understanding-sublocations)
- [Configuring Sublocations](/zia/configuring-sublocations)
[]Creating your policies gives you granular control over how users interact with content.
Before configuring your policies, see:
- [About Policy Enforcement](/zia/about-policy-enforcement)
- [Ranges & Limitations](/zia/ranges-limitations)
- [Saving and Activating Changes in the ZIA Admin Portal](/zia/saving-and-activating-changes-admin-portal)
- [About Backup and Restore](/zia/about-backup-and-restore)
To learn more about the different types of policies you can configure, see [Policies](/zia/documentation-knowledgebase/policies).
[]The Zscaler service provides real-time log consolidation across the globe, so you can view every transaction performed by your users regardless of where they are in the world. It also presents a wide range of standard reports, based on your organization's subscription, and provides the ability to create up to 500 custom reports. To learn more, see:
- [About Dashboards](/zia/about-dashboards)
- [About Insights](/zia/about-insights)
- [About Insights Logs](/zia/about-insights-logs)
- [Reports](/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports)
You can also utilize the Nanolog Streaming Service (NSS). This uses a virtual machine (VM) to stream traffic logs in real-time from the Zscaler NSS to your security information and event management (SIEM) system, such as Splunk or ArcSight, enabling real-time alerting, correlation with the logs of your other devices, and long-term local log archival. To learn more, see [About Nanolog Streaming Service (NSS)](/zia/about-nanolog-streaming-service).