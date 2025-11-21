# Step-by-Step Configuration Guide for Zscaler ITDR
Source: https://help.zscaler.com/itdr/step-step-configuration-guide-zscaler-itdr
PDF: https://help.zscaler.com/pdf/com/en/1531721.pdf

This guide takes you through the configuration steps that you need to complete to begin using Zscaler ITDR for your organization.
Before you begin configuring ITDR, Zscaler recommends reading the [What Is Zscaler ITDR?](/itdr/what-zscaler-itdr) article.
Configuring ITDR
To configure ITDR, complete the following steps:
- [Step 1: Log In to the Zscaler ITDR Admin Portal](#step-by-step-login)
- [Step 2: Configure Users & Roles](#configure-users)
- [Step 3: Configure Single Sign-On Authentication](#single-sign-on)
- [Step 4: Configure Threat Detection Policies](#endpoint-policies)
- [Step 5: Integrate ITDR with Okta](#okta-integration)
- [Step 6: Assess your Active Directory](#assess-ad)
- [Step 7: Set up Endpoint Credential Exposure Scan](#endpoint-credential-exposure)
- [Step 8: Analyze the Assessment Report](#view-scan-results)
- [Step 9: Enable Change Detection](#enabling-change-detection)
[]After your organization is provisioned for ITDR, you will receive an email with the following details:
- Link to your ITDR instance
- Link to set your password
- Security code
Click the password link to set your password and the two-factor authentication (2FA) code. To learn more, see [Accessing and Navigating the Zscaler ITDR Admin Portal](/itdr/accessing-and-navigating-zscaler-itdr-admin-portal).
[]Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to add users and roles. Contact Zscaler Support to subscribe to ZIdentity.
You can provision users who can access the ITDR Admin Portal. Users can access and manage different modules in the portal based on the roles assigned to them. To learn more, see [About Users & Roles](/itdr/about-users-roles).
[]Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to [configure primary and secondary external identity providers (IdPs)](/zidentity/configuring-okta-external-idp). ZIdentity supports both SAML and OpenID configurations.
You can enable single sign-on (SSO) to your ITDR Admin Portal via SAML or OpenID. To learn more, see the following articles:
- [About Identity Providers for Single Sign-On](/itdr/about-identity-providers-single-sign-on)
- [Configuring SAML for Single Sign-On](/itdr/configuring-saml-single-sign-on)
- [Configuring SAML for Okta Single Sign-On](/itdr/configuring-saml-okta-single-sign-on)
- [Configuring SAML for Microsoft Entra ID Single Sign-On](/itdr/configuring-saml-microsoft-entra-id-single-sign-on)
- [Configuring SAML for Active Directory Federation Services](/itdr/configuring-saml-active-directory-federation-services)
- [Configuring OpenID for Single Sign-On](/itdr/configuring-openid-single-sign)
- [Configuring OpenID for Single Sign-On Using Okta](/itdr/configuring-openid-single-sign-using-okta)
- [Configuring OpenID for Single Sign-On Using Google](/itdr/configuring-openid-single-sign-using-google)
[]You can add an Active Directory (AD) domain and assign an endpoint agent to scan the AD domain for identity misconfigurations and vulnerabilities. To learn more, see the following articles:
- [About Scan Agents](/itdr/about-scan-agents)
- [Scanning an Active Directory](/itdr/scanning-active-directory)
- [Triggering an On-Demand Scan](/itdr/triggering-demand-scan)
[]You can view and analyze the scan results of an AD domain and credential exposure on the Identity Posture and Endpoint Credential Exposure dashboards respectively. You can also view additional details about each issue, affected user, or affected computer to further investigate and remediate the issue. To learn more, see the following articles:
- [Identity Posture Dashboard](#identity-posture)
- [Endpoint Credential Exposure Dashboard](#exposure)
[]You can monitor and detect active changes in the AD domain and classify these changes as a good or bad impact. To learn more, see the following articles:
- [About Active Directory Change Detection](/itdr/about-itdr-change-detection)
- [Adding a Change Detection Issue to the Safelist](/itdr/adding-change-detection-issue-safelist)
- [Viewing and Managing the Change Detection Issue Safelist](/itdr/viewing-and-managing-change-detection-safelist)
[]You can create a threat detection policy and specify a selection criterion to apply to an endpoint for real-time threat detection. To learn more, see the following articles:
- [About Threat Detection Policies](/itdr/about-threat-detection)
- [Creating Threat Detection Policies](/itdr/creating-endpoint-policy)
- [Configuring an Endpoint Policy with ITDR - AD Detectors](/itdr/configuring-itdr-active-directory)
[]You can set up a credential exposure scan to scan the endpoints to identify credential exposure issues and disrupt lateral movements. To learn more, see the following articles:
- [About Endpoint Credential Exposure Scan](/itdr/about-endpoint-credential-exposure-scan)
- [Configuring an Endpoint Credential Exposure Scan](/itdr/configuring-endpoint-credential-exposure-scan)
- [Triggering an On-Demand Credential Exposure Scan](/itdr/triggering-demand-credential-exposure-scan)
[]You can integrate ITDR with Okta to enrich the identity metadata, identify real-time changes, and perform actions on an Okta identity. To learn more, see the following articles:
- [Integrating ITDR with Okta](/itdr/integrating-itdr-okta)
- [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details)
- [][About the Identity Posture Dashboard](/itdr/about-identity-posture-dashboard)
- [Viewing the Zscaler ITDR Active Directory Assessment Posture Report](/itdr/viewing-itdr-active-directory-assessment-report)
- [Downloading the Zscaler ITDR Active Directory Assessment Posture Report](/itdr/downloading-itdr-active-directory-executive-report)
- [Viewing Focus Area Details](/itdr/viewing-focus-area-details)
- [Viewing Affected Active Directory User Account Details](/itdr/viewing-affected-active-directory-user-account-details)
- [Viewing Affected Active Directory Computer Details](/itdr/viewing-affect-active-directory-computer-details)
- [][About the Endpoint Credential Exposure Dashboard](/itdr/about-endpoint-credential-exposure-dashboard)
- [Viewing Endpoint Credential Exposure Issues](/itdr/viewing-endpoint-credential-exposure-issues)