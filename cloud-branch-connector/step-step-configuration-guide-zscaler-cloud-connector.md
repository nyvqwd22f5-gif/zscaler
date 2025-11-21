# Step-by-Step Configuration Guide for Zscaler Cloud Connector
Source: https://help.zscaler.com/cloud-branch-connector/step-step-configuration-guide-zscaler-cloud-connector
PDF: https://help.zscaler.com/pdf/com/en/1420756.pdf

This guide takes you through the configuration steps you need to complete before using Zscaler Cloud Connector for your organization.
Before you begin configuring Cloud Connector, Zscaler recommends reading the following articles:
- [What Is Zscaler Cloud Connector?](/cloud-branch-connector/what-zscaler-cloud-connector)
- [Accessing and Navigating the the Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal)
- [Using the Zscaler Help Browser](/cloud-branch-connector/using-zscaler-help-browser)
Configuring Cloud Connector
To configure Cloud Connector, complete the following steps:
- [Step 1: Update Administrator and Role Management Information](#admin)
- [Step 2: Configure Your Provisioning Template](#provisioning)
- [Step 3: Configure Your Locations](#locations)
- [Step 4: Deploy Your Cloud Connector Virtual Machine (VM)](#deploy-cloud-connector-vm)
- [Step 5: Configure Your Firewall Filtering](#firewall-filtering)
- [Step 6: Configure Your Gateways](#gateways)
- [Step 7: Configure Your Forwarding Methods](#forwarding-methods)
- [Step 8: Configure Your Analytics](#analytics)
[]To update and configure administrators and roles as applicable, see:
- [Accessing Administrator Management](/cloud-branch-connector/accessing-administrator-management)
- [About Administrators](/cloud-branch-connector/about-administrators)
- [Adding Admins](/cloud-branch-connector/adding-admins)
- [About Role Management](/cloud-branch-connector/about-role-management)
- [Adding Admin Roles](/cloud-branch-connector/adding-admin-roles)
[]Locations identify the various networks from which your organization sends its internet traffic. To learn more, see:
- [About Locations](/cloud-branch-connector/about-locations)
- [About Location Templates](/cloud-branch-connector/about-location-templates)
- [Configuring a Location Template](/cloud-branch-connector/configuring-location-template)
[]Provisioning templates create provisioning URLs to deploy your Cloud Connector as a virtual machine (VM). To learn more, see:
- [About Cloud Provisioning Templates](/cloud-branch-connector/about-cloud-provisioning-templates)
- [Configuring a Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template)
[]To deploy your Cloud Connector VM, see:
- [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector)
- [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services)
- [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure)
- [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform)
[]Firewall filtering policies are comprised of source IP groups, destination IP groups, IP pools, and network services. To learn more, see:
- [About Source IP Groups](/cloud-branch-connector/about-source-ip-groups)
- [Configuring Source IP Groups](/cloud-branch-connector/configuring-source-ip-groups)
- [About Destination IP Groups](/cloud-branch-connector/about-destination-ip-groups)
- [Configuring Destination IP Groups](/cloud-branch-connector/configuring-destination-ip-groups)
- [About IP Pool](/cloud-branch-connector/about-ip-pool)
- [Configuring IP Pool](/cloud-branch-connector/configuring-ip-pool)
- [About Network Services](/cloud-branch-connector/about-network-services)
- [Configuring Network Services](/cloud-branch-connector/configuring-network-services)
- [About Network Service Groups](/cloud-branch-connector/about-network-service-groups)
- [Configuring Network Service Groups](/cloud-branch-connector/configuring-network-service-groups)
[]Gateway forwarding methods allow you to control and forward traffic. To learn more, see:
- [About Zscaler Internet Access Gateways](/cloud-branch-connector/about-zia-gateways)
- [Configuring a ZIA Gateway](/cloud-branch-connector/configuring-zia-gateway)
- [About Log and Control Gateways](/cloud-branch-connector/about-log-and-control-gateways)
- [Configuring a Log and Control Gateway](/cloud-branch-connector/configuring-log-and-control-gateway)
[]Forwarding allows you to set up traffic forwarding, log and control forwarding, and DNS control rules. To learn more, see:
- [About Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding)
- [Configuring Traffic Forwarding Rules](/cloud-branch-connector/configuring-traffic-forwarding-rule)
- [About Log and Control Forwarding](/cloud-branch-connector/about-log-and-control-forwarding)
- [Configuring Log and Control Forwarding Rule](/cloud-branch-connector/configuring-log-and-control-forwarding-rule)
- [About DNS Policies](/cloud-branch-connector/about-dns-policies)
- [Configuring the DNS Filtering Rule](/cloud-branch-connector/configuring-dns-filtering-rule)
[]The Zscaler service provides real-time log consolidation across the globe, so you can view every transaction performed by your users regardless of where they are in the world. It also presents the deployment status, activity status, and geographical view of your deployed Cloud Connector. To learn more, see:
- [Accessing Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring)
- [About Insights](/cloud-branch-connector/about-insights)
- [About Insights Logs](/cloud-branch-connector/about-insights-logs)