# Adding IP-Based Applications to Bypass Traffic
Source: https://help.zscaler.com/zscaler-client-connector/adding-ip-based-applications-bypass-traffic
PDF: https://help.zscaler.com/pdf/com/en/1458821.pdf

In addition to using predefined applications (e.g., Microsoft Teams and Zoom), you can add IP-based applications to bypass traffic. Select the applications to bypass in [App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
To add an IP-based application to bypass traffic:
- In the Zscaler Client Connector Portal, go to **Administration**.
- Select **Application Bypass**.
- On the **IP-Based **tab, click **Custom**.
-
Click **Add Application**.
[See image.](#add)
-
In the **Add Application** window, complete the following fields:
Android only supports IP-based bypasses and does not support ports and protocols. All traffic that is associated with the specified IP is bypassed.
- For **General**: Enter the application’s name in the **Name **field.
- For **IPv4 **or **IPv6** **Addresses**:
- **Port**: Enter valid port numbers (1–65535) or a range of port numbers (e.g., 80–100) or an asterisk (*), separated by commas.
- **Protocol**: Select one of the following protocols for your application:
- **UDP**
- **TCP**
- Asterisk (*****) to represent any protocol
- **IPv4 Addresses** or **IPv6 Addresses**: Enter the IPv4/IPv6 addresses or subnet for the application, separated by commas.
[See image.](#add_IP)
- Click **Save**.
[]![IP-Based Application Application Bypass](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-ip-based-applications-bypass-traffic-doc-56508/Client_Connector_Add_IP_Based_Bypass.png)
[]![Add Application window when adding an IP-based application in Application Bypass](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-ip-based-applications-bypass-traffic-doc-56508/client-connector-IP-Based_Add_Application_1.png)