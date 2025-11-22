# Using the Default Zscaler Kerberos PAC File
Source: https://help.zscaler.com/unified/using-default-zscaler-kerberos-pac-file
PDF: https://help.zscaler.com/pdf/com/en/1493511.pdf

All users who leverage Kerberos for authentication must configure their browsers to use PAC files to forward their traffic to the Zscaler service, even if their location has established an IPSec or VPN tunnel to forward traffic to the service.
Zscaler provides a default Kerberos PAC file. Following is information and tips about using the Keberos PAC file:
- Kerberos requires that the Internet & SaaS Public Service Edges be addressed as Fully Qualified Domain Names (FQDNs). To accommodate this requirement, the Kerberos PAC file contains the variables ${GATEWAY_HOST} and ${SECONDARY_GATEWAY_HOST}, which the service substitutes with the domain names of the primary and secondary Internet & SaaS Public Service Edges.
- It forwards web traffic to port 8800 of the Internet & SaaS Public Service Edge. Internet & SaaS Public Service Edges challenge all traffic that it receives on port 8800 for a Negotiate Authentication (Kerberos) ticket for the Zscaler service.
-
If your organization has a KDC proxy (with Microsoft DirectAccess) deployed for road warrior access, the KDC proxy traffic is also sent to the Internet & SaaS Public Service Edge, resulting in authentication failure. Therefore, you must create a new PAC file that includes a line to bypass the KDC proxy:
if shExpMatch(host,"kdcproxy.domain.com") return "DIRECT";
- Don't forward traffic destined within the realm to the Zscaler service, so the Internet & SaaS Public Service Edge does not challenge any traffic within the realm. Create a new PAC file that includes a line to bypass your organization's realm.
- If the location has Kerberos enabled, then traffic can be forwarded to the proxy ports (80, 443, 9400, 9443) or to the dedicated port associated with that location. The service automatically challenges all explicitly forwarded proxy traffic from that location for a Kerberos ticket for the Zscaler domain.
Zscaler strongly recommends that you either use the Zscaler Kerberos PAC file or copy and paste it to a new PAC file and then add any necessary arguments and exceptions.
Before deploying Kerberos authentication, see [Kerberos Deployment Guidelines](/unified/kerberos-authentication-deployment-guidelines) and [Kerberos Requirements](/unified/about-kerberos-authentication#kerberos-requirements). To learn how to deploy Kerberos, see [Deploying Kerberos Authentication](/unified/deploying-kerberos-authentication).
Using the Default Zscaler Kerberos PAC File
To use the default Kerberos PAC file hosted by the Zscaler service:
- Go to **Infrastructure **> **Internet & SaaS** > **Traffic Forwarding** > **Traffic Steering** >** Hosted PAC Files**.
- Copy the **Hosted URL** of the default Kerberos PAC file.
[See image.](#kerberos-pac)
- [Distribute the Keberos PAC file URL to your users.](/unified/distributing-pac-file-url-users)
[]![Screenshot of the default Kerberos PAC file on the Hosted PAC Files page](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/kerberos/kerberos-deployment-guide/how-do-i-use-zscaler-kerberos-default-pac-file/default_kerberos_pac_file_on_the_hosted_pac_files_page.png)