# About Applying Policies for Authenticated Guest Users
Source: https://help.zscaler.com/unified/about-applying-policies-authenticated-guest-users
PDF: https://help.zscaler.com/pdf/com/en/1494601.pdf

In general, policies are applied to authenticated traffic, regardless of location. If the traffic to the Zscaler service is from an authenticated user, the policies you configure are applied.
For example two companies, Host Corp. and Guest Inc., both use the Zscaler service. An employee from Guest Inc. visits the Host Corp. site and the Guest traffic is tunneled to the Zscaler service via either a [PAC file](/unified/understanding-pac-files) or the Zscaler Client Connector.
If the Guest Inc. user is authenticated:
- All of the Guest Inc. user's URL, Cloud App, firewall, Data Loss Prevention (DLP), and security policies are applied to that authenticated traffic.
- All transactions are logged against the Guest user.
- If the Guest user has an [Acceptable Use Policy (AUP)](/unified/configuring-end-user-notifications) configured, it is displayed after authentication.
- The Guest user cannot use the Guest DPPC port.
- All Host Corp. bandwidth limitations apply.
- All Host Corp. SSL and authentication bypasses apply.
- If Host Corp. has [SSL Interception enabled](/unified/deploying-ssl-inspection) at the location, then Guest user traffic is intercepted and decrypted using the Host Corp. SSL certificate.
However, if Host Corp. has authentication disabled at the location, the Guest user cannot be authenticated. If the Guest Inc. user cannot be authenticated for any reason:
- All of the Host Corp's URL, Cloud App, firewall, DLP, and security policies are applied to that unauthenticated traffic.
- All unauthenticated transactions are logged against Host Corp.
- If the Guest user has [AUP](/unified/configuring-end-user-notifications) configured, it is not displayed because the user is not authenticated.
- The Guest user cannot use the Guest DPPC port.
- All Host Corp. bandwidth limitations apply.
- All Host Corp. SSL and authentication bypasses apply.
- If Host Corp. has [SSL Interception enabled](/unified/deploying-ssl-inspection) at the location, then Guest user traffic is intercepted and decrypted using the Host Corp. SSL certificate.