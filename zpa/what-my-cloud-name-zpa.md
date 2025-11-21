# What Is My Cloud Name for ZPA?
Source: https://help.zscaler.com/zpa/what-my-cloud-name-zpa
PDF: https://help.zscaler.com/pdf/com/en/1485806.pdf

To maximize operational efficiency, Zscaler built a highly scalable, global multi-cloud infrastructure for ZPA. An organization is provisioned on one cloud and its traffic is processed by that cloud only.
Some configurations of the Zscaler service require that you specify the name of the cloud on which your organization is provisioned. For example, it is needed when you [configure SAML for admin single sign-on (SSO)](/zia/configuring-saml-admins) for the Zscaler service.
You can find the name of the cloud in the URL that admins use to log in to the Zscaler service.
If an organization logs into admin.private.zscaler.com, then that organization's cloud name is private.zscaler.com.
![Zscaler ZPA private cloud name](/downloads/zpa/getting-started/admin-portal/what-my-cloud-name-zpa/adminprivate%20https.png)
If an organization logs into admin.zpatwo.net, then that organization's cloud name is zpatwo.net.
![Zscaler zpatwo cloud name](/downloads/zpa/getting-started/admin-portal/what-my-cloud-name-zpa/zpatwohttps.png)
The ZPA API Portal URL on the [API Keys](/zpa/about-api-keys) page (Configuration & Control > Public API) differs depending on your organization’s assigned cloud. If an organization logs in to admin.private.zscaler.com, then the ZPA API Portal for that organization’s cloud name is config.private.zscaler.com. If an organization logs in to zpatwo.net, then the ZPA API Portal for that organization’s cloud name is config.zpatwo.net.