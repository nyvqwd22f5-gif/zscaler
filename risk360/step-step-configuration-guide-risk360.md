# Step-by-Step Configuration Guide for Risk360
Source: https://help.zscaler.com/risk360/step-step-configuration-guide-risk360
PDF: https://help.zscaler.com/pdf/com/en/1532608.pdf

This guide provides the configuration steps needed to begin using Risk360 Admin Portal for your organization.
Before you begin configuring Risk360, Zscaler recommends reading the following articles:
- [What Is Risk360?](/risk360/what-risk360)
- [Accessing and Navigating the Risk360 Admin Portal](/risk360/accessing-and-navigating-risk-360-admin-portal)
Configuring Risk360
To configure Risk360, complete the steps:
- [Step 1: Configure Role-Based Administration](#Configure-Role-Based-Administration)
- [Step 2: Configure Domains for External Attack Surface Analysis](#add-domains)
- [Step 3: Manage Peer Score and Financial Risk Settings](#settings)
- [Step 4: Configure Alerting](#ConfigureAlerting)
[]Using the super admin credentials provided to you for the Risk360 service, configure admin roles, users, and SAML for admins in the Risk360 Admin Portal. To learn more, see [Configuring Role-Based Administration](/risk360/configuring-role-based-administration-risk360) and [Configuring SAML for Admins](/risk360/configuring-saml-admins-risk360).
For ZIdentity-Enabled Tenants
If your organization is enabled with [ZIdentity](/zidentity/what-zidentity), you must assign ZIdentity users as Risk360 service admins:
- Add users in ZIdentity Admin Portal. To learn more, see [Adding Users](/zidentity/adding-users). Skip this step if the users are already configured in the ZIdentity Admin Portal.
- Assign users as Risk360 service admins. To learn more, see [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups).
You must be a global ZIdentity admin to view all available services for your organization for admin assignments. If you don't see the Risk360 service for admin assignment, reach out to your Zscaler Account team.
[]You can add domains to run frequent scans on them to detect vulnerabilities for external attack surfaces. To learn more, see [Adding a Domain for External Attack Surface Analysis](/risk360/adding-domain-external-attack-surface-analysis).
[]You can customize the parameters used to calculate your industry's peer risk score and your organization's financial exposure. To learn more, see [Managing Peer Score Settings](/risk360/managing-peer-score-settings) and [Managing Financial Risk Settings](/risk360/managing-financial-risk-settings).
[]Configure rules to trigger alerts when a preset threshold is reached. To learn more, see [Configure an Alert Rule](/risk360/configuring-alert-rule).