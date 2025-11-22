# What Is My Cloud Name for ZDX?
Source: https://help.zscaler.com/zdx/what-my-cloud-name-zdx
PDF: https://help.zscaler.com/pdf/com/en/1479516.pdf

To maximize operational efficiency, Zscaler built a highly scalable, global multi-cloud infrastructure for ZDX. An organization is provisioned on one cloud and its traffic is processed by that cloud only.
Some configurations of the Zscaler service require that you specify the name of the cloud on which your organization is provisioned. For example, it is needed when you [configure SAML for admin single sign-on (SSO)](/zdx/configuring-saml-zdx-admins) for the Zscaler service.
You can find the name of the cloud in the URL that admins use to log in to the Zscaler service.
If an organization logs into admin.zdxcloud.net, then that organization's cloud name is zdxcloud.net.
![ZDXCloud](/downloads/zdx/getting-started/admin-portal/what-my-cloud-name-zdx/zdx-zdxcloud.png)
The ZDX API Portal URL depends on your organization’s assigned cloud. If an organization logs in to admin.zdxcloud.net, then the ZDX API Portal for that organization’s cloud name is api.zdxcloud.net.