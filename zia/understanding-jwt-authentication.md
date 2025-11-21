# Understanding JWT Authentication
Source: https://help.zscaler.com/zia/understanding-jwt-authentication
PDF: https://help.zscaler.com/pdf/com/en/1530875.pdf

Zscaler supports JSON Web Token (JWT) authentication for cloud workloads. JWTs generated for cloud workloads are authenticated by token validators configured in the ZIdentity Admin Portal.
JWT authentication can be enabled when [configuring locations](/zia/configuring-locations). You can also bypass JWT authentication on the [Advanced Settings page](/zia/configuring-advanced-settings). Token validators are configured in the ZIdentity Admin Portal.
Sessions that include JWT authentication are logged in the [Insights Logs](/zia/about-insights-logs) with the user ID from the JWT.
JWT authentication is not enabled by default. To access this feature, submit a provisioning ticket to [Zscaler Support](/submit-ticket-links).
How JWT Authentication Works with Zscaler
The following diagram provides an overview of the JWT authentication flow with Zscaler:
- The workload requests a JWT from the token provider.
- After the workload receives the JWT, the workload sends a request along with the JWT through Zscaler Cloud & Branch Connector or GRE and IPSec tunnels.
- The Zscaler service checks the JWT against the token validators configured in the ZIdentity Admin Portal and authenticates it if the token is validated.
- The traffic proceeds to its destination and a 200 OK verification code is sent back to the client and Zscaler service.
![Traffic flow for JWT authentication](/downloads/zia/authentication-administration/user-management-authentication-settings/jwt-authentication/understanding-jwt-authentication/ZIA-jwt-auth-flow-diagram.png)