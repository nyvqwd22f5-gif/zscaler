# Blocking LAN Access and Configuring Zscaler Client Connector Firewall on Windows and macOS
Source: https://help.zscaler.com/zscaler-client-connector/blocking-lan-access-windows-and-configuring-zscaler-client-connector-firewall-macos
PDF: https://help.zscaler.com/pdf/com/en/1443386.pdf

To prevent users from accessing other endpoints on local area networks, admins can configure Zscaler Client Connector to block traffic.
On Windows devices, you can block traffic based on the version of Zscaler Client Connector:
- Zscaler Client Connector versions 4.7 and earlier: Block outbound traffic in Zscaler Tunnel (Z-Tunnel) 2.0 using destination exclusions.
- Zscaler Client Connector versions 4.8 and later: Block inbound and outbound traffic in Z-Tunnel 1.0, Z-Tunnel 2.0, and Tunnel with Local Proxy using the [Endpoint Firewall Management](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#firewall) feature.
On macOS devices, admins must create a system extension profile via a mobile device management (MDM), configure firewall rules, and also enable firewall settings in the Zscaler Client Connector Portal.
- [Windows](#windows-linux)
- [macOS](#mac)
[]To block LAN access for Windows devices using Zscaler Client Connector version 4.7 and earlier:
- Go to **App Profiles** > **Windows**.
- Click **Add Windows Policy**.
The **Add Windows Policy** window appears.
- In **(Optional) For Z-Tunnel 2.0 Configuration**:
**Destination Exclusions**: Enter the specific subnets of the traffic you want to exclude from Z-Tunnel 2.0.
By default, the Zscaler service includes the RFC 1918 networks (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) in the exclusions list. See [RFC 1918 Address Allocation for Private Internets](https://tools.ietf.org/html/rfc1918). Zscaler also includes the multicast range 224.0.0.0/4. Zscaler recommends that you keep these networks in the list, unless explicitly needed, because deleting them causes private network traffic (e.g., DHCP) to be tunneled through the cloud.
If you use Zscaler Client Connector version 4.8 and later for Windows, you can use the [Endpoint Firewall Management](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#firewall) feature to block LAN access. To learn more, see [About Location-Based Policies](/zscaler-client-connector/about-location-based-policies).
[]To block LAN access or control firewall rules using Zscaler Client Connector for macOS devices, configure these steps based on the MDM you are using.
In the content filter section, you can configure parameters and edit the keys and values in the general, inbound, and outbound sections. The following information applies to both Microsoft Intune and Jamf Pro.
- [See configuration parameters.](#shared-config-parameters)
[][][]You can edit the following general and firewall parameters in the copied content based on your needs:
General Parameters
- **enforceTrafficViaTunnel**: If true, when the tunnel is inactive, prevents circumvention of security by restricting network traffic when the Z-Tunnel is not running.
- **allowTrafficToDefaultGateway**: If set to false, traffic to the default gateway is blocked. Use this parameter with caution as it can prevent the device from interacting with captive portals and other services that the default gateway device provides.
- **Persistent**: If true, filtering remains on even when the user exits or logs out of Zscaler Client Connector, or turns off Zscaler Internet Access (ZIA). The feature is disabled only after the user logs out. If the persistent key is false, filtering stops when the user exits Zscaler Client Connector, turns off ZIA, or logs out.
- **detectAltInterfaceTraffic**: When set to true, Zscaler Client Connector detects traffic that attempts to bypass the routing table. This parameter is not supported on Zscaler Client Connector version 4.5.2 and later for macOS.
- **alwaysAllowed**: Inbound and outbound traffic defined using this parameter is always allowed even when enforceTrafficViaTunnel is set to true.
This parameter applies to Z-Tunnel 1.0 and Z-Tunnel 2.0 and is supported on Zscaler Client Connector version 4.5.2 and later for macOS.
Firewall Parameters
- **action**: Defines what action is taken if the rule matches. Use `allow` or `block`.
- **apps**: Specifies a flow's association with a particular application. This value must exactly match the teamid.bundleid, unless the app has no Team ID, in which case the app must exactly match the bundleid.
- **protos**: Specifies the IP protocol that the flow must match. For example, `tcp` and/or `udp` or `icmp`.
System extension does not filter incoming ICMP.
- **ips**: Specifies the set of remote IP addresses that the flow must match. Add a space or a comma to the delimited list of IP addresses and/or IP subnets. Mixed IPv4, IPv6 addresses, and `lanlocal` are allowed.
- **ports**: Specifies what UDP or TCP ports cause the rule to match the flow. Add a space or comma to the delimited list of port numbers and/or port ranges. If `protos` is configured and is set to `icmp`, the `ports` attribute is ignored.
The `VendorConfig` section of the ZscalerSample.mobileconfig has several dictionaries that determine the logic for the traffic.
The top-level dictionaries are `general`, `inbound`, and `outbound`. Within each dictionary are dictionaries for untrusted or trusted networks. Each trusted and untrusted key contains an optional array of rule dictionaries. Within each rule dictionary, you can define specific actions.
Configuration Parameters Examples
The following is an example of the structure for general:
- [General example](#general-example)
[]
`<key>general</key>
<dict>
<key>allowTrafficToDefaultGateway</key>
<true/>
<!--- The detectAltInterfaceTraffic is deprecated in Zscaler Client Connector 4.5.2 and later for macOS -->
<key>detectAltInterfaceTraffic</key>
<true/>
<key>enforceTrafficViaTunnel</key>
<true/>
<key>persistent</key>
<false/>
<key>alwaysAllowed</key>
<array>
<dict>
<key>ips</key>
<string>1.2.3.4</string>
<key>ports</key>
<string>80,443</string>
<key>action</key>
<string>allow</string>
</dict>
</array>
</dict>
`
The following is an example of this structure for inbound:
- [Inbound example](#inbound-example)
[]
`<key>inbound</key>
<dict>
<key>trustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedsplitvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>untrustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
</dict>
`
Actions include `allow` and `block`. Possible network specifications include applications (`apps`), IP addresses (`ips`), and ports (`ports`).
To block the browser Opera from communicating outbound, block traffic to 1.2.3.4 and any local network traffic, and port 5432 traffic on an untrusted network, see the following example:
- [Outbound example](#outbound-example)
[]
`<key>outbound</key>
<dict>
<key>trustednet</key>
<array>
<dict>
<key>action</key>
<string>allow</string>
</dict>
</array>
<key>untrustednet</key>
<array>
<dict>
<key>apps</key>
<string>A2P9LX4JPN.com.operasoftware.Opera</string>
<key>ips</key>
<string>1:2:3:4:: 192.168.0.0/16 lanlocal</string>
<key>ports</key>
<string>5900-5901 2222</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ips</key>
<string>1:2:3:4:: 1.2.3.4 lanlocal</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ports</key>
<string>5432</string>
<key>action</key>
<string>block</string>
</dict>
</array>
<key>trustedvpnnet</key>
<array>
<dict>
<key>apps</key>
<string>A2P9LX4JPN.com.operasoftware.Opera</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ips</key>
<string>1:2:3:4:: 1.2.3.4 lanlocal</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ports</key>
<string>5432</string>
<key>action</key>
<string>block</string>
</dict>
</array>
<key>trustedsplitvpnnet</key>
<array>
<dict>
<key>apps</key>
<string>A2P9LX4JPN.com.operasoftware.Opera</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ips</key>
<string>1:2:3:4:: 1.2.3.4 lanlocal</string>
<key>action</key>
<string>block</string>
</dict>
<dict>
<key>ports</key>
<string>5432</string>
<key>action</key>
<string>block</string>
</dict>
</array>
</dict>                                                                                                                                         `
**How are Rules Evaluated?**
The above `untrustednet` array has three separate rules (`apps`, `ips`, `ports`). Each rule is independent of the other two. For example, if traffic from `Opera` is detected, it matches only the first rule (`apps`), where the second rule (`ips`) and third rule (`ports`) are not evaluated. Similarly, if the second rule is matched because the traffic is not from `Opera`, but the remote address is `1.2.3.4`, then the third rule is not evaluated. Only if the traffic is not from `Opera`, and is also not destined for `1:2:3:4::`, `1.2.3.4`, or `lanlocal`, then the third rule is evaluated.
You can combine key types for more specific rules, such as disallowing `Opera` traffic only if the destination is `1.2.3.4:5432:.` For example:
- [Combined rules example](#combined-rules-example)
[]
`<dict>
<key>apps</key>
<string>A2P9LX4JPN.com.operasoftware.Opera</string>
<key>ips</key>
<string>1:2:3:4:: 1.2.3.4 lanlocal</string>
<key>ports</key>
<string>5432</string>
<key>action</key>
<string>block</string>
</dict>`
The following is a complete property list (PLIST) example for both general and firewall parameters.
- [All general and firewall parameters](#all-example)
[]
`<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>VendorConfig</key>
<dict>
<key>general</key>
<dict>
<key>allowTrafficToDefaultGateway</key>
<true/>
<!--- The detectAltInterfaceTraffic is deprecated in Zscaler Client Connector 4.5.2 and later for macOS -->
<key>detectAltInterfaceTraffic</key>
<true/>
<key>enforceTrafficViaTunnel</key>
<true/>
<key>persistent</key>
<false/>
<key>alwaysAllowed</key>
<array>
<dict>
<key>ips</key>
<string>1.2.3.4</string>
<key>ports</key>
<string>80,443</string>
<key>action</key>
<string>allow</string>
</dict>
</array>
</dict>
<key>inbound</key>
<dict>
<key>trustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedsplitvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>untrustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
</dict>
<key>outbound</key>
<dict>
<key>trustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedsplitvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>trustedvpnnet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
<key>untrustednet</key>
<array>
<dict>
<key>action</key>
<string>block</string>
<key>ips</key>
<string>lanlocal</string>
</dict>
</array>
</dict>
</dict>
</dict>
</plist>`
Microsoft Intune
In the Microsoft Intune portal, you can deploy the Zscaler System Extension, configure general firewall behavior, and configure inbound and outbound rules:
- [Step 1: Configure a System Extension Profile in the Microsoft Intune Portal](#SystemExtensionProfile)
- [Step 2: Configure Firewall Rules in Microsoft Intune Portal](#firewall-rules)
- [Step 3: Configure a Property List File in the Microsoft Intune Portal](#PropertyListFile)
- [Step 4: Enable Firewall Settings in the Zscaler Client Connector Portal](#EnableFirewall)
Jamf Pro
The Jamf Pro configuration for Zscaler Firewall has changed. Follow the directions outlined in [Remove the Firewall Rules from Application and Custom Settings](#jamf-step-remove-firewall-rules-app-custom-settings) to reconfigure your existing configuration profiles to ensure the firewall rule updates are enforced without any disruption.
- [Step 1: Create a Configuration Profile for Auto Approval of Zscaler System Extension](#configuration-profile-auto-approval-Zscaler-system-extension)
- [Step 2: Configure the Firewall Rules in Jamf Pro](#configure-firewall-rules-Jamf-Pro)
- [Step 3: Enable Firewall Settings in the Zscaler Client Connector Portal](#enable-firewall-settings-client-connector-portal)
- [Step 4: (For legacy/pre-existing configurations) Remove the Firewall Rules from Application and Custom Settings](#remove-firewall-rules-from-application-and-custom-settings)
- []In the Microsoft Intune Portal, go to **Devices**.
- From the options, click **Configuration profiles**.
[See image.](#mac-create-config-profile)
- Click **Create profile**.
[See image.](#mac-create-profile)
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Extensions**.
[See image.](#mac-create-a-profile)
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the preference file. For example, `Zscaler System Extension`.
- **Description**: (Optional) Enter a description.
[See image.](#mac-basics)
- Click **Next**.
- In the **Configuration settings** section, expand the **System extensions** section:
- **Block user overrides**: Select **Yes** if you want to block the users from making any changes to the file. The default setting is **Not configured**.
- **Team identifier**: Enter the team identifier `PCBCQZJ7S7`.
The team identifier allows the System Extension Profile to be installed on the user's system silently.
[See image.](#mac-system-extensions)
- Click **Next**.
- In the **Assignments** section, choose the users, groups, and devices for the profile.
[See image.](#mac-assignments)
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
If the system extension feature is activated using a command line, you must deactivate it manually. Uninstallation of Zscaler Client Connector does not remove the system extension feature.
[]![Configuration profiles in Microsoft Intune](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-macos-configuration%20Profiles.png)
[]![Create a profile in configuration profiles](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-macos-Intune-Create-%20profile.png)
[]![Create a profile section](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-create-a-profile.png)
[]![Basics section in the configuration profiles](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-intune-basics.png)
[]![System extensions in confirguration settings](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-intune-configuration-settings.png)
[]![Assignments section in configuration profiles](/downloads/z-app/downloading-deployment/blocking-lan-access/zclientconnector-intune-assignments.png)
- []In the Microsoft Intune Portal, go to **Devices**.
- From the options, click **Configuration profiles**.
- Click **Create profile**.
- In the **Create a profile** section:
- **Platform**: Select **macOS**.
- **Profile type**: Select **Templates**.
- **Template name**: Choose **Custom**.
- Click **Create**.
- In the **Basics** section:
- **Name**: Enter a name for the preference file. For example, `Zscaler firewall rules`.
- **Description**: (Optional) Enter a description.
- Click **Next**.
- Use a mobileconfig file. You can download the following ZscalerSample.mobileconfig file:
[Download the ZscalerSample.mobileconfig file](/downloads/zscaler-client-connector/downloading-deployment/blocking-lan-access/ZscalerSampleMobileConfig.mobileconfig)
- In the **Configuration settings** section, upload the ZscalerSample.mobileconfig file and configure the Zscaler Client Connector firewall for macOS [configuration parameters.](#intuneconfigparam)
- Click **Next**.
- In the **Assignments** section, choose the users, groups, and devices for the profile.
- Click **Next**.
- In the **Review + create** section, review the summary, and click **Create**.
[]To create a property list file, see [Configuring a Custom Settings Profile](/zscaler-client-connector/deploying-zscaler-client-connector-microsoft-intune-macos#configure-custom-profile).
- []In the Zscaler Client Connector Portal, go to **App Profiles** > **macOS**.
- Click **Add macOS Policy**.
The **Add macOS Policy** window appears.
- In **Add macOS Policy **window, under **Traffic Steering**, go to **App and IP Bypass **>** Firewall.**
- Enable **Zscaler Firewall** to determine which network traffic is allowed and blocked. This setting is disabled by default.
![Zscaler Firewall setting in macOS policy](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/zscaler-firewall-app-profiles.png)
[]Although Zscaler system extension is built into Zscaler Client Connector, you must configure it in Jamf to activate it. To add a configuration profile for system extension:
- In the Jamf Pro portal, go to the **Computers **tab.
- In the left-side navigation, select **Configuration Profiles**.
[See image.](#jamf-computers-config-profiles)
[]![Jamf PRO computers tab](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-firewall-rules-draft/jamf-computers-config-profiles.png)
- Click **New** to create a new configuration profile.
- In the **General** section:
- **Name**: Enter a name. For example, `Zscaler Socket Filter System Extension Deployment`.
- **Description**: (Optional) Enter a description.
- **Category**: (Optional) Choose a category based on the Jamf categories you configured.
- **Level**: Choose a level per your requirements.
- **Distribution Method**: Choose a distribution method per your requirements.
[See image.](#jamf-system-extension-general)
[]![General section of configuration profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configuration-Profile-System%20Extension-General.png)
- From the left-side navigation, click **System Extensions** and select **Configure**.
[See image.](#jamf-system-extension-configure)
[]![Configure system extensions](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configuration-Profile-System%20Extension-Configure.png)
- Under **System Extensions**:
- **Display Name**: Enter a display name. For example, `Zscaler Filter Socket Filter System Extension`.
- **System Extension Types**: Select **Allowed Team Identifiers** from the drop-down menu.
- **Team Identifier**: Enter `PCBCQZJ7S7`.
- Click **Save**.
[See image.](#jamf-system-extension-configure-save)
[]![System Extensions](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configuration-Profile-System%20Extension-Configure-Save.png)
- To bind the Configuration Profile to particular computers, select the necessary information for **Targets**, **Limitations**, and **Exclusions** under the **Scope** tab.
[][]Create a Content Filter Configuration Profile to configure firewall rules. To add a Content Filter:
- In the Jamf Pro portal, go to the **Computers **tab.
- In the left-side navigation, select **Configuration Profiles **and click **New**.
- In the **General** section:
- **Name**: Enter a name. For example, `Zscaler Firewall Rules`.
- **Description**: (Optional) Enter a description.
- **Category**: (Optional) Choose a category based on the Jamf categories you configured.
- **Level**: Choose a level per your requirements.
- **Distribution Method**: Choose a distribution method per your requirements.
[See image.](#jamf-configure-firewall-rules-general)
[]![General section](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Firewall-Rules-General.png)
- From the left-side navigation, select **Content Filter**.
- In the **Content Filter** section:
- **Filter Name**: Enter a name for your filter. For example, `Zscaler Socket Filter System Extension`.
- **Identifier**: Enter `com.zscaler.zscaler`.
- **Service Address**: Enter `zscaler.com.`
- **Organization**: Enter `Zscaler`.
- **User Name**: (Optional) Enter a username.
- **Password**: (Optional) Enter a password.
[See image.](#jamf-configure-firewall-rules-content-filter)
[]![Content Filter section](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Firewall-Rules-Content-Filter.png)
- **Socket Filter**: Click **Enable**.
- **Socket Filter Bundle Identifier**: Enter `com.zscaler.zscaler.pktfilter`
- **Socket filter Designated Requirement**: Enter `identifier "com.zscaler.zscaler.pktfilter" and anchor apple generic`
- Click **Save**.
[See image.](#jamf-configure-firewall-rules-content-filter-2)
[]![Content filter section continued](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-windows-and-configuring-zscaler-client-connector-firewall-macos-doc-58237/Jamf-Configure-Firewall-Rules-Content-Filter-2_0.png)
- In the **Custom Data** section, define the Zscaler Client Connector [firewall configuration parameters](#Jamfconfigparam) for general, outbound and inbound rules.
To disable a feature, set the value to False.
- Click **Save**.
[See image.](#jamf-configure-firewall-rules-content-filter-gen-inbound-outbound)
[]![Custom Data inputs](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Firewall-Rules-Content-Filter-Gen-Outbout-Inbound-.png)
[]
- In the Zscaler Client Connector Portal, go to **App Profiles** > **macOS**.
- Click **Add macOS Policy**.
The **Add macOS Policy** window appears.
- In **Add macOS Policy **window, enable **Zscaler Firewall** to determine which network traffic is allowed and blocked. This setting is disabled by default.
- (Optional) If firewall persistence is required, enable the **Persistent Zscaler Firewall** setting. This setting is disabled by default.
[See image.](#jamf-configure-firewall-rules-client-connector-portal)
[]![Go to macOS App Profiles, Enable Zscaler Firewall](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Enable-Firewall-Rules-Zscaler-Client-Connector-Portal-App-Profile.png)
When Zscaler Client Connector performs a policy update, the Zscaler Firewall feature is enabled and the firewall rules are enforced.
If you want to change firewall parameters or rules, edit the Configuration Profile and redeploy it to macOS devices using Jamf Pro. No change is required to the App Profiles in the Zscaler Client Connector Portal when changing existing firewall rules.
[][]If you have existing legacy configuration profiles in Jamf Pro, you must remove **Application and Custom Settings** and add general, inbound, and outbound firewall rules to the **Content Filter** payload. Following these steps ensures that firewall rule changes are enforced without any disruption. This applies to Zscaler Client Connector for macOS versions 4.5.0.211, 4.3.1.102 and later.
- In the Jamf Pro portal, go to the **Computers** tab.
- In the left-side navigation, select **Configuration Profiles** and open the existing **Configuration Profile**.
[See image.](#jamf-remove-legacy)
[]![Go to Configuration Profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Remove-Firewall-Rules-Legacy.png)
- Select **Application and Custom** **Settings** and save a copy of the property list (PLIST) configuration.
[See image.](#jamf-remove-legacy-save-plist)
[]![Save a copy of plist file ](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Remove-Firewall-Rules-Legacy-Save-Plist.png)
- Click **Remove All** to remove the payload from the **Configuration Profile**.
[See image.](#jamf-remove-legacy-remove-all)
[]![Click Remove All](/downloads/tech-pubs-drafts/client-connector-draft-articles/blocking-lan-access-mo-40040-doc-56696/Jamf-Configure-Remove-Firewall-Rules-Legacy-Remove-All.png)
- Add the general, inbound and outbound firewall rules to the **Content Filter** payload as shown in [Configure the Firewall Rules in Jamf Pro.](#jamf-step-configure-firewall-rules)