# Understanding Basic Authentication
Source: https://help.zscaler.com/zia/understanding-basic-authentication
PDF: https://help.zscaler.com/pdf/com/en/1498526.pdf

Zscaler supports Basic authentication, a simple authentication scheme built into the HTML protocol. Basic authentication prompts users for a username and password, which are sent as a Base64 encoded string in the HTTP request header.
Basic authentication is not enabled by default. To access this feature, submit a support ticket from your Admin Portal.
How Basic Authentication Works with Zscaler
The following diagram provides an overview of the Basic authentication flow with Zscaler:
![Basic Authentication Flow](/downloads/zia/authentication-administration/user-management-authentication-settings/basic-authentication/about-basic-authentication/ZIA-Basic-Auth-Flow.png)
- The client sends a request along with the authentication credentials of its corresponding user enrolled with Zscaler.
- A ZIA Public Service Edge calculates the HA1 value for the given credentials and authenticates the user upon successful validation.
- The traffic proceeds to its destination and a 200 OK verification code is sent back to the Zscaler service and client.
Basic Authentication Overview
Basic authentication can be integrated with the following Zscaler workflows:
- [User Enrollment](#user-enrollment)
- [Authenticating Traffic](#authenticating-traffic)
[]Basic authentication works with an HA1 value that must be initialized. Therefore, users need to be enrolled to the ZIA Admin Portal via API. This is necessary because Basic authentication is often used for workloads, which may not be able to interactively perform user enrollment on a browser.
For more information about user enrollment, see [Deploying Basic Authentication](/zia/deploying-basic-authentication).
[]After users are enrolled, they may browse the internet through a ZIA proxy and one of several forwarding proxy methods such as Static IP, DPCC, ZIA Virtual Service Edge, or with transparent proxy such as GRE and VPN. User traffic from [locations](/zia/about-locations) can be configured for Basic authentication and the desired forwarding method.