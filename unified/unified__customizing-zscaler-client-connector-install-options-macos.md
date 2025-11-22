# Customizing Zscaler Client Connector with Install Options for macOS
Source: https://help.zscaler.com/unified/customizing-zscaler-client-connector-install-options-macos
PDF: https://help.zscaler.com/pdf/com/en/1491931.pdf

For Zscaler Client Connector version 3.9 and later for macOS, Zscaler Client Connector now uses a pkg installation process with plist (property list) configuration settings deployed from an MDM. Versions earlier than Zscaler Client Connector 3.9 for macOS used an installation script with variables. The deployment process for each is as follows:
For Zscaler Client Connector version 3.9 and earlier for macOS
You can deploy Zscaler Client Connector via the MDM (Mobile Device Management) used by your organization or by manually installing Zscaler Client Connector on a device.
To add install options to customize the app package for your organization using various command-line options:
- [Installing the Package with Command-Line Options](#install-package-command-line)
- [Allowing Users to Log into Zscaler Client Connector without Entering Domains](#Allowing-without-domain)
[]To install the package using macOS command-line options:
- Open the **Applications** folder.
- Open the **Utilities** folder.
- Double-click the **Terminal **icon.
- Enter the following command:
sudo sh <complete path>/Contents/MacOS/installbuilder.sh <install options>
- Replace <complete path> with the absolute pathname to the package file. For example, /Users/Admin/Downloads/Zscaler-osx-1.5.2.6-installer.app
- Replace <install options> with the one or more of the following install options:
- [--cloudName](#cn)
- [--deviceToken](#dt)
- [--hideAppUIOnLaunch](#hide)
- [--launchTray](#lauchTray)
- [--mode](#mode)
- [--policyToken](#pt)
- [--strictEnforcement](#se)
- [--unattendedmodeui](#umui)
- [--userDomain](#ud)
- [--externalRedirect](#external-redirect)
The following image is an example of a command-line that uses all the available install options above, where:
- The absolute path to the package file is /Users/Admin/Downloads/Zscaler-osx-1.5.2.6-installer.app
- The cloud on which the organization is provisioned is zscalertwo
- The device token value is 123456789
- The policy token value is 987654321
- The organization's domain name is safemarch.com
![Installing the Zscaler Client Connector package with a command line](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-macos/Z-App-macOS-CLI-Options.png)
[]If your organization is provisioned on more than one cloud, your users are asked to select the cloud to which their traffic is sent during the enrollment process.
[See image.](#cnimage2)
With this install option, you can specify the cloud to which the app must send user traffic so that your users do not have to make the selection during enrollment. This option is not needed if your organization is provisioned on one cloud. The app automatically sends traffic to the proper cloud and your users do not need to make a selection during enrollment.
This install option is required if you enable the --strictEnforcement option.
To add this option using the command-line, enter --cloudName <organization's cloud name in lowercase>. For example, if your cloud name is zscalertwo.net, you would enter zscalertwo.
[]![Selecting a cloud on the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-macos/24f92544-ad8c-4691-9519-14a36c465838.png)
[]The --deviceToken install option only applies to Internet & SaaS. It is not supported by Private Applications.
This install option allows you to use Zscaler Client Connector as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Admin Portal and complete the full configuration detailed in [Using Zscaler Client Connector as an IdP](/unified/using-zscaler-client-connector-identity-provider).
To add this option using the command-line, enter --deviceToken* *<device token from the Admin Portal>.
[]This install option forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
To enable this option using the command-line, enter --hideAppUIOnLaunch 1. By default, the value is 0 (i.e., disabled).
[]By default, Zscaler Client Connector starts its services and user interface after installation. This install option prevents Zscaler Client Connector from automatically starting after installation. Users must open Zscaler Client Connector manually to start the app, or Zscaler Client Connector automatically runs after the next reboot.
To disable this option using the command-line, enter --launchTray 0. By default, this value is 1 (i.e., enabled).
[]This install option allows you to install the app in silent mode.
If you add this option for macOS, the --unattendedmodeui option with a value of none is required. To learn more, see --unattendedmodeui.
To add this option using the command-line, enter --mode unattended
[]This install option allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy apply, including the bypass of the IdP login page. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on group affiliation.
Prerequisites:
- This install option is only applicable, and required, if you enable the --strictEnforcement option and want users to enroll with the app before accessing the internet.
- In the Admin Portal, you must [configure the app profile policy](/unified/configuring-zscaler-client-connector-app-profiles) that you want to enforce and ensure that the custom PAC file associated with that policy includes a bypass for your IdP login page. This allows the user to access the IdP page to log in as necessary before enrolling with the app.
To add this option using the command-line, enter --policyToken <policy token from the Admin Portal>.
![The policy token for a Zscaler Client Connector profile policy](/downloads/z-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-macos/zapp-macos-policytoken.png)
[]This install option only works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
This install option allows you to require users to enroll with the app before accessing the internet and blocks traffic in the following situations:
- The user has not yet logged in after a new install.
- A user logs in and logs out.
- An administrator removes a device.
This install option does not affect users that remain logged in and disable the Internet & SaaS service.
If you enable this install option, the --cloudName and --policyToken options are required.
To enable this option using the command-line, enter --strictEnforcement 1. By default, the value is 0 (i.e., disabled).
[]This install option allows you to control what's displayed to users if you are performing an unattended installation of the app.
To add the install option using the command-line, enter --unattendedmodeui <value>, where <value> is one of the following:
- none: Nothing is displayed to the user and no interaction is required. If you included the mode --unattended install option for macOS, you must include --unattendedmodeui with a value of none.
- minimal: A small progress bar showing installation progress is displayed to the user and no interaction is required.
- minimalWithDialogs: More information is displayed to the user with some dialogs that require user interaction.
[]This install option allows users to skip the app enrollment page. If SSO is enabled for your organization, users are taken directly to your organization's SSO login page. If you've integrated SSO with the app, users can also skip the SSO login page and are automatically enrolled with Zscaler service and logged in.
[See image.](#udimage2)
To add the install option using the command-line, enter --userDomain <your organization's domain>. If your instance has multiple domains associated with it, enter the primary domain for your instance.
[]![The Zscaler Client Connector enrollment page and an organization SSO login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-macos/19897a56-8004-4068-aaf7-dd52975a8e4c.png?1602764389)
[]The –-externalRedirect install option redirects authentication to your organization’s SAML IdP through the Safari browser. When redirected to the browser for the first time, your users must select Remember Me on their IdP log-in screen. For any subsequent authentications, the browser remembers the user and automatically logs them in.
To enable this option using the command-line, enter --externalRedirect true. The default is false.
[]This configuration can only be used if your organization's domain is registered on a single cloud. If your organization's domain is registered on multiple clouds, use the command-line install options described earlier.
This configuration achieves the same function as the --userDomain install option. The following guidelines apply:
- Your organization is using Zscaler Client Connector version 1.5 or later.
- If you've integrated your SSO with Zscaler Client Connector (using a mechanism like Integrated Windows Authentication (IWA), users can also skip the SSO login page and are automatically enrolled with Zscaler service and logged in.
To allow users to log into the app without entering domains:
- Locate the macOS installer file.
- Prefix the file name with your organization's domain name. For example, if the file name is Zscaler-osx-1.5.0.326-installer and your organization's domain is safemarch.com, you would rename the file to safemarch.com-Zscaler-osx-1.5.0.326-installer.
![A configured Zscaler Client Connector macOS installer file that allows users to log in without entering domains](/downloads/z-app/downloading-deployment/customizing-zscaler-app-install-options-macos/configured-macOS-Z-App-installer-file.png)
For Zscaler Client Connector version 3.9 and later for macOS
If you are using Zscaler Client Connector version 3.9 or later for macOS, you must use a pkg installation process with property list (plist) configuration settings deployed from an MDM. The manual deployment process through install options is no longer applicable.
To install Zscaler Client Connector for your macOS devices, choose the following deployment procedure:
The steps for downloading and deploying the app vary by your MDM.
- [Deploying Zscaler Client Connector with Microsoft Intune for macOS](/unified/deploying-zscaler-client-connector-microsoft-intune-macos)