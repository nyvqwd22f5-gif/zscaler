# Upgrading to Zscaler Experience Center
Source: https://help.zscaler.com/unified/upgrading-zscaler-experience-center
PDF: https://help.zscaler.com/pdf/com/en/1508581.pdf

[Watch a video about Zscaler Experience Center.](https://fast.wistia.net/embed/iframe/mnoj1tyik0)
Zscaler Experience Center aims to simplify Zero Trust adoption and operations by providing an intuitive interface for all administrative users.
Key Benefits
Experience Center has the following key benefits:
- Simplicity in Zero Trust Implementation: Experience Center offers a guided workflow for onboarding users and configuring security policies, making it easier for organizations to start their Zero Trust journey.
- Enhanced Management: Boost user experience and cybersecurity efficiency with advanced management. Experience Center brings together management for Internet & SaaS applications, Private Applications, Digital Experience Monitoring (DEM), and Endpoint Agents.
- Unifed Analytics and AI Integration: The new interface delivers a cohesive and dynamic experience, featuring an intuitive layout that facilitates persona-focused unified analytics views, as well as interactive experiences powered by a generative AI copilot.
Migration and Upgrade Processes
The following processes detail how to migrate and upgrade to Experience Center.
Prerequisites
- You must have administrative users (i.e., admins) who have already migrated to ZIdentity for a centralized identity experience to access Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX), and Zscaler Client Connector Admin Portals. To learn more, see [Migrating Zscaler Service Admins to ZIdentity](/zidentity/migrating-zscaler-service-admins-zidentity).
- Admins do not need to take any further action in order to upgrade to Experience Center. Upon receiving the migration notification, admins can log in to Experience Center ([https://console.zscaler.com](https://console.zscaler.com)) using their existing ZIdentity authentication credentials.
Experience Center requires migration for admin users only. To learn more, see [Migrating Zscaler Service Admins to ZIdentity](/zidentity/migrating-zscaler-service-admins-zidentity). There is no need for ZIdentity end user migration.
Accessing Experience Center after Migration
Zscaler has simplified the login process by learning the admin's identity and redirecting them to their respective tenant. Irrespective of the Zscaler cloud that the tenant belongs to, the login URL is [https://console.zscaler.com](https://console.zscaler.com) for the production cloud and [https://beta.console.zscaler.com](https://beta.console.zscaler.com) for the beta cloud. All existing configurations are retained and can be managed via the new Experience Center UI.
Alternatively, you can access Experience Center through the banner displayed on the ZIdentity Admin Portal.
![ZIdentity Admin Portal displaying banner at top of page.](/downloads/unified/getting-started-zscaler/upgrading-zscaler-experience-center/unified-zid-adminportal-banner.png)
Key Features
All of your existing configurations, reports, and dashboards are available on Experience Center. In addition, Experience Center offers the following:
- Unified analytics make it a breeze to navigate across consolidated views, from users to cyber and data protection, ensuring admins and IT leaders can quickly get a snapshot of events across their organization.
- Streamlined onboarding workflow for new tenants to add users, distribute the Zscaler Client Connector app, and secure traffic by enabling policies that are recommended by Zscaler as a best practice.
Accessing Standalone Portals
Access to the current standalone portals (i.e., Admin Portals) will continue to be supported at this time. All portals can be accessed via ZIdentity.