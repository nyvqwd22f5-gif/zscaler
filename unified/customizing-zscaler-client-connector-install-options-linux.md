# Customizing Zscaler Client Connector with Install Options for Linux
Source: https://help.zscaler.com/zscaler-client-connector/customizing-zscaler-client-connector-install-options-linux
PDF: https://help.zscaler.com/pdf/com/en/1380441.pdf

You can use the application package, the Debian package, or the RPM Package Manager (RPM) to manually install Zscaler Client Connector on a device. You can also use these packages if you're deploying the app to users through a device management method that supports Linux devices.
After downloading the Zscaler Client Connector package, you can deploy the file with your device management method or add install options to customize the app package using various command-line options. You can edit the parameter configuration in both the Debian package and the RPM package using a Zscaler script.
Zscaler Client Connector relies on the Linux systemd-resolved service to manage DNS configurations.
Because /etc/resolv.conf is a symbolic link to /run/systemd/resolve/stub-resolv.conf, you should not modify the /etc/resolv.conf file when deploying Zscaler Client Connector for Linux.
Zscaler Client Connector requires NetworkManager and its CLI, nmcli, which is a default system program that provides detection and configuration for systems to automatically connect to networks.
This article covers the following topics:
- [Installing Prerequisite Dependencies](#install-package-dependencies)
- [Installing the Application Using the Zscaler Run File](#install-application-run)
- [Installing the Application Using the Debian Package](#install-application-deb)
- [Downloading and Installing with RPM](#install-RPM)
- [Installing with Command-Line Options Using the Zscaler Run File](#install-package-command-line)
- [Providing Command-Line Options with the Debian Package](#install-package-command-line-deb)
- [Providing Command-Line Options with the RPM Package](#install-package-command-line-RPM)
- [Locating Logs](#install-log-locations)
[]
As long as your device is connected to the network, the application installer automatically installs the necessary prerequisite package dependencies for you. The individual package dependencies are listed here for reference:
- [Debian-Based Operating System](#DB)
- [RPM-Based Operating System](#RPM)
[]Install the following dependencies depending on the distribution you're using:
- [Ubuntu 22.04.5 LTS and Earlier](#ubuntu23)
- [Ubuntu 24 LTS](#ubuntu24)
- [Debian](#Debian)
[]
- libglib2.0-0
- net-tools
- libqt5dbus5
- libqt5core5a
- libqt5gui5
- libqt5opengl5
- libqt5qml5
- libqt5quick5
- libqt5quickcontrols2-5
- libqt5quickparticles5
- libqt5quickwidgets5
- libqt5sql5
- libqt5sql5-sqlite
- libqt5webchannel5
- libqt5webengine5
- libqt5webenginecore5
- libqt5webenginewidgets5
- libqt5webkit5
- libqt5webview5
- libqt5widgets5
- dbus
- libdbus-glib-1-2
- libnss3-tools
- libnss-resolve
- libpcap0.8 curl
- jq
- systemd-coredump
[]
- libglib2.0-0t64
- libqt5dbus5t64
- libqt5core5t64
- libqt5gui5t64
- libqt5opengl5t64
- libqt5qml5
- libqt5quick5
- libqt5quickcontrols2-5
- libqt5quickparticles5
- libqt5quickwidgets5
- libqt5sql5
- libqt5sql5-sqlite
- libqt5webchannel5
- libqt5webengine5
- libqt5webenginecore5
- libqt5webenginewidgets5
- libqt5webkit5
- libqt5webview5
- libqt5widgets5t64
- dbus
- libdbus-glib-1-2
- libnss3-tools
- libnss-resolve
- libpcap0.8t64
- curl
- jq
- systemd-coredump
[]
- libglib2.0-0
- net-tools
- dbus
- libqt5core5a
- libqt5webengine5
- libqt5webenginewidgets5
- libqt5sql5
- libqt5webkit5
- libdbus-glib-1-2
- libnss3-tools
- libnss-resolve
- libpcap0.8
- curl
- jq
- systemd-coredump
[]Install the following dependencies depending on the distribution you're using:
- [Fedora and CentOS Stream 8 and Later](#fedora)
- [Red Hat Enterprise Linux (RHEL)](#RHEL)
- [Arch Linux](#archlinux)
- [openSUSE Leap](#opensuse)
[]
- dbus-devel
- dbus-glib-devel
- qt5-qtwebengine
- qt5-qtbase-devel
- net-tools
- dbus
- dbus-glib
- nss-util
- ca-certificates
- libpcap
- systemd
- curl
- jq
CentOS 9 stream has an additional package, systemd-resolved, that is part of the Extra Packages for Enterprise Linux (EPEL) repository which must be installed separately for CentOS. The CentOS OS is required to enable the EPEL repository for Qt packages. Use one of the following commands to enable the EPEL repository:
- `sudo yum -y install epel-release`
- `sudo yum -y --disablerepo="*" --enablerepo="epel" update`
[]
- dbus-devel
- dbus-glib-devel
- qt5-qtbase
- qt5-qtwebengine
- net-tools
- dbus
- dbus-glib
- ca-certificates
- nss-util
- nss
- libpcap
- curl
- jq
RHEL 9 has an additional package, systemd-resolved, that is part of the Extra Packages for Enterprise Linux (EPEL) repository which must be installed separately for RHEL 9. The qt5-qtwebengine is also part of the EPEL repository. You must enable the EPEL repository using the following commands:
- For RHEL 8: `sudo yum -y install `[`https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`](https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm)
- For RHEL 9: `sudo yum -y install `[`https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm`](https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm)
[]
- glib2
- net-tools
- inetutils
- qt5-base
- qt5-tools
- qt5-webengine
- dbus-glib
- ca-certificates
- nss
- libpcap
- wget
- curl
- jq
[]
- dbus-1
- dbus-1-devel
- dbus-1-glib
- dbus-1-glib-devel
- ca-certificates
- nss-systemd
- systemd-network
- libpcap1
- libpcap-devel
- libQt5Core5
- libQt5WebKit5
- libQt5WebView5
- systemd
- curl
- jq
- systemd-coredump
- mozilla-nss-tools
If dependencies don't automatically install, you can install them manually by entering all dependencies in a command line on one line without line breaks, as in the following examples:
Example for Debian:
`sudo apt install libglib2.0-0 net-tools dbus libqt5core5a libqt5webengine5 libqt5webenginewidgets5 libqt5sql5 libqt5webkit5 libdbus-glib-1-2 libnss3-tools libnss-resolve libpcap0.8 curl jq systemd-coredump -y`
Example for RPM:
`sudo yum install dbus-devel dbus-glib-devel qt5-qtwebengine qt5-qtbase-devel net-tools dbus dbus-glib nss-util ca-certificates libpcap system curl jq -y`
[]
You must have administrator permission to do the installation.
To download and install the application:
- From a terminal window, open a command prompt as administrator.
- Download the Zscaler run file from the Zscaler Client Connector App Store on the Zscaler Client Connector Portal. To learn more, see [Understanding Zscaler Client Connector App Downloads](/client-connector/understanding-zscaler-client-connector-app-downloads).
- Navigate to the folder with the installation file:
cd ~/Downloads
- Make the file executable using the following command:
sudo chmod a+x Zscaler-linux-<version number>-installer.run
- Install the application using the following command:
sudo ./Zscaler-linux-<version number>-installer.run
- Leave the token form empty. You'll see the progress of your installation.
[]
You must have administrator permission to do the installation. Contact Zscaler Support to obtain the Debian package.
Installing Zscaler Client Connector with the Debian package requires the following two-step process to ensure you can provide install parameters during the installation:
- Install the Debian package.
- [Configure installation parameters using either interactive or silent mode](#configure).
The Debian package is a silent installer and does not allow any arguments to pass next to it. For example, this command would not work with the Debian package:
sudo .deb --strictEnforcement 0 --enableFips 1.
The configuration script `zscaler-config` resolves this issue. This script edits the parameters in this file:
/opt/zscaler/.config.ini.
The Zscaler Debian package name follows this convention:
<packagename>_<version number>-<Debianrevisionnumber>_<Debianarchitecture>".deb
Zscaler's package name is:
zscaler-client_<version number>_amd64.deb
zscaler-client-debug_<version number>_amd64.deb
Examples:
zscaler-client_1.3.0.11-0_amd64.deb
zscaler-client-debug_1.3.0.11-0_amd64.deb
- [Installing the Debian Package](#install-deb)
- [Removing the Debian Package](#remove-deb)
Zscaler recommends installing `systemd-coredump` before installing the Zscaler Client Connector Debian package.
[]Enter one of the following commands to install the Debian package on the system:
- `dpkg -i ``<absolutePathToThePackage>`
- `sudo apt-get install ``<absolutePathToThePackage>`
Examples:
- `sudo dpkg -i /home/zuser/Downloads/zscaler-client_1.3.0.11-0_amd64.deb`
- `sudo dpkg -i ~/Downloads/zscaler-client_1.3.0.11-0_amd64.deb`
- `sudo apt-get install /home/zuser/Downloads/zscaler-client_1.3.0.11-0_amd64.deb`
- `sudo apt-get install ~/Downloads/zscaler-client_1.3.0.11-0_amd64.deb`
[][]Enter one of the following commands to remove the Debian package from the system:
- `sudo apt-get remove ``<PackageName>`
- `sudo apt-get purge ``<PackageName>`
Examples:
- `sudo apt-get remove zscaler-client`
- `sudo apt-get purge zscaler-client`
If the Zscaler Client Connector was already installed on the system with the Zscaler run file and a user wants to install the Zscaler Client Connector Debian package, first uninstall the Zscaler run file before installing the Debian package.
[]
[][]Only administrators can use `zscaler-config` to edit the parameter configuration after the Debian package is installed on the system and requires root permission. Use the `zscaler-config` script to edit the following parameters:
- cloudName
- userDomain
- enableFips
- Help
- hideAppUIOnLaunch
- User password
- externalRedirect
- strictEnforcement
- policyToken
- deviceToken
- userName
- waitForInput
The `zscaler-config` script resides in the `/usr/bin` directory. You can use this script in the following two ways:
- [Interactive Mode](#Debconf)
- [Silent Mode](#Silent)
[]Run `zscaler-config` without parameters (e.g., `sudo zscaler-config`). You are prompted with a series of questions to set the parameters, as shown in the following image:
![Debian package install](/downloads/zscaler-tech-pubs-style-guide/draft-articles/customizing-zscaler-client-connector-install-options-linux-draft-0/MO-11001_1.png)
[]You can change the order of parameters without any UI prompting. For example, you can use the following commands in the following combinations to edit parameters:
- **command**: `sudo zscaler-config -h`
- **When to use**: To see parameter help.
- **Output**:** **Usage
zscaler-config - [ -c Cloud Name ] [-d User Domain ] [ -f Enable Fips ]
[ -h Help] [ -l hideAppUIOnLaunch ] [ -p User password ] [ -r externalRedirect ]
[ -s strictEnforcement ] [ -t policyToken ] [ -T deviceToken ] [ -u username ]
[ -w waitForInput ]
zscaler-config - [ No Argument ] For UI based interaction
zscaler-config - [ -c Cloud Name ][ String Argument ]
zscaler-config - [ -d User Domain ] [ String Argument ]
zscaler-config - [-f Enable Fips ] [ 0/1 ]
zscaler-config - [ -h Help]
zscaler-config - [ -l Hide App UI on Launch ] [ 0/1 ]
zscaler-config - [ -p User Password ] [ Sring Argument ]
zscaler-config - [ -r External Redirect ] [ 0/1 ]
zscaler-config - [ -s Strict Enforcement] [ 0/1 ]
zscaler-config - [ -S Disable sudo keyword inside the scripts] [ 0/1 ]
zscaler-config - [ -t Policy Token ] [ String Argument ]
zscaler-config - [ -T Device Token ] [ String Argument ]
zscaler-config - [ -u User Name ] [ String Argument ]
zscaler-config - [ -w Wait for Input ] [ 0/1 ]
- **command**:** **`sudo zscaler-config -s 1 -t ``<Policy Token>`` -T ``<Device Token>``-u ``<User Name>``-u`
- **When to Use**: To set the value for `strictEnforcement`, `policyToken`, `deviceToken`, and `username`.
- **Output**:** **None. The command writes data in the `/opt/zscaler/.config.ini` file.
[]RPM is a package management system that runs on Red Hat Enterprise Linux (RHEL), CentOS, and Fedora. You can use RPM to distribute, manage, and update software that you create for any of these operating systems. RPM simplifies the distribution of software because RPM packages are standalone binary files, similar to compressed archives.
Zscaler Client Connector for Linux supports the following RPM distributions: RHEL, Fedora, CentOS, and openSUSE. The Zscaler Client Connector Linux RPM package is a `.tar` file, i.e., `zscaler-client–``<release version>``-rpm.tar`, and contains two files that perform the following tasks:
- `Zscaler_package_installation.sh`: Zscaler Client Connector installation requires different dependencies based on the respective distribution. This script identifies the distribution and installs the corresponding dependencies.
- `Zscaler-client-``<release version>``-1.x86_64.rpm`: This file installs Zscaler Client Connector binaries in each system.
To download and install the CLI version of the RPM Package for Zscaler Client Connector version 3.7.1 and later for Linux, follow these steps:
- Obtain the Zscaler Client Connector RPM package from your IT administrator.
- Copy the `.tar` file to the Linux endpoint device and unzip the package using the following command:
`tar -xvf zscaler-client-3.7.1.51-rpm.tar`
![CLI to unzip the RPM package](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/step1_unzip.png)
- Run the following installation script to install all dependencies for Zscaler Client Connector:
`sudo ./zscaler_package_installation.sh install_dependency_libs`
![Client-Connector-install-dependencies](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/figure%202%20example.png)
- Install the RPM package using one of the following commands, depending on the distribution you’re using:
- For Fedora, RHEL, and CentOS, use one of the following commands:
- `sudo dnf install zscaler-client-3.7.1.51-1.x86_64..rpm`
- `sudo yum install zscaler-client-3.7.1.51-1.x86_64..rpm`
- For openSUSE, enter `sudo zypper install zscaler-client-3.7.1.51-1.x86_64..rpm`.
![Client Connector Linux Command for installing the RPM package](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/figure%203%20example.png)
While the Zscaler Client Connector package installation script displays all missing dependencies on the system and installs the missing packages for Zscaler Client Connector, it doesn’t remove Zscaler Client Connector dependencies in the current release.
[]
[]You can install the package for Zscaler Client Connector from a terminal using specific Linux command-line options. For example:
sudo ./Zscaler-linux-1.0.0.108-installer.run <install options>
Replace <install options> with one or more of the following options:
- [--cloudName](#cn)
- [--deviceToken](#dt)
- [--hideAppUIOnLaunch](#hide)
- [--policyToken](#pt)
- [--strictEnforcement](#se)
- [--userDomain](#ud)
- [--enableFips](#ef)
For example:
sudo ./Zscaler-linux-1.0.0.108-installer.run --hideAppUIOnLaunch 1 --cloudName zscalertwo
The following image is an example of a command that uses all the available installation options, where:
- The cloud on which the organization is provisioned is zscalertwo.
- The device token value is 123456789.
- The policy token value is 123456789.
- The organization's domain name is safemarch.com.
![Installation example showing all parameter options on command line](/downloads/z-app/downloading-deployment/customizing-zscaler-client-connector-install-options-linux/client-connector-all-options.png)
[]
Only administrators can use `zscaler-config` to edit the configuration after the RPM package is installed on the system. It also requires admin privileges. Use the `zscaler-config` script to edit the following parameters:
- cloudName
- userDomain
- enableFips
- Help
- hideAppUIOnLaunch
- externalRedirect
- strictEnforcement
- policyToken
- deviceToken
- userName
- MAPubKey
The `zscaler-config` script resides in the `/usr/bin` directory. You can use this script in the following combinations to edit these parameters:
- **command**: `sudo zscaler-config -h`
- **When to use**: To see parameter help.
- **Output**: Usage
- **command**: `sudo zscaler-config -s 1 -t ``<Policy Token``> -T ``<Device Token>` `-u ``<User Name>`
- **When to Use**: To set the value for `strictEnforcement`, `policyToken`, `deviceToken`, and `username`.
- **Output**: None. The command writes data in the `/opt/zscaler/.config.ini` file.
![client connector edit parameters using zscaler-config](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/figure%204%20example.png)
[]The following are locations where you can find related log information:
- Tray logs: <user home>/.Zscaler/Logs
- Zscaler system logs: /var/log/zscaler/.Zscaler/Logs
- Installer errors: /var/log/zscaler/zscaler-installation.log
[]With this install option, you can specify the cloud to which the app must send user traffic so your users won't make the selection during enrollment. Do not use this option if your organization is provisioned on one cloud. The app automatically sends traffic to the proper cloud.
This install option is required if you enable the` --strictEnforcement` option.
To add this option using the CLI, enter --cloudName <organization's cloud name in lowercase>. For example, if your cloud name is zscalertwo.net, you would enter zscalertwo. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
[]The --deviceToken install option only applies to Zscaler Internet Access (ZIA). It is not supported by Zscaler Private Access (ZPA).
This install option allows you to use Zscaler Client Connector Portal as an IdP. The Zscaler service silently provisions and authenticates users even if you don't have an authentication mechanism in place. Before adding this option, you must generate a device token in the Zscaler Client Connector Portal and complete the full configuration detailed in [Using Zscaler Client Connector Portal as an IdP](/zscaler-client-connector/using-zscaler-client-connector-portal-identity-provider).
To add this option using the CLI, enter --deviceToken* *<device token from the Zscaler Client Connector Portal>.
![Device Token](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/client-connector-IdP-Device-Token.png)
[]This install option forces the app window to stay hidden before users enroll. Users can always open the window by clicking the app icon in the system tray.
To enable this option using the CLI, enter --hideAppUIOnLaunch 1. By default, the value is 0 (i.e., disabled).
[]This install option allows you to specify which app profile policy you want to enforce for the app before the user enrolls. All relevant settings associated with the policy apply, including the bypass of the IdP login page. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on group affiliation.
Prerequisites:
- This install option is only applicable, and required, if you enable the --strictEnforcement option and want users to enroll with the app before accessing the internet.
- In the Zscaler Client Connector Portal, you must [configure the app profile policy](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles) that you want to enforce and ensure that the custom PAC file associated with that policy includes a bypass for your IdP login page. This allows the user to access the IdP page to log in as necessary before enrolling with the app.
To add this option using the CLI, enter --policyToken <policy token from the Zscaler Client Connector Portal>.
![Policy Token](/downloads/tech-pubs-drafts/client-connector-draft-articles/customizing-zscaler-client-connector-install-options-linux/client-connector-app-profiles-token.png)
[]This install option only works when the forwarding profile action for Zscaler Client Connector is **Tunnel** or **Tunnel with Local Proxy**. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector).
This install option allows you to require users to enroll with the app before accessing the internet and blocks traffic in the following situations:
- The user has not yet logged in after a new install.
- A user logs in and logs out.
- An administrator removes a device.
This install option does not affect users that remain logged in and disable the ZIA service.
If you enable this install option, the `--cloudName` and `--policyToken` options are required.
To enable this option using the CLI, enter `--strictEnforcement 1`. By default, the value is 0 (i.e., disabled).
[]This install option allows users to skip the app enrollment page. If SSO is enabled for your organization, users are taken directly to your organization's SSO login page. If you've integrated SSO with the app, users can also skip the SSO login page and are automatically enrolled in the Zscaler service and logged in.
[See image.](#udimage2)
To add the install option using the CLI, enter --userDomain <your organization's domain>. If your instance has multiple domains associated with it, enter the primary domain for your instance.
[]This install option allows you to enable the Federal Information Processing Standard (FIPS) mode for Zscaler Client Connector. By default, the value is 0 (i.e., disabled).
[]![The Zscaler Client Connector enrollment page and an organization SSO login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/downloading-and-deploying-zscaler-app/customizing-zscaler-app-install-options-macos/19897a56-8004-4068-aaf7-dd52975a8e4c.png?1602764389)