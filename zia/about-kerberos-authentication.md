# About Kerberos Authentication
Source: https://help.zscaler.com/zia/about-kerberos-authentication
PDF: https://help.zscaler.com/pdf/com/en/1399556.pdf

Zscaler supports authentication using Kerberos, an industry standard secure protocol. Unlike the other supported authentication mechanisms, Kerberos doesn't use cookies for authentication. It is a ticket-based authentication protocol that is widely used to authenticate users to network services. To learn more about the Kerberos protocol, see [RFC 4120 The Kerberos Network Authentication Service (V5)](https://tools.ietf.org/html/rfc4120).
How Kerberos Authentication Works With Zscaler
The Zscaler service uses Kerberos cross-realm authentication, enabling clients from your organization’s domain to authenticate themselves to the ZIA Public Service Edges in the Zscaler domain. Your organization and the Zscaler domain establish a one-way trust relationship based on a shared password, eliminating the need to upload and manage keytab files or to join the ZIA Public Service Edges to your domain.
The following diagram shows a simplified view of the authentication process after the trust relationship is established. Review the following:
- In the organization's domain, the Kerberos Key Distribution Center (KDC) is integrated in the domain controller on the Windows server.
- In the Zscaler domain, the Central Authority (CA) hosts the KDC.
- The user is logged in to the corporate domain.
- The user's browser used the default Kerberos PAC file to identify the primary ZIA Public Service Edge.
![About Kerberos Diagram](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-kerberos-authentication-draft/zia-about-kerberos-diagram.png)
- The user's browser sends the request to the ZIA Public Service Edge. (HTTPS requests are also sent as HTTP CONNECT method requests to the ZIA Public Service Edge.) If the ZIA Public Service Edge doesn't find a Zscaler cookie for the domain in the HTTP request, it issues a 407 Negotiate challenge.
-
Because the user has already logged into the domain, the user has a session ticket for the domain controller. Using this session ticket, the client sends the domain controller an authentication request for the Zscaler service. The domain controller issues a cross-realm ticket.
[See image.](#seeimage)
- The client sends the cross-realm ticket to Zscaler KDC, which issues a ticket for the ZIA Public Service Edge.
- The client sends the HTTP request with the proxy authorization header and ticket, which contains the client information. The ZIA Public Service Edge decrypts the ticket, and after verifying the username, sends the request to the website.
As shown in the diagram, users authenticate themselves only once when they log in to the corporate domain. They don't need to log in separately to the Zscaler service. Additionally, the Zscaler service is able to identify users through the proxy authorization header. This allows the service to then apply user, group, and department policies on FTP and HTTPS transactions without decrypting them.
Kerberos Authentication Overview
You can review the features, benefits, requirements, and limitations for your organization:
- [Features](#kerberos-features)
- [Benefits](#kerberos-benefits)
- [Requirements](#kerberos-requirements)
- [Limitations](#kerberos-limitations)
Before deploying Kerberos, see [Kerberos Deployment Guidelines](/zia/kerberos-deployment-guidelines). To deploy Kerberos, see [Deploying Kerberos](/zia/how-do-i-deploy-kerberos).
[]Using Kerberos to authenticate users provides the following benefits:
- It enables the Zscaler service to authenticate users when they use applications that do not support cookies, such as Office 365 and Windows Metro apps.
- It enables transparent Single Sign-On (SSO) authentication for users. Users authenticate themselves once, when they log in to their corporate domain. They do not need to explicitly authenticate to the Zscaler service, because authentication occurs transparently with Kerberos.
- The service can enforce granular user, group, and department policies on proxied FTP transactions as well as HTTPS transactions, without having to decrypt the HTTPS transactions.
- Your organization doesn't need to configure its firewall to allow incoming connections from ZIA Public Service Edges.
- Kerberos is a secure, open standard protocol that most operating systems support, including Windows 7, Windows 8, OS X, Linux, and FreeBSD. Additionally, most browsers support Kerberos authentication, including Internet Explorer, Firefox, and Safari.
[]The Zscaler Kerberos implementation provides the following features:
- It is simple to configure and manage. Your organization and the Zscaler service establish a one-way trust that is based on a shared password, eliminating the need to upload and manage keytab files or to join the ZIA Public Service Edges to your domain.
- It offers various deployment options. Your organization can use Kerberos as its sole authentication method or combine it with another method, such as SAML or LDAP. To learn more, see [Kerberos Deployment Guidelines](/zia/kerberos-deployment-guidelines#Kerberos-Deployment-Options).
- It can be used to authenticate road warriors as well. DirectAccess is required (To learn more, see [Kerberos Deployment Guidelines](/zia/kerberos-deployment-guidelines#Kerberos-Deployment-Options)).
[]The Zscaler service doesn't support Kerberos on Windows XP, Apple iOS, or Android devices.
[]To use Kerberos as an authentication mechanism, your organization must do the following:
- Provision users on the Zscaler service. Kerberos is an authentication mechanism. It is not a provisioning method, like [SAML](/zia/configuring-saml) or [LDAP synchronization](/zia/configuring-zscaler-service-synchronize-data). Users must be provisioned on the Zscaler service before they can use Kerberos for authentication. For supported provisioning methods, see [About Provisioning and Authentication Methods](/zia/choosing-provisioning-and-authentication-methods).
- Use a [PAC file](/zia/how-do-i-use-default-pac-files-forward-traffic-zia) to forward traffic to the Zscaler service.
The service supports Kerberos authentication only for traffic forwarded in explicit mode. It doesn't support Kerberos for traffic forwarded in transparent mode, which is traffic forwarded through a [GRE](/zia/configuring-gre-tunnels) or [IPSec](/zia/how-do-i-configure-ipsec-vpn-tunnels) tunnel and the browser isn't configured to use a PAC file to forward traffic. To learn more, see [Using the Default Zscaler Kerberos PAC File](/zia/using-default-zscaler-kerberos-pac-file).
- Ensure that the DNS server on site can resolve the Zscaler service host names (Zscaler PAC servers; Central Authority, which hosts the Zscaler Key Distribution Center (KDC); and ZIA Public Service Edges). If this isn't possible from the location, then your organization must conditionally forward Zscaler cloud domain resolution to the Zscaler DNS servers.
- Ensure that your firewall allows connections to port 88/8800 in order to allow Kerberos authentication to work.
- Ensure that the domain suffix of either the client or server, in the Kerberos ticket obtained from your organization's domain controller, is a registered domain in the Zscaler account. In the example below, the domain suffix is SAFEMARCH.COM. To see the Kerberos tickets, open Windows PowerShell and run the command klist.
[See image.](#seeimage1)
Additionally, the following are required in a Windows environment:
- A domain controller that runs Windows Server 2008 or higher
- Client devices must run Windows Vista or higher
- Client devices must be joined to the domain
[]![Screenshot of the authentication request](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/how-does-zscaler-kerberos-authentication-work/authentication_request.png)
[]![Screenshot of the klist command and the Kerberos ticket in Windows PowerShell](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/kerberos-requirements/klist_command_&_kerberos_ticket_in_windows_powershell.png)