# Step-by-Step Configuration Guide for Isolation
Source: https://help.zscaler.com/isolation/step-step-configuration-guide-isolation
PDF: https://help.zscaler.com/pdf/com/en/1529970.pdf

This guide takes you step by step through the configuration tasks you must complete to begin using Isolation for your organization. The steps reflect the process for configuring Isolation for either Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA). To learn more, see [Understanding the ZIA Cloud Architecture](/zia/understanding-zscaler-cloud-architecture) and [What Is Zscaler Private Access (ZPA)?](/zpa/what-zscaler-private-access)
Before you begin using Isolation, Zscaler recommends reading the following articles:
- [What Is Isolation?](/isolation/what-is-isolation)
- [Ranges & Limitations](/isolation/ranges-limitations)
Prerequisites
- Access to a ZIA or a ZPA tenant.
- Subscription to the Isolation add-on.
- Supporting ZPA infrastructure (e.g., App Connector or Application Access).
- Identity provider (IdP) with conditional access capabilities (e.g., IP restrictions or context-aware policy).
Configuring Isolation
To configure Isolation, complete the following steps:
- [Step 1: Enable Isolation for Your Organization](#UpdateCompanyAdminInfo)
- [Step 2: Create Isolation Profiles](#ConfigureCertificates)
- [Step 3: Configure Policies for Isolation](#ConfigureZscalerApp)
[]Before you begin configuring Isolation, ensure that you have the access your organization needs:
- [Enable ZIA for your organization.](/zia/step-step-configuration-guide-zia)
- [Enable ZPA for your organization.](/zpa/step-step-configuration-guide-zpa)
- Contact Zscaler Support to get Isolation enabled for your organization.
[]Configure individual isolation profiles in your tenant for users:
- For ZIA isolation profiles:
- [Create a ZIA isolation profile.](/isolation/creating-isolation-profiles-zia) You can [edit your ZIA isolation profiles](/isolation/editing-your-isolation-profile-zia) at any time.
- Choose [banner themes for the isolation end user notification](/isolation/adding-banner-theme-isolation-end-user-notification-zia) that shows to each individual ZIA isolation profile.
- Choose the [root certificates](/isolation/about-root-certificates-isolation-zia) for each ZIA isolation profile.
- For ZPA isolation profiles:
- [Create a ZPA isolation profile.](/isolation/creating-isolation-profiles-zpa) You can [edit your ZPA isolation profiles](/isolation/editing-your-isolation-profile-zpa) at any time.
- Choose [banner themes for the isolation end user notification](/isolation/adding-banner-theme-isolation-end-user-notification-zpa) that shows to each individual ZPA isolation profile.
- Choose the [root certificates](/isolation/about-root-certificates-isolation-zpa) for each ZPA isolation profile.
[]Configure the policies to map to the isolation profiles:
- For ZIA policies:
- [Configure ZIA for Isolation](/isolation/configuring-zia-isolation).
- [Configure the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
- [Configure the Smart Browser Isolation Policy.](/zia/configuring-smart-browser-isolation-policy)
- [Configure Sandbox Integration with Isolation.](/isolation/using-sandbox-integration-isolation)
- For ZPA policies:
- [Learn about the Isolation Policy](/zpa/about-isolation-policy).
- [Configure Isolation Policies](/zpa/configuring-isolation-policies).
- [Configure the Access Policy for Isolation.](/zpa/configuring-access-policies)
- [Configure Secure SaaS Access from Unmanaged Devices via the User Portal.](/isolation/secure-saas-access-unmanaged-devices-user-portal)