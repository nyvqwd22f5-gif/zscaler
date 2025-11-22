# Step-by-Step Configuration Guide for ZDX
Source: https://help.zscaler.com/zdx/step-step-configuration-guide-zdx
PDF: https://help.zscaler.com/pdf/com/en/1355756.pdf

This guide provides the configuration steps needed to begin using Zscaler Digital Experience (ZDX) for your organization.
Before you begin configuring ZDX, Zscaler recommends reading the articles:
- [What Is Zscaler Digital Experience?](/zdx/about-zscaler-digital-experience)
- [Accessing and Navigating the ZDX Admin Portal](/zdx/accessing-and-navigating-zdx-admin-portal), including:
- [Monitoring the Performance Dashboard](/zdx/monitoring-performance-dashboard)
- [Monitoring the Users Overview](/zdx/monitoring-users-overview)
- [Monitoring the Applications Overview](/zdx/monitoring-applications-overview)
- [Ranges & Limitations](/zdx/ranges-limitations)
- [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility)
Configuring ZDX
To configure ZDX, complete the steps:
- [Step 1: Configure Authentication and Provisioning Settings in ZIA](#ConfigAuthProvZIA)
- [Step 2: Configure Role-Based Administration](#Configure-Role-Based-Administration)
- [Step 3: Allowlist Domains on Zscaler cloud](#AllowlistDomains)
- [Step 4: Configure Zscaler Client Connector for ZDX](#ConfigureZApp)
- [Step 5: Configure an Application](#AddApp)
- [Step 6: Configure a Probe](#AddProbe)
- [Step 7: Configure Alerting](#ConfigureAlerting)
- [Step 8: Configure Diagnostics](#ConfigureDiagnostics)
[]To configure ZDX, have users, authentication, and provisioning set up for your organization in Zscaler Internet Access (ZIA). To configure these settings in ZIA, see [About Provisioning and Authenticating Users](/zia/about-provisioning-authenticating-users) and [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-authentication-methods). If you cannot configure these settings in ZIA, contact Zscaler Support.
[]To create admin users and roles in the ZDX Admin Portal, complete the steps to set up role-based administration. To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration) and [First Time Provisioning for ZDX Admins](/zdx/first-time-provisioning-zdx-admins).
[]Each cloud requires a list of domains to be placed on the allowlist for your organization to configure ZDX. To learn more, see [Allowlist Domains for ZDX](/zdx/allowlist-domains-zdx).
[]To configure ZDX, you must first deploy Zscaler Client Connector. Minimum versions of Zscaler Client Connector and ZDX Module are required. To configure Zscaler Client Connector for your organization, see [What is the Zscaler Client Connector?](/z-app/what-zscaler-app), [Step-by-Step Configuration Guide for Zscaler Client Connector](/z-app/step-step-configuration-guide-zscaler-app), and [Supported Versions & Feature Compatibility](/zdx/feature-version-compatibilities).
After you configure Zscaler Client Connector for your organization, you can also enable ZDX for a select group of users. To learn more, see [Selective Entitlement: Enabling ZDX for a Group of Users](/z-app/selective-entitlement-enabling-zdx-group-users).
[]Configure the SaaS web-based applications on your network that you want to probe via ZDX. To add and configure applications, see the following articles:
- [About Applications](/zdx/about-applications)
- [Adding a Custom Application](/zdx/adding-custom-application)
- [Configuring a Predefined Application](/zdx/configuring-predefined-application)
- [Editing an Application](/zdx/editing-application)
[]Configure the probes for the SaaS Web-based applications. To configure probes, see the following articles:
- [About Probes](/zdx/about-probes)
- [Configuring a Probe](/zdx/configuring-probe)
- [Editing a Probe](/zdx/editing-probe)
[]Configure rules to trigger alerts when a preset threshold is reached. To learn more, see the following articles:
- [About Alerts](/zdx/about-alerts)
- [About Rules](/zdx/about-rules)
- [Configuring an Alert Rule](/zdx/configuring-alert-rule)
- [Editing an Alert Rule](/zdx/editing-alert-rule)
- [Triggering an Alert](/zdx/triggering-alert)
- [Configuring Webhooks](/zdx/configuring-webhooks)
- [Understanding the Alert Email](/zdx/understanding-alerts-email)
[]Start a Diagnostics session to analyze any issues that users might be facing. To learn more, see following the articles:
- [About Diagnostics](/zdx/about-diagnostics)
- [Starting a Diagnostics Session](/zdx/starting-new-diagnostics-session)
- [Viewing Diagnostics Session Results](/zdx/viewing-diagnostics-session-results)