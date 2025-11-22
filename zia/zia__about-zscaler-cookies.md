# About Zscaler Cookies
Source: https://help.zscaler.com/zia/about-zscaler-cookies
PDF: https://help.zscaler.com/pdf/com/en/1399511.pdf

The Zscaler service uses cookies to determine whether a user has been authenticated. A cookie is a text file that is set by a website and stored by a user's web browser on the local disk for future use. Websites use cookies for a number of reasons, including user authentication, internet activity tracking, or session information storage (so the website can show relevant content in the future).
The Zscaler service uses the following types of cookies:
- **Gateway cookie**: This cookie contains a string that provides login information, including if the user is logged in to the Zscaler service and the number of times the user logged in.
- **Domain cookie**: After a user logs in to the Zscaler service, the service sets an additional cookie for each domain to which a user browses. This enables the service to identify which domains a user has visited, so it won’t require the user to log in again. This cookie is set by the ZIA Public Service Edge.
- **Acceptable Usage Policy (AUP) cookie**: The Zscaler service sets this cookie when a user accepts the AUP. This cookie is set by the ZIA Public Service Edge.
The service needs to authenticate users only once to set the gateway cookie. However, you can require users to [authenticate more often](/zia/about-authentication-profile#authentication-frequency) based on your organization's needs.
Zscaler service marks the following user traffic against their location instead of the user due to the absence of authentication cookies:
- All the CONNECT method requests.
- Requests from UNKNOWN user agents that do not support cookies.
- Traffic destined to globally exempted websites, i.e. all the websites that are included in the Exempted URL Categories.
- Traffic destined to locally exempted websites, i.e. all the websites that are included in the Exempted URLs list.
- SSL traffic that is not decrypted.