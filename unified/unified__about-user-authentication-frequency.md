# About User Authentication Frequency
Source: https://help.zscaler.com/unified/about-user-authentication-frequency
PDF: https://help.zscaler.com/pdf/com/en/1491621.pdf

Zscaler offers multiple options for how often users are required to authenticate to the Zscaler service. The authentication frequency options are:
- Daily
- Only Once
- Once Per Session
- Custom
These options don't apply to users with the Zscaler Client Connector feature.
To learn more about these options and how to configure them, see [About Authentication Default Settings](/unified/about-authentication-default-settings).
Zscaler recommends that you choose **Only Once** as your authentication frequency. This is the default authentication interval. Choosing **Only Once **as the authentication frequency** **allows for a seamless experience for the end user. The Zscaler service only needs to authenticate users once to set the cookie. Once users have logged in, they do not need to authenticate again as long as the cookie is saved in the browser. Typically, the cookie expires in about two years. However, to log out of Zscaler, users must log out of the service explicitly or delete the cookie from their browser.
See below for information regarding concerns you might have when choosing **Only Once **as your authentication frequency.
Security Concerns
The following information addresses security concerns when setting the authentication frequency to only once.
Zscaler Authentication Cookies
The Zscaler service uses cookies to determine if a user has been authenticated. To learn more about the types of cookies the Zscaler service uses, see [About Zscaler Cookies](/unified/about-zscaler-cookies).
Zscaler issues an authentication cookie encrypted with SSL for the gateway cloud; therefore, that cookie can only be set and read from the gateway SSL site. It also can't be sniffed on the network. When a user browses a website, the proxy can only get cookies from that website. It issues a redirect to the gateway to fetch the cookie, and then validates it. If the gateway cookie is valid, the proxy generates a new domain cookie for that website and issues a redirect to it. So the cookie, for the website to which the user browsed, provides the user identity for the Zscaler proxy. This domain cookie is rotated every 12 hours.
If a user steals a domain cookie, that user can browse the Internet through Zscaler to that website for up to 12 hours maximum. They cannot browse to another website if they do not have the gateway SSL cookie and the cookie generation algorithm for domain cookies.
Stolen Device & User Termination
If the user's device is stolen, the culprit can use it to browse the Internet through Zscaler as that user. Alternatively, if a user is terminated, but has authenticated to the Zscaler service on a personal device, then that user can browse the Internet through Zscaler. However, this is not a security issue because the Zscaler cookie does not give access to any privileged resources. The culprit may first try to disable the Zscaler traffic redirection because all of their actions on the stolen device are logged.
Zscaler Private Application and Zscaler Client Connector features do not use cookies for authentication. This is the recommended mechanism for companies that use Private Applications or use Zscaler as an identity proxy.
Active Directory Server Reliability and Scalability
The following information addresses the Active Directory (AD) server reliability and scalability when setting the authentication frequency to more than once.
Authenticating More Than Once
If you choose **Only Once **as the authentication frequency, authentication is completely transparent to your end users during maintenance or a downtime window of your AD server. If you choose an authentication frequency that requires users to authenticate to the Zscaler service more than once, your users are authenticated against your AD server on a regular basis. For example, if you choose **Daily** as the authentication frequency, all of your users must authenticate themselves against the AD server every day when they access the internet. You must ensure that your server can scale to service these requests.
Updating Information
The following information addresses information updates when setting the authentication frequency to more than once.
Adding, Updating, and Deactivating Users & Groups
[User information](/unified/about-users) and [group information](/unified/about-groups) is updated when either a user is authenticated or the Zscaler server synchronizes data from the directory server.
If you choose **Only Once** as the authentication frequency, user and group information is only updated when synchronization is performed. If you do not synchronize the information with a directory server, you can either add and delete users manually, update the group information, or modify the group in the Admin Portal.
Zscaler also exposes the API to update the information via third-party IdP vendors, such as Okta.