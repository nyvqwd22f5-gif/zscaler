# Using Application Segment Multimatch
Source: https://help.zscaler.com/unified/using-application-segment-multimatch
PDF: https://help.zscaler.com/pdf/com/en/1492226.pdf

Multimatch allows an application request to match multiple application segments. When a user tries to access a private application without Multimatch, a request is mapped to an application segment. After the application is mapped to an application segment, the [policy](/unified/about-access-policy) search is performed, and the request is either allowed or blocked based on the policy configuration.
To learn more, see [About Access Policy](/unified/about-access-policy) and [Configuring Access Policies.](/unified/configuring-access-policies)
Prerequisites
To use application segment Multimatch, ensure the following:
- App Connectors or Private Service Edges for Private Applications are upgraded to version 24.298.1 or later.
-
Zscaler Client Connector is upgraded to the following versions per OS:
- Windows versions:
- 4.5.0.337 or later
- 4.4.0.379 or later
- 4.3.0.261 or later
- macOS versions:
- 4.3.1.59 or later
- 4.3.0.240 or later
Multimatch is only supported for Windows and macOS.
Using Multimatch
By default, after a specific FQDN is configured in an application segment, the destination is removed from the wildcard application segment. The default behavior can cause unwanted access failure due to the destination matching a more specific application segment that does not have the UDP or TCP ports defined. Multimatch allows admins to create new application segments without the risk of unwanted access failure if a user attempts to access a FQDN with undefined ports. After Multimatch is enabled, the wildcard application segment catches all UDP or TCP ports that are not configured in the more specific application segment. When you have decided what application segments you want matched, you can enable Multimatch for that application segment. To learn more, see [Configuring Defined Application Segments](/unified/configuring-defined-application-segments).
Multimatch must be disabled if the configuration contains applications using the Access Type of Browser Access, AppProtection, or Privileged Remote Access. Additionally, Multimatch must be disabled if the configuration contains applications using Double Encryption, Inspect Traffic with ZIA, and Source IP Anchor. To learn more, see [Configuring Defined Application Segments](/unified/configuring-defined-application-segments).
Exact Match vs. Multimatch
There are two application match behaviors available in Private Applications: Exact Match and Multimatch. Exact match is the default behavior.
About Exact Match
The default behavior of Private Applications is to perform an exact match of applications. If two or more application segments cover the same destination address, Zscaler Client Connector attempts to match traffic to the more granular application segment. Consider the following example of two application segments with the overlapping domain name example.com:
- [Example: Exact Match](#Example_Exact-Match)
[]If a user attempts to access server1.example.com on TCP port 3389, the destination address maps to the more specific application segment, which is Server1_AS. However, the Server1_AS application segment does not have TCP port 3389 configured, resulting in failed access.
| Application Segment Name | Application | Protocol | Ports |
| ------------------------ | ----------- | -------- | ----- |
| Wildcard_AS | *.example.com | TCP, UDP | 1 to 52, 54 to 65535 |
| Server1_AS | server1.example.com | TCP | 443, 3389 |
In this scenario, the attempt to access server1.example.com on TCP port 3389 is dropped at the client level, traffic is not sent to the cloud, and logs aren't visible in the diagnostics. After a specific FQDN (Fully Qualified Domain Name) has been configured in an application segment, it is removed from the wildcard application segment by default. Even though server1.example.com is part of the Wildcard_AS application segment for the *example.com application on the TCP port range of 54 to 65535, this access does not match the Wildcard_AS application segment. To fix this, TCP port 3389 must be configured for the Server1_AS application segment, or Multimatch can be enabled. Enabling Multimatch changes the behavior of the wildcard application segment, and catches access to ports that have not been defined in the more specific FQDN application segment.
About Multimatch
The following examples illustrate how applications are mapped to application segments, as well as how policy execution works when Multimatch is enabled or not enabled on application segments.
- [Multiple application segment matches](#Multiple-App-Segment-Matches_tables)
- [Behavior after inserting a block rule](#Matching-for-Block-Policies_tables)
[]The primary use for Multimatch is when there are multiple possible application segment matches. The following tables show application segment configuration, the policy configuration, and how they match up.
| Application Segment Configuration |  |
| --------------------------------- | --- |
| Application Segment Name | Application | Protocol | Ports | Multimatch |
| Wildcard_AS | *.example.com | TCP, UDP | 1 to 52, 54 to 65535 | Enabled |
| Server1_AS | server1.example.com | TCP | 443, 3389 | Enabled |
| Access Policy Configuration |
| --------------------------- |
| # | Access Policy Name | Application Segment Name | Policy Action | User Group |
| 1 | Allow Server1_AS for Admin | Server1_AS | Allow | Admin_Grp |
| 2 | Allow Wildcard_AS for All | Wildcard_AS | Allow | All |
| Application Match and Policy Search Results |
| ------------------------------------------- |
| User | Group | FQDN: Protocol & Port | Matched Application Segment with Multimatch | Matched Application Segment without Multimatch | Matched Policy with Multimatch | Matched Policy Number without Multimatch |
| user1 | Admin_Grp | server1.example.com:TCP+3389 | Wildcard_ASServer1_AS | Server1_AS | Allow Server_AS for All (#1) | Allow Server1_AS for Admin (#1) |
| user2 | IT_Grp | server1.example.com:TCP+3389 | Wildcard_ASServer1_AS | Server1_AS | Allow Wildcard_AS for All (#2) | No policy match. Blocked by implicit default block policy. |
| user1 | Admin_Grp | server1.example.com:TCP+22 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#2) | Traffic is dropped at the client level |
| user2 | IT_Grp | server1.example.com:TCP+22 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#2) | Traffic is dropped at the client level |
| user3 | IT_Grp | server1.example.com:TCP+80 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#2) | Traffic is dropped at the client level |
| user3 | IT_Grp | server1.example.com:TCP+443 | Wildcard_ASServer1_AS | Server1_AS | Allow Wildcard_AS for All (#2) | No policy match. Blocked by implicit default block policy. |
Traffic that is dropped at the client level means that traffic matches the hostname, but it does not match the protocol and port. In this condition, traffic is not sent to the cloud for further processing. This means that policy evaluation does not occur, and the user is not able to access the application segment. In this case, traffic is not visible in the diagnostics.
[]The following table shows how the policy search results change by inserting a block policy in the rule set.
| Application Segment Configuration |
| --------------------------------- |
| Application Segment Name | Application | Protocol | Ports | Multimatch |
| Wildcard_AS | *.example.com | TCP, UDP | 1 to 52, 54 to 65535 | Enabled |
| Server1_AS | server1.example.com | TCP | 443, 3389 | Enabled |
| Access Policy Configuration |
| --------------------------- |
| # | Access Policy Name | Application Segment Name | Policy Action | User Group |
| 1 | Allow Server1_AS for Admin | Server1_AS | Allow | Admin_Grp |
| 2 | Block Server1_AS for All | Server1_AS | Block | All |
| 3 | Allow Wildcard_AS for All | Wildcard_AS | Allow | All |
| Application Match and Access Policy Search Results |
| -------------------------------------------------- |
| User | Group | FQDN: Protocol & Port | Matched Application Segment with Multimatch | Matched Application Segment without Multimatch | Matched Policy Number with Multimatch | Matched Policy Number without Multimatch |
| user1 | Admin_Grp | server1.example.com:TCP+3389 | Wildcard_ASServer1_AS | Server1_AS | Allow Server1_AS for Admin (#1) | Allow Server1_AS for Admin (#1) |
| user1 | Admin_Grp | server1.example.com:TCP+443 | Wildcard_ASServer1_AS | Server1_AS | Allow Server1_AS for Admin (#1) | Allow Server1_AS for Admin (#1) |
| user1 | Admin_Grp | server1.example.com:TCP+22 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#3) | Traffic is dropped at the client level |
| user2 | IT_Grp | server1.example.com:TCP+22 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#3) | Traffic is dropped at the client level |
| user3 | IT_Grp | server1.example.com:TCP+80 | Wildcard_AS | N/A | Allow Wildcard_AS for All (#3) | Traffic is dropped at the client level |
| user3 | IT_Grp | server1.example.com:TCP+443 | Wildcard_ASServer1_AS | Server1_AS | Block Server1_AS for All (#2) | Block1_AS for All (#2) |
Traffic that is dropped at the client level means that traffic matches the hostname, but it does not match the protocol and port. In this condition, traffic is not sent to the cloud for further processing. This means that policy evaluation does not occur, and the user is not able to access the application segment. In this case, traffic is not visible in the diagnostics.
Matched vs. Not Matched
Multiple matches apply to applications from most specific to least specific. As soon as an application is encountered that does not support Multimatch, the multimatching stops. The following examples show each possible outcome for matched and not matched results:
- [Example 1](#App-Match_Example1)
- [Example 2](#App-Match_Example2)
- [Example 3](#App-Match_Example3)
- [Example 4](#App-Match_Example4)
[]
| Application Match |
| ----------------- |
| **Application** | **Multimatch** | **Requested Domain** |
| server1.db.hr.company.com | server2.ui.hr.company.com |
| *.db.hr.company.com | Enabled | Matched | Not matched |
| *.ui.hr.company.com | Disabled | Not matched | Matched |
| *.hr.company.com | Enabled | Matched | Not matched |
| *.company.com | Disabled | Not matched | Not matched |
[]
| Application Match |
| ----------------- |
| **Application** | **Multimatch** | **Requested Domain** |
| server1.db.hr.company.com |
| server1.db.hr.company.com | Enabled | Matched |
| *.db.hr.company.com | Enabled | Matched |
| *.hr.company.com | Enabled | Matched |
| *.company.com | Disabled | Not matched |
| *.com | Enabled | Not matched |
[]
| Application Match |
| ----------------- |
| **Application** | **Multimatch** | **Requested Domain** |
| server1.db.hr.company.com | server2.db.hr.company.com |
| server1.db.hr.company.com | Disabled | Matched | Not matched |
| *.db.hr.company.com | Enabled | Not matched | Matched |
| *.hr.company.com | Enabled | Not matched | Matched |
| *.company.com | Disabled | Not matched | Not matched |
[]
| Application Match |
| ----------------- |
| **Application** | **Multimatch** | **Requested Domain** |
| server2.ui.hr.company.com |
| server2.ui.hr.company.com | Enabled | Matched |
| *.ui.hr.company.com | Disabled | Not matched |
| *.hr.company.com | Enabled | Not matched |
| *.company.com | Disabled | Not matched |
About IP Address- and IP Subnet-Based Multimatch
Even with an IP address, the default behavior of Private Applications is to perform an exact match of applications. If two or more application segments cover the same destination address, Zscaler Client Connector attempts to match traffic to the more granular application segment. Consider the following examples of two application segments with overlapping IP addresses:
- [Example: IP-Based Exact Match](#exactMatchIp)
- [Example: IP-Based Multimatch](#ipBasedMultimatch)
[]
| Application | Applications | Protocol | Port |
| ----------- | ------------ | -------- | ---- |
| Subnet_AS | 10.0.0.0/24 | TCP, UDP | 1 to 52, 54 to 65535 |
| IPaddress_AS | 10.0.0.1/32 | TCP | 443 |
| Rule Number | Access Policy Name | Application Segment | User Group | Action |
| ----------- | ------------------ | ------------------- | ---------- | ------ |
| 1 | Allow User A to access IPaddress_AS | IPaddress_AS | User A | Allow |
| 2 | Allow Everyone to access Subnet_AS | Subnet_AS | All | Allow |
In this scenario, the host at IP address 10.0.0.1 is contained within the IPaddress_AS application segment. If user B tries to access 10.0.0.1 on TCP port 443, they match the implicit block rule. User B does not match with rule number 1 because it is restricted to only User A. User B also does not match with rule number 2 even though it is for everyone, because the moment the IP address is created, the 10.0.0.1/32 host is carved out of Subnet_AS 10.0.0.0/24.
[]The primary use for Multimatch is when there are multiple possible application segment matches. The following tables show application segment configuration, the policy configuration, and how they match up.
| Application Segment Configuration |
| --------------------------------- |
| Application Segment Name | Application | Protocol | Port | Multimatch |
| Subnet_AS | 10.0.0.0/24 | TCP, UDP | 1 to 52, 54 to 65535 | Enabled |
| IPAddress_AS | 10.0.0.1/32 | TCP | 443, 3389 | Enabled |
| Application Match and Policy Search Results |
| ------------------------------------------- |
| # | Access Policy Name | Application Segment Name | Policy Action | User Group |
| 1 | Allow IPAddress_AS for Admin | IPAddress_AS | Allow | Admin_Grp |
| 2 | Allow Subnet_AS for All | Subnet_AS | Allow | All |
| Application Match and Policy Search Results |
| ------------------------------------------- |
| User | Group | IP Address: Protocol & Port | Matched Application Segment with Multimatch | Matched Application Segment without Multimatch | Matched Policy with Multimatch | Matched Policy without Multimatch |
| user1 | Admin_Grp | 10.0.0.1:TCP+3389 | Subnet_ASIPAddress_AS | IPAddress_AS | Allow IPAddress_AS for Admin (#1) | Allow IPAddress_AS for Admin (#1) |
| user2 | IT_Grp | 10.0.0.1:TCP+3389 | Subnet_ASIPAddress_AS | IPAddress_AS | Allow Subnet_AS for All (#2) | No policy match. Blocked by implicit default block policy. |
| user1 | Admin_Grp | 10.0.0.1:TCP+22 | Subnet_AS | N/A | Allow Subnet_AS for All (#2) | Traffic is dropped at the client level |
| user2 | IT_Grp | 10.0.0.1:TCP+22 | Subnet_AS | N/A | Allow Subnet_AS for All (#2) | Traffic is dropped at the client level |
| user3 | IT_Grp | 10.0.0.1:TCP+80 | Subnet_AS | N/A | Allow Subnet_AS for All (#2) | Traffic is dropped at the client level |
| user3 | IT_Grp | 10.0.0.1:TCP+443 | Subnet_ASIPAddress_AS | IPAddress_AS | Allow Subnet_AS for All (#2) | No policy match. Blocked by implicit default block policy. |
Traffic that is dropped at the client level means that traffic matches the IP address, but it does not match the protocol and port. In this condition, traffic is not sent to the cloud for further processing. This means that policy evaluation does not occur, and the user is not able to access the application segment. In this case, traffic is not visible in the diagnostics.