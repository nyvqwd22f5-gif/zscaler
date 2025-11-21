# About the Zscaler Authentication Bridge
Source: https://help.zscaler.com/zia/about-zscaler-authentication-bridge
PDF: https://help.zscaler.com/pdf/com/en/1399631.pdf

[Watch a video about the Zscaler Authentication Bridge](https://fast.wistia.net/embed/iframe/ulvay54489)
The Zscaler Authentication Bridge (ZAB) is a virtual appliance that you can use to [provision as well as authenticate users](/zia/provisioning-and-authenticating-users). You can use the ZAB to automatically import user information from an Active Directory (AD) or a Lightweight Directory Access Protocol (LDAP) server to the Zscaler database, without requiring inbound connections to your directory server. The ZAB can be used solely as a provisioning tool in conjunction with another authentication mechanism, such as [SAML](/zia/configuring-saml) or [Kerberos](/zia/about-kerberos-authentication). Alternatively, it can be used for authentication using [LDAP](/zia/synchronizing-users-directory-server) with SSL client certificates.
The ZAB scales to hundreds of thousands of users. It requires minimal administration. After you deploy it, you can configure the Zscaler service to automatically synchronize users on demand, daily, weekly, or monthly. To learn more, see [Deploying a Zscaler Authentication Bridge](/zia/how-do-i-deploy-zscaler-authentication-bridge).
The Authentication Bridge page is unavailable if you're subscribed to the ZIdentity service. Users can be imported into the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) through different methods to enroll them in the ZIA service. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
Authentication Bridges provide the following benefits and enable you to:
- Automatically import user information from an AD or LDAP server to the Zscaler database.
- Scale to hundreds of thousands of users with minimal administration.
New or clean deployment of ZAB requires a virtual machine image running on Zscaler OS version 24.
Provisioning Users
You can download the ZAB from the ZIA Admin Portal and install it as a virtual appliance on a hypervisor at your location. As shown in the diagram, the ZAB opens a long-living secure outbound tunnel to the Zscaler Central Authority (CA). It downloads the authentication profile configuration of your organization from the CA and connects to the directory server. It synchronizes user information from the directory server to the Zscaler cloud on demand or as scheduled.
- The ZAB downloads your organization's authentication profile.
- The ZAB synchronizes user information to the Zscaler service on demand or as scheduled.
![A diagram of provisioning users with the Zscaler Authentication Bridge](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-zscaler-authentication-bridge-draft/zia-provisioning-users-about-zscaler-authentication-bridge.png)
The Zscaler service synchronizes data as follows:
- It adds users, groups, and departments that are in the directory server, but not in the Zscaler service. It can synchronize up to 128 groups per user.
- It deletes users, groups, and departments that are in the service, but not in the directory server. The service invalidates the authentication cookies of the users that were deleted and they are no longer allowed to authenticate.
- If there is a discrepancy between the information that’s in the service and in the directory server, the ZAB modifies its data to match what’s in the directory server.
The ZAB doesn't synchronize passwords. Passwords are always stored and maintained on your directory server.
Authenticating Users
A ZAB can also be used as an authentication tool. As shown in the diagram, the Zscaler service communicates only with the ZAB during the authentication process. The service directs requests to the ZAB, which in turn authenticates users against your organization's directory server. The passwords are always stored on your directory server. They are never stored on the ZAB or the CA.
- A user opens a browser and sends an HTTP request.
- When the ZIA Public Service Edge receives an unauthenticated request, it displays the login form.
- The user enters a login name.
- The ZIA Public Service Edge sends the request to the Central Authority (CA).
- The CA directs the request to the Zscaler Authentication Bridge (ZAB).
- The ZAB challenges the user for a password. It then creates a TLS connection to the directory server and sends an LDAP BIND request with the username and password.
- The user enters the username and password.
- After the user is authenticated, the ZAB redirects the browser to the CA.
- The CA sets the Zscaler gateway cookie and redirects the browser to the Zscaler Public Service Edge.
- The Zscaler Public Service Edge sets the domain cookie on the browser and sends the HTTP request to the requested site.
![Authenticating Users Diagram](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/about-zscaler-authentication-bridge/ZIA-Authenticating-Users-Diagram-for-About-the-Zscaler-Authentication-Bridge%20(1).png)
About the Authentication Bridges Page
You must have a ZAB subscription to view the Authentication Bridges page.
On the Authentication Bridges page (Administration > Authentication Settings > Authentication Bridges), you can do the following:
- [Add a ZAB.](/zia/how-do-i-add-zscaler-authentication-bridge)
- [Download the ZAB virtual machine.](/zia/downloading-zscaler-authentication-bridge-vm)
- Search for a configured ZAB.
- View a list of configured ZABs. For each ZAB, you can view the following information:
- **Name**: The name of the ZAB.
- **Status**: The status of the ZAB (Enabled or Disabled).
- **SSL Certificate**: Download option to download the ZAB's SSL certificate.
- Download the SSL certificate for the ZAB. The ZAB uses this certificate to authenticate itself to the Zscaler service.
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- [Edit the configured ZAB.](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal)
![Zscaler Authentication Bridge Page ](/downloads/zia/authentication-administration/user-management-authentication-settings/zscaler-authentication-bridge/about-zscaler-authentication-bridge/ZIA-6.2r-Authentication%20Bridge-page%20(1).png)