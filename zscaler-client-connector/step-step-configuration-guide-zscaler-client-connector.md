# Step-by-Step Configuration Guide for Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/step-step-configuration-guide-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1285406.pdf

This guide takes you step-by-step through the configuration tasks you must complete to begin using Zscaler Client Connector for your organization.
Before you begin configuring Zscaler Client Connector, Zscaler recommends reading the following articles:
- [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
- [About the Zscaler Client Connector Portal](/zscaler-client-connector/about-zscaler-app-portal)
- [Using Zscaler Client Connector](/zscaler-client-connector/using-zscaler-client-connector)
- [Zscaler Client Connector Processes to Allowlist](/zscaler-client-connector/zscaler-client-connector-processes-allowlist)
Configuring Zscaler Client Connector
To configure Zscaler Client Connector, complete the following steps:
- [Step 1: Complete System Requirements and Prerequisite Tasks](#step-1)
- [Step 2: Configure Your Administration Settings](#step-2)
- [Step 3: Configure Your Zscaler Client Connector Profiles](#step-3)
- [Step 4: Download Zscaler Client Connector](#step-4)
- [Step 5: Customize Zscaler Client Connector with Installer Options](#step-5)
- [Step 6: Deploy Zscaler Client Connector](#step-6)
[]Before you begin configuring Zscaler Client Connector, complete the following system requirements and prerequisite tasks:
- [Windows Requirements](#windows-requirements)
- [macOS Requirements](#macOS-requirements)
- [Linux Requirements](#linux-requirements)
- [iOS Requirements](#iOS-requirements)
- [Android Requirements](#android-requirements)
- [Android on ChromeOS Requirements](#chrome-requirements)
- [ZIA Prerequisite Tasks](#zia-prereq-tasks-windows-macOS)
- [ZPA Prerequisite Tasks](#zpa-prereq-tasks-windows-macOS)
- [ZDX Prerequisite Tasks (Windows and macOS)](#zdx-prereq-tasks-windows-macOS)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for Windows, see [Supported Versions](/eos-eol/supported-versions).
- Disk usage: 200 MB
- Memory usage: 150 MB
- Processor capable of running operating systems supported by Zscaler Client Connector.
- Microsoft .NET Framework 4 and later.
- Supported languages: For a list of supported languages for localization, see [Localization Support](/zscaler-client-connector/localization-support).
- Allowlist Zscaler Client Connector processes and configure firewall bypasses.
While Zscaler has allowlist agreements for Zscaler Client Connector in place with specific endpoint protection vendors such as Trend Micro and Kaspersky Labs, for some endpoint protection products like anti-virus and personal firewall, you might need to perform additional allowlist to ensure full Zscaler Client Connector functionality. To learn more, see [Zscaler Client Connector Processes to Allowlist](/zscaler-client-connector/zscaler-client-connector-processes-allowlist).
- [Limitations and dependencies](#Windows-limitations)
[]For Windows, note the following:
- [Upgrading to Zscaler Client Connector 3.7 for Windows](/zscaler-client-connector/upgrading-zscaler-client-connector-3.7-windows)
- [Upgrading to Windows 10, Version 2004](/zscaler-client-connector/upgrading-windows-10-version-2004)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for macOS, see [Supported Versions](/eos-eol/supported-versions).
- Disk usage: 200 MB
- Memory usage: 150 MB
- Processor capable of running operating systems supported by Zscaler Client Connector.
- If you are using Tunnel mode in your [forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app), ensure that you disabled the system firewall.
- Supported languages: For a list of supported languages for localization, see [Localization Support](/zscaler-client-connector/localization-support).
- Allowlist Zscaler Client Connector processes and configure firewall bypasses.
While Zscaler has allowlist agreements for Zscaler Client Connector in place with specific endpoint protection vendors such as Trend Micro and Kaspersky Labs, for some endpoint protection products like anti-virus and personal firewall, you might need to perform additional allowlist to ensure full Zscaler Client Connector functionality. To learn more, see [Zscaler Client Connector Processes to Allowlist](/zscaler-client-connector/zscaler-client-connector-processes-allowlist).
- [Limitations and dependencies](#macOS-limitations)
[]For macOS, note the following:
- [Using Zscaler Client Connector with Cisco AnyConnect on macOS Catalina](/zscaler-client-connector/using-zscaler-client-connector-cisco-anyconnect-macos-catalina)
- [Upgrading to macOS Big Sur](/zscaler-client-connector/upgrading-macos-big-sur)
- [Upgrading to macOS Catalina](/zscaler-client-connector/upgrading-macos-catalina)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for Linux, see [Supported Versions](/eos-eol/supported-versions).
- Disk usage: 200 MB
- Memory usage: 150 MB
- x86-64 architecture processor capable of running operating systems supported by Zscaler Client Connector.
- [Limitations and dependencies](#Linux-limitations)
[]For Linux, note the following:
- [Resolving Auto-Update Issues for Zscaler Client Connector Linux 1.2](/zscaler-client-connector/resolving-auto-update-issues-zscaler-client-connector-linux-1.2)
- [Missing Zscaler Client Connector Gnome Tray icon for Linux](/zscaler-client-connector/missing-zscaler-client-connector-gnome-tray-icon)
- [Resolving Zscaler Client Connector Linux 1.2 DNS Configuration Issues for VPNs](/zscaler-client-connector/resolving-zscaler-client-connector-linux-1.2-dns-configuration-issues-vpns)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for iOS, see [Supported Versions](/eos-eol/supported-versions).
- Compatible with iPhone, iPad, and iPod touch.
- 20 MB required for installation and additional space for logs.
- [Limitations and dependencies](#iOS-limitations)
[]For iOS, note the following:
- [Using the Unauthorized Modification Device Posture Profile](/zscaler-client-connector/using-unauthorized-modification-device-posture-profile)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for Android, see [Supported Versions](/eos-eol/supported-versions).
- 21 MB required for installation and additional space for logs.
- [Limitations and dependencies](#Android-limitations)
[]For Android, note the following:
- [Upgrading to Zscaler Client Connector version 1.9 for Android](/zscaler-client-connector/upgrading-android-1.9)
- [Upgrading to Android 10](/zscaler-client-connector/upgrading-android-10)
- [Using the Unauthorized Modification Device Posture Profile](/zscaler-client-connector/using-unauthorized-modification-device-posture-profile)
- []Supported versions: For a list of supported Zscaler Client Connector versions and supported OS versions for Android on ChromeOS, see [Supported Versions](/eos-eol/supported-versions).
- 21 MB required for installation and additional space for logs.
- []Configure appropriate security and access settings in the ZIA Admin Portal.
- You must have one of the following for authentication:
- An authentication mechanism configured and users provisioned on the ZIA service.
- If you do not have an authentication mechanism installed, you must [use the Zscaler Client Connector Portal as your Identity Provider (IdP)](/zscaler-client-connector/using-zscaler-app-portal-identity-provider) to provision and authenticate users.
- Configure your organization's firewall to allow the necessary connections. For detailed information about the traffic your firewall must allow, go to config.zscaler.com/<Zscaler Cloud Name>/zscaler-app. For example, if your cloud name is zscalertwo.net, you would go to config.zscaler.com/zscalertwo.net/zscaler-app. To learn more, see [What Is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- (Optional) Enable SSL inspection for users running Zscaler Client Connector. To learn more, see [Configuring SSL Inspection for Zscaler Client Connector](/zscaler-client-connector/configuring-ssl-inspection-zscaler-app).
To learn more, see [Deploying and Managing Zscaler Client Connector for ZIA](/zia/deploying-managing-zscaler-client-connector-zia).
- []Configure appropriate security and access settings in the ZPA Admin Portal.
- SAML-based authentication must be configured and users provisioned. You cannot use the Zscaler Client Connector Portal as an IdP for the ZPA service.
- Ensure that Zscaler Client Connector properly processes traffic for ZPA. To learn more, see [Domains to Add to SSL Bypass List](/zscaler-client-connector/domains-add-ssl-bypass-list).
If you use a PAC file for Zscaler Client Connector, you must add the URLs to the SSL exemptions list on the proxy as well.
[]To ensure that Zscaler Client Connector properly monitors your users’ digital experience, ensure all destination domains are placed on the allowlist in your SSL bypass list. To learn more, see [Allowlist Domains for ZDX](/zdx/allowlist-domains-zdx).
[]To configure your administration settings for Zscaler Client Connector, see the following articles:
- [Configuring Acceptable Use Policy (AUP) for Zscaler Client Connector](/zscaler-client-connector/configuring-acceptable-use-policy-aup-zscaler-app)
- [Configuring Update Settings for Zscaler Client Connector](/zscaler-client-connector/configuring-update-settings-zscaler-app)
- [Configuring Forwarding Profiles for Zscaler Client Connector](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app)
- [Configuring User Access to Support & Logging for Zscaler Client Connector](/zscaler-client-connector/configuring-user-access-support-and-logging-zscaler-app)
- [Configuring Fail-Open Settings for Zscaler Client Connector](/zscaler-client-connector/configuring-fail-open-settings-zscaler-app)
- (Optional) If necessary, for ZIA, see [Using the Zscaler Client Connector Portal as an Identity Provider](/zscaler-client-connector/using-zscaler-app-portal-identity-provider).
- (Optional) If necessary, for ZPA, see [Configuring Device Posture for ZPA](/zscaler-client-connector/configuring-device-posture-profiles-zpa).
To learn more about other administration settings for Zscaler Client Connector, see [Policy & Administration Settings](/zscaler-client-connector/policy-administration-settings).
[]Zscaler Client Connector profiles control key settings and behaviors for Zscaler Client Connector. To configure Zscaler Client Connector profiles, see the following articles:
- [About Zscaler Client Connector Profiles](/zscaler-client-connector/about-zscaler-app-profiles)
- [Configuring Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-app-profiles)
To learn more, see [Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-policy-and-administration-settings/zscaler-app-profiles).
[]To download Zscaler Client Connector, see the following articles:
- [About the Zscaler Client Connector Store](/zscaler-client-connector/about-zscaler-app-store)
- [Downloading Zscaler Client Connector](/zscaler-client-connector/downloading-zscaler-app)
[]You can configure a Zscaler Client Connector installer file with installation options that allow you to remove steps from the user enrollment process (e.g., allowing users to skip the enrollment page or the cloud selection prompt on Zscaler Client Connector).
To learn more, see the following articles:
- [Customizing Zscaler Client Connector with Install Options (MSI)](/zscaler-client-connector/customizing-zscaler-app-install-options-msi)
- [Customizing Zscaler Client Connector with Install Options (EXE)](/zscaler-client-connector/customizing-zscaler-app-install-options-exe)
- [Customizing Zscaler Client Connector with Install Options (macOS)](/zscaler-client-connector/customizing-zscaler-app-install-options-macos)
[]You can install Zscaler Client Connector manually on individual devices or use your organization’s device management mechanism to deploy Zscaler Client Connector on your users’ devices. Before deploying Zscaler Client Connector, see [Best Practices for Zscaler Client Connector Deployment](/zscaler-client-connector/zscaler-app-deployment-best-practices-guide). For examples on how to deploy Zscaler Client Connector, see [Downloading & Deployment](/zscaler-client-connector/downloading-deployment).