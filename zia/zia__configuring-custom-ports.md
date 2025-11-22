# Configuring Custom Ports
Source: https://help.zscaler.com/zia/configuring-custom-ports
PDF: https://help.zscaler.com/pdf/com/en/1399926.pdf

By default, the Zscaler service "listens to" the following ports:
- Port 80 for HTTP traffic
- Port 443 for HTTPS traffic
- Port 53 for DNS traffic
- Port 21 for FTP traffic
- Port 554 for RTSP traffic
- Port 1723 for PPTP traffic
If your organization uses other or additional ports for these types of traffic, you can configure the service to use custom ports for them. To begin, create a custom service with the appropriate ports. Then, in [Advanced Settings](/zia/about-advanced-settings), configure the service to accept traffic from the ports assigned to the custom service that you created.
Add a Custom Network Service
[Watch a video about adding Network Services, including how to add a network service.](https://fast.wistia.net/embed/iframe/fa5a6c5wtm)
You can define custom network services to add to the [Firewall](/zia/understanding-firewall-capabilities), [DNS](/zia/about-dns-control) and [NAT](/zia/about-nat-control) policies. Additionally, you can define custom services that include [custom ports](/zia/configuring-custom-ports) for HTTP, HTTPS, DNS, FTP, RTSP, or PPTP.
Custom network services can be defined as a combination of protocols and ports used at the source and destination. The available combination of protocols and ports are:
- TCP Source Ports
- UDP Source Ports
- TCP Destination Ports
- UDP Destination Ports
When defining a custom network service, these protocol-port combinations are associated using implicit logical relationships based on source and destination, explained as follows:
[(TCP Source Ports OR UDP Source Ports) AND (TCP Destination Ports OR UDP Destination Ports)]
All source and destination entities have an OR relationship within them and a combination of source and destination entities have an AND relationship. For example, if you have configured a network service with TCP Destination Port 444, UDP Destination Port 333, and TCP Source Port 111, the traffic is identified with the network service only if it originates from port 111 over TCP *and *is destined to either TCP 444 *or *UDP 333 port.
To add a custom network service:
- Go to **Administration **>** Network Services**.
- On the **Services** tab, click **Add Network Service**.
- Enter a **Name** for the application layer service that you want to control. It can include any character and spaces.
For the **Definition** field, the service displays **Custom** to indicate that this is an admin-defined service.
- For **TCP Source Ports**, **TCP Destination Ports**, **UDP Source Ports**, and **UDP Destination Ports**, enter the port number (e.g., 50) or port number range (e.g., 1000–1050), if any, that is used by the network service. You can add up to 8 ports for each of the fields.
- Optionally, enter additional notes or information. The description cannot exceed 10,240 characters. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- Click **Save** and [activate the change.](/zia/how-do-i-configure-custom-ports)
Configure the Proxy Service
To configure the Zscaler proxy service to accept traffic from custom ports:
- Go to **Administration **>** ****Advanced Settings**
[See image.](#Advanced)
- Complete the following information:
- **Services Forwarded to HTTP Web Proxy**:** **From the **HTTP Services** and **HTTPS Services** lists, choose the custom service that specifies the ports your organization uses for HTTP and HTTPS.
- **Services Applicable to DNS Transaction Policies**: From the **DNS Services** list, choose the custom service that specifies the ports your organization uses for DNS traffic.
- **Services Forwarded to FTP Proxy**:** **From the **FTP Services** list, choose the custom service that specifies the ports your organization uses for FTP traffic.
- **Services Forwarded to RTSP**: From the **RTSP Services** list, choose the custom service that specifies the ports your organization uses for RTSP traffic.
- **Services Forwarded to PPTP**: From the **PPTP Services** list, choose the custom service that specifies the ports your organization uses for PPTP traffic.
[See image.](#seeimage1)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![zia-custom-ports.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/configuring-custom-ports/zia-custom-ports.png)
[![Advanced Settings found in the Administration section under Cloud Configuration](/downloads/zia/policies/firewall/configuring-custom-ports/Configuring%20Custom%20Ports_Advanced%20Settings.png)
]