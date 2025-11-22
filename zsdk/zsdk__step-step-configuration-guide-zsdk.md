# Step-by-Step Configuration Guide for ZSDK
Source: https://help.zscaler.com/zsdk/step-step-configuration-guide-zsdk
PDF: https://help.zscaler.com/pdf/com/en/1506946.pdf

This guide provides the configuration steps needed to begin using Zscaler SDK for Mobile Apps (ZSDK) for your organization.
Before you begin configuring ZSDK, Zscaler recommends reading the following articles:
- [What Is Zscaler SDK for Mobile Apps?](/zsdk/what-zscaler-sdk-mobile-apps)
- [Ranges & Limitations](/zsdk/ranges-limitations)
Configuring ZSDK
To configure ZSDK, complete the following steps:
- [Step 1: Register Your App](#RegisterApp)
- [Step 2: Configure a Token Validator](#Add-Token-Validator)
- [Step 3: Add App Connectors](#AddAppConnectors)
- [Step 4: Deploy App Connectors](#DeployAppConnectors)
- [Step 5: Define Application Segment](#DefineAppSegment)
- [Step 6: Add Access Policy](#AddAccessPolicy)
- [Step 7: Integrate ZSDK](#integrate)
[]To use ZSDK in your mobile app, you need to register your mobile app to obtain an app key. To learn more, see [Register Your App](/zsdk/register-your-app).
If you cannot register an app, contact Zscaler Support.
[]Configure a JSON Web Token validator to enable ZSDK to work with your user identity and management systems to provide strong authentication and authorization. To learn more, see [Managing Token Validators](/zsdk/managing-token-validators).
[]Add App Connectors to provide a secure, authenticated interface between your servers and the ZSDK cloud. To learn more, see [Managing App Connectors](/zsdk/managing-app-connectors).
[]
App Connector deployment consists of installing the App Connector and enrolling it to obtain the TLS client certificate to authenticate itself to the Zscaler cloud.
The deployment process differs depending on the platform used for the App Connector. Zscaler recommends that App Connectors be deployed in pairs to ensure continuous availability during software upgrades. To learn more, see the platform-specific deployment guides:
- [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites)
- [App Connector Deployment Guide for Amazon Web Services](/zpa/connector-deployment-guide-amazon-web-services)
- [App Connector Deployment Guide for Linux](/zpa/app-connector-deployment-guide-linux)
- [App Connector Deployment Guide for Docker](/zpa/app-connector-deployment-guide-docker)
- [App Connector Deployment Guide for Microsoft Azure](/zpa/connector-deployment-guide-microsoft-azure)
- [App Connector Deployment Guide for Microsoft Hyper-V](/zpa/connector-deployment-guide-microsoft-hyper-v)
- [App Connector Deployment Guide for Nutanix AHV](/zpa/app-connector-deployment-guide-nutanix-ahv)
- [App Connector Deployment Guide for VMware Platforms](/zpa/connector-deployment-guide-vmware-platforms)
- [Networking Deployed App Connectors](/zpa/networking-deployed-connectors)
- [Configuring a Split DNS Zone for App Connectors](/zpa/configuring-split-dns-zone-connectors)
- [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors)
[]You need to define an application segment for applications (e.g., back-end services, APIs) that you want to protect with ZSDK. An application is an FQDN, local domain name, or IP address that you define on a standard set of ports. To learn more, see [Defining and Managing Application Segments](/zsdk/defining-and-managing-application-segments).
[]By default, Zscaler blocks access to applications and segment groups for users until you configure policy rules that explicitly allow access. To learn more, see [Managing Access Policies](/zsdk/managing-access-policies).
[]After configuring your application in the ZSDK Admin Portal and deploying App Connectors, you need to integrate ZSDK before you can start securing your app's operations. Depending on your application type, read one of the ZSDK Integration Guides:
- [ZSDK Integration Guide for Android](/zsdk/zsdk-integration-guide-android)
- [ZSDK Integration Guide for iOS](/zsdk/zsdk-integration-guide-ios)