# End-of-Support for Adobe Flash Cookies
Source: https://help.zscaler.com/eos-eol/end-support-adobe-flash-cookies
PDF: https://help.zscaler.com/pdf/com/en/1269016.pdf

In our continuing effort to provide the highest level of security to our users, Zscaler is discontinuing its use of Adobe Flash cookies on its authentication pages and pre-provisioned cookies as an authentication mechanism. This is due to security concerns around the vulnerabilities of Adobe Flash cookies.
Determine If You Are Using Adobe Flash Cookies
You are using Adobe Flash cookies if you downloaded cookies from https://admin.<Zscaler Cloud Name>/download/cookies and distributed them to your users’ devices. To find your Zscaler cloud name, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
What to Do
If you are using Adobe Flash cookies for authentication, ensure that another authentication mechanism is configured on the Authentication Settings page of the ZIA Admin Portal. Zscaler recommends deploying Identity Federation using SAML for provisioning and authentication. To learn more, see [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-and-authentication-methods).
You can also deploy the Zscaler Client Connector to your users with no additional charge. The Zscaler Client Connector provides all of the benefits of the Zscaler Cloud Security Platform for internet traffic, and requires users to log in just once. To learn more, see [What is the Zscaler Client Connector?](/zia/what-zscaler-app)
If you do not configure an authentication mechanism before Zscaler ends its support for Adobe Flash cookies, the Zscaler service will use the authentication mechanism that is already configured on the ZIA Admin Portal to authenticate users.
Additionally, Zscaler strongly recommends that you inform your users about the new authentication process, because the Adobe Flash cookies allowed them to skip the authentication step. With the new authentication mechanism, users will need to authenticate themselves to the Zscaler service at least once.
Change Timing
Zscaler discontinued its support for Adobe Flash cookies in the 5.5 release.
Additional Information
If you need help changing your configuration or if you have additional questions or concerns, contact Zscaler Support via the Support link in the ZIA Admin Portal.
Announcement date: August 14, 2017