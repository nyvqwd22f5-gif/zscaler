# SAML Configuration Guide for CA Single Sign-On
Source: https://help.zscaler.com/zia/saml-configuration-guide-ca-single-sign-on
PDF: https://help.zscaler.com/pdf/com/en/1399661.pdf

This guide illustrates how to configure CA SiteMinder running version of R12 SP3 CR5 as the Identity Provider (IdP) for the Zscaler service.
If you are using CA SiteMinder r12.0 SP2 or the initial release of r12.0 SP3 (prior to CR1), download and deploy an assertion generator plug-in (AGP).
Consider the following before configuring CA Single Sign-On (SSO) (formerly CA SiteMinder) as the IdP for the Zscaler service:
- You might not be able to use the default CA SSO SAML portal URL. A critical piece of information (RelayState) is dropped from the URL and the functionality fails. This is resolved by using the “Redirect script”.
- There is a bug in CA SSO where it provides the multiple values Group data in an invalid format/syntax that Zscaler can't use. This is resolved by using the latest release/patches from CA SSO and a special formatting function that was introduced in the latest release/patches.
- Zscaler expects a POST Binding which isn't the default for CA SSO.
Prerequisites
Ensure that you have the following before you start configuring CA SSO as the IdP:
- The Zscaler CA SSO redirect JSP. There are several versions of this script but they all have the basic function of redirecting the request and appending the “RelayState”. Some scripts also include more error handling but therefore may require more customization/changes to match the specific environment. Following is the simplest version of the JSP:
<% String msg = (String)request.getParameter("RelayState");
String redirectURL = "http://original.example.com/affwebservices/public/saml2sso?SPID=staging.<Zscaler Cloud Name>.saml2&ProtocolBinding=urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST&RelayState="+msg;response.sendRedirect(redirectURL);
%>
Ensure this file is included in the WAR file so that it is included in any reboot/reload/restart.
- The original CA SSO URL of the SAML portal, which users are sent for authentication.
Configuring CA SSO as the IdP for the Zscaler Service
To configure CA SSO as the IdP for the Zscaler Service:
- [1. Configure CA SSO as the IdP](#ca-siteminder)
- [2. Configure the CA SSO SAML Service Provider Properties](#siteminder-saml-properties)
- [3. Add CA SSO as the IdP for the Zscaler Service](/zia/adding-identity-providers)
- [4. Configure SAML SSO in the ZIA Admin Portal](#zscaler-admin-portal)
- [5. Configure the Zscaler Authentication Exemptions List](#authentication-exemptions)
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]To configure CA SSO as the IdP:
- Edit the Zscaler provided redirect script. Replace the URL in the redirectURL attribute with the original URL from CA SSO. Also, replace <Zscaler Cloud Name> with the name of the cloud, which your organization is provisioned on. To learn how you can find your cloud name, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia) Leave all the additional variables in the string.
“&RelayState=”+msg;”.
String redirectURL = “http://securenet.example.com/affwebservices/public/saml2sso?SPID=staging.<Zscaler Cloud Name>.saml2&ProtocolBinding=urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST&RelayState="+msg;
- Save the JSP file.
- Deploy this file to the company website where the current SAML SSO URL is hosted.
[]The Zscaler service requires the username (JohnSmith@safemarch.com), given name (John Smith), and member-of-Groups (Browsing-group1, Browsing-Group2). The Active Directory attributes will be samaccountname or email, givenname and memberOf. The key to handling Groups is to use the FMATTR function as shown below.
![Screenshot showing an example of the FMATTR function](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/saml/saml-configuration-guide/saml-configuration-example-siteminder/fmattr_function.png)
[]To configure SAML SSO in the ZIA Admin Portal:
- Go to **Administration**** **>** Authentication Settings**.
- Under **Authentication Frequency**,** **choose how often users are required to authenticate to the Zscaler service. To learn more, see [About Authentication Profile](/zia/about-authentication-profile#authentication-frequency). If you select **Custom**, the following field will appear:
- **Custom Authentication Frequency (days)**: Specify 1 to 180 days.
- Under** Authentication Type**, choose **SAML**.
[See image.](#seeimage-2c)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot highlighting the SAML option under Authentication Type on the Authentication Profile page.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/configuring-saml/ZIA-Authentication-Profile-Authentication-Type.png)
[]Enter the redirected URL to the [PAC file](/zia/how-do-i-use-default-pac-files-forward-traffic-zia) exemption list. Otherwise, authentication will fail. This is due to the browser trying to reach the authentication URL via the Zscaler service and the current user isn't yet authorized to use the Zscaler service, so the request never passes through the service.
If (dnsDomainIs(host, "securenet.com") )
return "DIRECT";