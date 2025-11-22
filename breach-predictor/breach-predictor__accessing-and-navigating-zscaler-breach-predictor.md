# Accessing and Navigating Zscaler Breach Predictor
Source: https://help.zscaler.com/breach-predictor/accessing-and-navigating-zscaler-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1500441.pdf

This article covers the following topics:
- [Completing Prerequisite Tasks](#completing-prereqs)
- [Accessing the Zscaler Breach Predictor Portal](#accessing-breach-predictor)
- [Navigating the Breach Predictor UI](#navigating-breach-predictor-ui)
- [Understanding Maintenance and Upgrades](#maintenance-and-upgrades)
To learn more about how to use Breach Predictor, see [Using Zscaler Breach Predictor](/breach-predictor/using-zscaler-breach-predictor).
[]
- License Breach Predictor: Zscaler Breach Predictor is a standalone product that is licensed separately from other parts of the Zscaler ecosystem. To learn more about getting Breach Predictor for your organization, contact your Zscaler Account team.
- [Configure Zscaler Internet Access (ZIA)](/zia/step-step-configuration-guide-zia): To ensure that Zscaler Internet Access (ZIA) logs are available for Breach Predictor, ZIA must be fully configured for your organization. If your organization already uses ZIA, no extra configuration is required for Breach Predictor to access ZIA logs.
- [Integrate with third-party applications](/breach-predictor/integrating-applications-zscaler-breach-predictor): Breach Predictor lets you expand functionality by integrating with multiple third-party applications. For example, you can integrate with Zscaler Sandbox for log data, with Splunk and CrowdStrike Next-Gen SIEM to send event data to your SIEM, or with Jira and ServiceNow to log tickets for policy changes.
[]
- [Sign in to the ZIdentity Landing Page.](#access-zidentity-landing)
-
Click the **Breach Predictor** tile to access the Breach Predictor Portal.
[See image.](#zidentity-landing-page-image)
You are redirected to the Breach Predictor Portal.
[]
Based on your organization's [authentication preference](/zidentity/configuring-authentication-methods), sign in to the ZIdentity Landing Page using one of the following methods:
- [Password](#password)
- [Email One-Time Password (OTP)](#email-otp)
- [Security Key or Biometric](#security-key-biometric)
-
[]Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
[See image.](#login-page)
- Click** Next**.
-
Enter your **Password **and click **Sign In**.
[See image.](#Password-auth)
-
Based on your organization's MFA policy, two-factor authentication (2FA) is required. Complete your 2FA to access the ZIdentity Landing Page.
If you forget your password or want to configure a different secondary authenticator, click **Having trouble signing in? **> **Reset Password **or** Reset Second Factor**, and a reset email is sent to your email ID. The reset link within the email expires after 15 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
If your account is configured with MFA, you can sign in using an email OTP as well:
- []Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
-
Click** Next** and then, click **Other Sign-in Options**.
[See image.](#email-otp1)
The **Sign-in Options** window appears.
-
In the **Sign-in Options** window, click **Email OTP**.
[See image.](#email-otp2)
-
Enter the OTP sent to your email address and click **Sign In**. The OTP expires after 15 minutes. If the OTP expires or you don't receive an OTP, click **Resend **to receive another OTP after 60 seconds.
[See image.](#email-otp3)
- []Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
-
Select **Sign-in using Security Key or Biometric**.
[See image.](#security-key)
- Click** Next**.
-
Based on your configuration, enter your security key or complete the biometric to access the ZIdentity Landing Page.
If you want to configure with a different security key or biometric, click **Having trouble signing in? **> **Reset Security Key or Biometric**, and a reset email is sent to your email ID. The reset link within the email expires after 15 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
[]![ZIdentity Login screen with blurred Login ID and Remember Me option selected..](/downloads/zidentity/zid-login-pagenew.png)
[]![A screenshot with blurred login ID and displaying password field.](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/Zid-PasswordAuth.png)
[]![A screenshot with blurred login ID, displaying password field and highlighted Other Sign-in Options.](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-other-sign-in-option.png)
[]![Sign-in options screen with blurred login ID and highlighted email otp option. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-email-otp-sign-in.png)
[]![Login using Email Code window with blurred login ID and displaying placeholder to enter OTP. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-email-otp-MFA1.png)
[]![ZIdentity Login screen with blurred login ID and selected Remember Me  and Sign-in using Security Key or Biometric options. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-securitykey-mfa.png)
[]![The ZIdentity Landing Page with the Breach Predictor Tile](/downloads/breach-predictor/getting-started/accessing-and-navigating-zscaler-breach-predictor/ZBP-ZIdentity_BreachPredictorTile.png)
[]From the left-side navigation, you can access the following areas of Breach Predictor:
- [Dashboard](#dashboard)
- [Findings](#findings)
- [Users](#users)
- [Events](#events)
- [Threat Landscape](#threat-landscape)
- [Profile](#profile)
- [Tickets](#tickets)
- [Theme](#theme)
[]From the **Dashboard**, you can use various charts and tables to better understand your Overall Breach Probability score and to assess your organization’s placement within the MITRE ATT&CK  framework during a specified period.
To learn more, see [About the Dashboard](/breach-predictor/about-dashboard).
[]The **Findings** page provides an overview of the threats that are affecting your organization as a whole. You can see user data by threat stage, department, threat type, and region. You can also drill down to see information about activity by individual users.
To learn more, see [About Users](/breach-predictor/about-users).
[]On the **User Threat Profile** page, you can view prioritized data across the MITRE ATT&CK  matrix presented in the different tables. As you work with Findings data, you should always work from right to left in the MITRE ATT&CK  matrix; as a threat moves further to the right in the matrix, your organization is at a higher risk of a data breach.
To learn more, see [About Findings](/breach-predictor/about-findings).
[]The **Events** page provides a view across time of all tracked events in your organization. On the **Events** page, you can use a number of filters (e.g., time frame, threat family, and user) to get a more granular view of the events affecting your organization.
To learn more, see [About Events](/breach-predictor/about-events).
[]The **Threat Landscape** page provides an overview of the biggest current security threats according to Zscaler ThreatLabz, the security research arm of Zscaler.
To learn more, see [About the Threat Landscape](/breach-predictor/about-threat-landscape).
[]Click **Profile** to see basic information about your username, your license, the Zscaler cloud to which Breach Predictor is connected, and the organization ID for your organization's instance of Zscaler Internet Access (ZIA). Additionally, you can see the various integrations available in your organization (e.g., Jira, CrowdStrike Next-Gen SIEM, and Splunk). You can also log out of Breach Predictor.
To learn more, see [About Profiles](/breach-predictor/about-profiles).
[]To specify the UI theme (i.e., dark mode or light mode), click the **Theme** toggle.
[]Because Breach Predictor doesn’t require configuration for new data visibility (e.g., new logs, data sources, etc.), your organization automatically benefits from added functionality. You can stay up to date with Breach Predictor enhancements by tracking [release notes updates](/breach-predictor/release-notes).
[]The **Tickets** page lets you view the Jira and ServiceNow tickets that have been created for your organization. The tickets you create are grouped into two categories: Request tickets and Support tickets. Request tickets are created based on the policy recommendations that Breach Predictor provides. Support tickets are created for other improvements that do not involve policy updates.
To learn more, see [About Tickets](/breach-predictor/about-tickets).