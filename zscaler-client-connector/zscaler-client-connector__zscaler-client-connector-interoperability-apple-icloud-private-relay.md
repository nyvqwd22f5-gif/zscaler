# Zscaler Client Connector Interoperability with Apple iCloud Private Relay
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-interoperability-apple-icloud-private-relay
PDF: https://help.zscaler.com/pdf/com/en/1529917.pdf

iCloud Private Relay is a security feature available on Apple iOS and macOS devices. It routes internet traffic through Apple’s servers and encrypts client DNS traffic to obfuscate the end user's identity. iCloud Private Relay encrypts client DNS traffic before it is intercepted by Zscaler Client Connector. This interferes with Zscaler Client Connector’s ability to process DNS requests and can disrupt both Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) traffic flows.
Zscaler recommends disabling iCloud Private Relay when deploying Zscaler Client Connector to iOS and macOS devices to avoid connectivity issues.
How do I disable iCloud Private Relay?
End Users
End users can check whether iCloud Private Relay is enabled and then disable iCloud Private Relay on their individual devices. To learn more, refer to the following documentation based on the OS:
- [iOS](https://support.apple.com/en-sg/guide/iphone/iph499d287c2/ios)
- [macOS](https://support.apple.com/guide/mac-help/use-icloud-private-relay-mchlecadabe0/mac)
Administrators
You can Disable iCloud Private Relay in App Profiles. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#iOS-advanced). Applies to Zscaler Client Connector version 4.4 and later for iOS.
Administrators can return an NXDOMAIN response for the hostnames used by iCloud Private Relay traffic to alert end users that they must disable iCloud Private Relay. To learn more, refer to the *Allow for network traffic audits* section in the [Apple documentation](https://developer.apple.com/icloud/prepare-your-network-for-icloud-private-relay/).
If you use Jamf Pro or another MDM to deploy Zscaler Client Connector, you can restrict iCloud Private Relay by distributing a configuration profile. To learn more, refer to the [Jamf documentation](https://learn.jamf.com/en-US/bundle/jamf-security-cloud-setup-guide/page/Enabling_the_HTTPS_Block_Page_for_Supervised_Apple_Devices.html).