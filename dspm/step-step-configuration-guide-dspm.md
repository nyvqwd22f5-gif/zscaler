# Step-by-Step Configuration Guide for DSPM
Source: https://help.zscaler.com/dspm/step-step-configuration-guide-dspm
PDF: https://help.zscaler.com/pdf/com/en/1474186.pdf

This guide explains the configuration steps that you need to complete to begin using Data Security Posture Management (DSPM) for your organization.
Before you begin configuring DSPM, Zscaler recommends reading the following articles:
- [What is DSPM?](/dspm/what-dspm)
- [Accepting the End User Subscription Agreement (EUSA)](/dspm/accessing-and-navigating-dspm-admin-portal#dspm-eusa)
- [Using the Zscaler Help Browser](/dspm/using-zscaler-help-browser)
Configuring DSPM
To configure DSPM, complete the following steps:
- [Step 1: Log In to the DSPM Admin Portal](#login1)
- [Step 2: Set up the DLP Engines and Define Sensitive Data](#dlp)
- [Step 3: Onboard Cloud Accounts](#onboardca)
- [Step 4: Configure Scan Settings](#scansettings)
- [Step 5: Configure Users](#usersroles)
- [Step 6: Configure Business Units](#bu)
- [Step 7: Configure the Data Posture Policies](#policies)
- [Step 8: Configure Alert Rules](#alerts)
- [Step 9: Configure 3rd-Party Integrations and Notifications](#thirdparty)
- [Step 10: Configure SSO Authentication (Optional)](#configuressoauthentication)
[]After your organization is provisioned for DSPM, you receive an email to complete the registration. DSPM is enabled with ZIdentity as the identity and authentication service. You need to log in to your ZIdentity account to single sign-on to DSPM. To learn more, see [Accessing and Navigating the DSPM Admin Portal](/dspm/accessing-and-navigating-dspm-admin-portal).
![The DSPM login page](/downloads/dspm/getting-started/step-step-configuration-guide-dspm/dspm-zidentity-ssopage.png)
[]DSPM uses predefined DLP engines and dictionaries that are synced from Zscaler Internet Access (ZIA) to classify data types. To learn more, see [Understanding DLP Engines and Dictionaries](/dspm/understanding-dlp-engines-and-dictionaries).
[]You can onboard the Amazon Web Services (AWS) organizations, Microsoft Azure tenants, or Google Cloud Platform (GCP) organizations into DSPM. When onboarded, DSPM monitors the data in your cloud accounts for any vulnerabilities and threats and provides comprehensive reports of your data's security posture. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
[]After you have onboarded the cloud accounts, you need to configure the scan settings. DSPM scans the resources (data stores, cloud storage, virtual machines, etc.) in your onboarded cloud accounts, classifies the data, detects vulnerabilities, and generates alerts so you can evaluate the issue and take necessary action. To learn more, see [About Scan Settings](/dspm/about-scan-settings).
[]You need to add users and user groups and assign roles in the ZIdentity Admin Portal to control their level of access to specific modules in the DSPM Admin Portal. To learn more, see [About Users](/zidentity/about-users).
[]You can onboard your cloud accounts and map them to business units. You can restrict user access to specific business units. For example, you might want to restrict a group to Amazon Web Services (AWS) accounts or restrict partners to view resources only in a specific account. To learn more, see [About Business Units](/dspm/about-business-units).
[]DSPM offers predefined data posture policies to meet your organization's compliance requirements across multiple cloud service providers (CSPs). You can also create custom policies. To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies).
[]You can configure and manage alert rules and notifications, so individuals in your organization can receive notifications for any security policy violations that occur in your cloud resources. To learn more, see [About Alerts](/dspm/about-alerts).
[]DSPM offers incident management by integrating with IT Service Management (ITSM) tools and cloud storage services. You can send alert data to these tools for further investigation and remediation. To learn more, see [About Third-Party Integrations](/dspm/about-third-party-integrations).
[]Configure SSO authentication with external IdPs in the ZIdentity Admin Portal to authenticate users to access DSPM. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).