# Validating a Client Hostname
Source: https://help.zscaler.com/zpa/validating-client-hostname
PDF: https://help.zscaler.com/pdf/com/en/1485046.pdf

Validating a client hostname allows you to enroll endpoints for [peer-to-peer connectivity](/zpa/administration/peer-peer-connectivity) so that you can accept incoming connections through ZPA from other clients. To enroll the endpoints, a regular expression of allowed hostnames is configured per tenant. This regular expression controls the endpoints to which Zscaler Client Connector allows the peer-to-peer connectivity. Endpoints whose FQDNs match this regular expression are enrolled. To learn more, see [Understanding Client-To-Client Connectivity](/zpa/understanding-client-client-connectivity) and [Understanding Server-To-Client Connectivity](/zpa/understanding-server-client-connectivity).
If an application configured for Privileged Remote Access (PRA) matches a valid client hostname configured for peer-to-peer connectivity, and the user's device is also configured for peer-to-peer connectivity, then PRA is not supported.
Prior to enabling peer-to-peer connectivity, the following prerequisites must be met:
- Ensure that the remote user has installed Zscaler Client Connector version 3.9.0.169 or later on the destination machine that they want to establish the connectivity to. Zscaler Client Connector on the destination machine must have a machine tunnel deployed. To learn more, see [Understanding Zscaler Client Connector App Downloads](/z-app/downloading-zscaler-app#zia-admin-portal).
- Ensure that endpoints or devices have valid, complete, and unique FQDNs.
To validate a client hostname:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- (Optional) If your window is compact and resized, click the **Menu **icon (![menu icon in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/validating-client-hostname/zpa-admin-portal-menuIcon.png)
) to view a drop-down menu of the features.
[See image.](#SeeImage)
- Click **Client Hostname Validation**.
![Validating a client hostname in the ZPA Admin Portal](/downloads/zpa-c2c-click-client-hostname.png)
The **Edit Regular Expression **window appears.
- In the **Regular Expression **field, configure a valid regular expression.
![Configure a regex in the ZPA Admin Portal](/downloads/zpa-c2c-configure-regex_0.png)
For example, enter the regular expression “.*.example.com” to establish a peer-to-peer connection for devices joined with domains matching this regular expression (e.g., “test.example.com”).
If you have the same namespace for both your applications and workstations, Zscaler recommends creating different application segments for peer-to-peer connectivity and for application access. To successfully enable remote assistance, the application segment designated for peer-to-peer connectivity must match the regular expression defined in step 4.
- Click **Save**.
[]![App Segment drop-down menu for features](/downloads/zpa-c2c-3-line-dropdown.png)