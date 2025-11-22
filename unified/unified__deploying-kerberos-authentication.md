# Deploying Kerberos Authentication
Source: https://help.zscaler.com/unified/deploying-kerberos-authentication
PDF: https://help.zscaler.com/pdf/com/en/1490966.pdf

This article provides step-by-step instructions for deploying Kerberos authentication for your organization. To learn more about using Kerberos for your organization, see [About Kerberos Authentication](/unified/about-kerberos-authentication).
Requirements
Before deploying Kerberos authentication, see:
- [Kerberos Requirements](/unified/about-kerberos-authentication#kerberos-requirements)
- [Kerberos Deployment Guidelines](/unified/kerberos-authentication-deployment-guidelines)
Deploying Kerberos Authentication
To deploy Kerberos authentication:
- [1. Verify the Kerberos Realm Name Is a Zscaler Registered Domain](#verify-kerberos-realm-name)
- [2. Provision Users on the Zscaler service](#provision-users)
- [3. Configure Your Outbound Firewall](#configure-outbound-firewall)
- [4. Configure Kerberos in the Admin Portal](#configure-kerberos-auth)
- [5. (Optional) Enable Kerberos for a Location](#enable-kerberos-location)
- [6. Configure the Trust Relationship on the Organization's Server](#configure-trust-relationship)
- [7. Use PAC files to Forward Traffic to the Zscaler service](#use-pac-files)
Troubleshooting
To troubleshoot your Kerberos configuration, see [Troubleshooting Kerberos](/unified/troubleshooting-kerberos-authentication) and [Internet & SaaS Public Service Edge Error Codes for Kerberos](/unified/error-codes-kerberos-authentication).
[]To verify that your Kerberos realm name is a registered domain on the Zscaler service:
- Go to **Administration **> **Account Management** >** Company Profile**.
- In the **Organization** tab, verify that the realm name matches one of the domains in the **Domains **field.
[]Provision users on the Zscaler service. You can provision users with one of the following options:
- [Manually adding users to the Zscaler Hosted User Database](/unified/adding-users-0)
- [Importing users to the Zscaler Hosted Uster Database](/unified/importing-user-details-csv-file)
The sAMAccountName@Windows- Domain is sent as the Kerberos identifier. You might need to change the user login attribute in your synchronization settings to map to the sAMAccountName.
[]Configure your outbound firewall to allow the necessary connections. To view the Zscaler Central Authority (CA) and Internet & SaaS Public Service Edge IP addresses, log in to the Admin Portal and go to **Help **>** Cloud Configuration Requirements**.
| Source: Client Workstation |
| -------------------------- |
| Destination | Destination |
| Destination Port | Destination Port |
| Description | Description |
| Central Authority IP Addresses | Internet & SaaS Public Service Edge IP Address Ranges |
| TCP 88 or UDP 88The choice of TCP or UDP is determined by the client. Some clients fall back to the other protocol if either TCP or UDP port 88 is blocked, but this is not guaranteed. | TCP 8800 (The default Kerberos authentication port on Intrnet & SaaS Public Service Edges.) |
| Enables the client to authenticate against the Zscaler Domain KDC. | Enables the client to send traffic to the global Kerberos authentication port on the Internet & SaaS Public Service Edge. Not required if Kerberos is enabled on a location.Enabling Kerberos on a location automatically enforces Kerberos authentication, so you can send traffic to the default proxy ports, such as port 80. |
[]Configure Kerberos as an authentication mechanism to generate the domain trust password that is used to establish the trust relationship between the Zscaler domain and your organization's domain. This password is required when you configure the trust relationship.
- Go to **Administration **>** Identity **>** Internet & SaaS **>** Internet Authentication Settings**.
- Select **Enable Kerberos **to use Kerberos authentication. You can use Kerberos authentication in addition to other authentication methods. The **Domain Trust Password** field appears.
-
Under **Domain Trust Password**, click **Generate New Password**.
The **Alert** window appears.
- In the **Alert** window, click **OK**. The password appears obfuscated.
- Click **Reveal Password**.
- Copy the password. You need it when you establish the cross-realm trust between your organization's domain and the Zscaler domain.
- Click **Conceal Password**.
- Save and activate the change.
[]Optionally enable Kerberos for a location. Only do this task if you want the service to enforce Kerberos authentication on *all* web traffic explicitly forwarded from the location and its associated dedicated ports. Skip this task, if you want to use Kerberos for specific users and another authentication mechanism for all other users in the location.
To enable Kerberos authentication for all users in a location:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Location Management**.
- Click the **Edit** icon for the location.
- Enable **Enforce Authentication**.
- Enable **Enable Kerberos Authentication**.
[See image.](#seeimage5d)
- Click **Save** and activate the change.
[]![Screenshot of the Enforce Authentication and Enable Kerberos Authentication toggles](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/how-do-i-deploy-kerberos/enforce_authentication_&_enable_kerberos_authentication_toggles.png)
[]Configure the trust relationship on the organization's server. See the configuration guide for your server:
- [Configuration Example: Trust Relationship on Windows 2012 Server and GPO Push](/unified/kerberos-trust-relationship-configuration-guide-windows-server-2012-gpo-push)
- [Configuration Example: Trust Relationship on Linux Server](/unified/kerberos-trust-relationship-configuration-guide-linux-server).
[]To use Kerberos as an authentication mechanism, your organization's users must configure their browsers to use PAC files to forward their traffic to the Zscaler service, even if their location has established an IPSec or VPN tunnel to forward traffic to the service.
To use the default Zscaler PAC file for Kerberos, see [Using the Default Zscaler Kerberos PAC File](/unified/using-default-zscaler-kerberos-pac-file).