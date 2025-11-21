# SAML & SCIM Configuration Guide for PingFederate
Source: https://help.zscaler.com/zia/saml-scim-configuration-guide-pingfederate
PDF: https://help.zscaler.com/pdf/com/en/1401201.pdf

This guide illustrates how to configure Ping Identity's PingFederate server as the identity provider (IdP) for the Zscaler service.
Zscaler and Ping Identity are technology partners. To learn more about the Zscaler and PingFederate integration, see the [Zscaler and Ping Identity Deployment Guide](/zscaler-technology-partners/zscaler-and-pingone-deployment-guide).
Prerequisites
Ensure that you have the following before you start configuring PingFederate as your IdP:
- PingFederate server with the Zscaler Connector add-on
- PingFederate admin account
- [Zscaler cloud name](/zia/what-my-cloud-name)
Configuring PingFederate as the IdP for the Zscaler service
To configure SAML Single Sign-On (SSO) and SCIM Provisioning with Zscaler and PingFederate, see the [PingFederate documentation](https://docs.pingidentity.com/r/en-us/pingfederate-zscaler-zia-connector/pingfederate_zscaler_zia_connector).
Testing the SAML and SCIM Configuration
[]When your configuration is complete, you can test your work on another device.
Test the configuration with one or both of the following methods:
- [Test the SAML Configuration by Logging Out of the Zscaler Service](#test-saml-1)
- [Test the SAML Configuration with the Test URL](#test-saml-2)
To test the SCIM configuration, in the ZIA Admin Portal, go to **Administration** >** User Management**. You should see a complete list of the users and groups added to your user database.
Troubleshooting
If any errors occur, see [Troubleshooting SAML](/zia/saml-troubleshooting-guidelines) to troubleshoot browser settings and SAML error codes.
[]This testing method only applies if you're forwarding traffic using Proxy Auto-Configuration (PAC) files, Generic Routing Encapsulation (GRE) tunnels, or IPSec tunnels, and you've enabled Enforce Authentication for the location or sublocation.
- On the device, browse to [ip.zscaler.com](http://ip.zscaler.com).
- If you are already logged in to the Zscaler service, click **Logout**. Otherwise, ensure that your traffic is being forwarded to the Zscaler service.
- Browse to a website. You are redirected to PingFederate and prompted to log in.
- Log in using your PingFederate credentials, and you are automatically redirected to the original URL request.
- Go to [ip.zscaler.com](http://ip.zscaler.com). The status window shows the username indicating that authentication was successful.
-
[]On the device, enter `https://login.``<Zscaler Cloud Name>``/clstart?version=1&_domain=``<Tenant Domain>``&redrurl=https://mobile.``<Zscaler Cloud Name>`. To learn how you can find your cloud name, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia) The <Tenant Domain> is your organization's domain that is used to log in to the Zscaler service. For example, if you logged in to the Zscaler service with the username `admin@``zscaler.com`, then zscaler.com is your <Tenant Domain>.
Given an organization on the `zscalerbeta.net` cloud with `zscaler.com` as the <Tenant Domain>, the completed URL would be:
``https://login.``zscalerbeta.net``/clstart?version=1&_domain=``zscaler.com``&redrurl=https://mobile.``zscalerbeta.net``
- If you are redirected to the ZIA Admin Portal, the SAML configuration is successful. You might be prompted to authenticate with your IdP.