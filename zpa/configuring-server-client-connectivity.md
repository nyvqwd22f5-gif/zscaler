# Configuring Server-to-Client Connectivity
Source: https://help.zscaler.com/zpa/configuring-server-client-connectivity
PDF: https://help.zscaler.com/pdf/com/en/1485586.pdf

Server-to-client connectivity allows an admin to connect to an end user's device to troubleshoot, provide remote assistance, or push software updates. To use this in Zscaler Private Access (ZPA), complete the following steps.
To enable server-to-client connectivity:
- Deploy a Zscaler Cloud Connector or Branch Connector. To learn more, see [Zscaler Cloud & Branch Connector Help](/cloud-branch-connector/getting-started).
Check with your Zscaler Account team to confirm your license for Cloud Connector or Branch Connector.
- If you are deploying Branch or Cloud Connector specifically for *server-to-client connectivity through an FQDN*, Zscaler recommends you configure conditional DNS forwarding so only the DNS requests from the applications requiring server-to-client connections are forwarded to the Branch or Cloud Connector. To learn more, see [Zscaler Cloud and Branch Connector Help](/cloud-branch-connector/getting-started).
- If you are using Zscaler IP-based connectivity, point the IP gateway from those servers to the Branch or Cloud Connector's service IP.
- For Windows devices, enter the following command and check that it is applied using the `route print` command:
route add 0.0.0.0 mask 0.0.0.0 <Branch or Cloud Connector service IP address> metric 30 if 2
For example:
route add 0.0.0.0 mask 0.0.0.0 10.66.36.132 metric 30 if 2
- For Linux devices, enter the following command and check that it is applied using the `route -n` command:
sudo route add default gw <Branch or Cloud Connector Service IP address>
For example:
sudo route add default gw 10.66.36.132
- Ensure the destination device is running versions Zscaler Client Connector 4.2 for Windows or later. ZPA must be enabled and turned on, with a user logged in, on the destination machine. To learn more, see [Configuring Update Settings for Zscaler Client Connector](/client-connector/configuring-update-settings-zscaler-client-connector).
- Configure and [validate a client hostname](/zpa/validating-client-hostname) to enroll endpoints and accept the incoming connections.
- If you are using Zscaler IP-based connectivity, create a virtual IP range that is assigned to Zscaler Client Connector as a Zscaler IP. This IP range must be non-overlapping. To learn more, see [About Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment).
- Create application segments that include the Zscaler IP of the clients for an IP-based connection, or FQDNs of the clients for a FQDN-based connection. To learn more, see [Configuring Recommended Application Segments](/zpa/configuring-recommended-application-segments).
If you have the same namespace for both your applications and workstations, Zscaler recommends creating different application segments for client-based remote assistance and for application access, with separate FQDNs or wildcard subdomains if possible. Alternatively, you can use the Zscaler IP-based connectivity and create the Zscaler IP-based application segments.
- Create or update an existing policy to control which servers can connect to the existing remote users. Add additional criteria to your access policy if you want more granular access control. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies) and [Editing Access Policies](/zpa/editing-access-policies).
If access policies are not created or updated for the server-to-client connection, then any user in their organization can use this feature to connect to any endpoints enrolled in this feature within their organization.
For Microsoft Remote Assistance (MSRA) with Zscaler IP-based connectivity, the following changes must be made in the invitation file by the destination user:
- Remove the `LHTICKET` attribute.
- Replace the IP address for the `RCTICKET` value with the [Zscaler IP](/zpa/about-client-connector-ip-assignment). The following is an example `RCTICKET` value with the Zscaler IP:
<UPLOADINFO TYPE=“Escalated”><UPLOADDATA USERNAME=“Zscaler”
RCTICKET=“65538”, 1, 192.168.1.1:54606;100.64.0.2:54607,*,wmLNc8PLK1/q4ypjbU9+4PLWONEe6TKayN0ISF79EXdW+41xqXATVZDwGAQJcbrf…
After making the connection, confirm that the server-to-client connection is enabled successfully by checking the following:
- Zscaler Client Connector endpoints were accessed.
[See image.](#endpointVerification)
- The data in the [user activity diagnostics](/zpa/about-user-activity-diagnostics#filters) and [live logs](/zpa/accessing-live-logs) show the value **Client to Client **for the **Access Type** field.[]
[]![Client Connector verification of server-to-client endpoints](/downloads/zpa/administration/peer-peer-connectivity/configuring-server-client-connectivity/zcc-server-to-client-successful-verification2.png)