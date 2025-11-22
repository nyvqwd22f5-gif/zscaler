# Configuring Network Services
Source: https://help.zscaler.com/zia/configuring-network-services
PDF: https://help.zscaler.com/pdf/com/en/1400131.pdf

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