# Configuring Network Services
Source: https://help.zscaler.com/cloud-branch-connector/configuring-network-services
PDF: https://help.zscaler.com/pdf/com/en/1420441.pdf

You can define custom network services to add to the [Firewall](/zia/about-firewall-control), [DNS](/zia/about-dns-control), and [NAT](/zia/about-nat-control) policies. Additionally, you can define custom services that include [custom ports](/zia/configuring-custom-ports) for HTTP, HTTPS, DNS, FTP, RTSP, or PPTP.
To add a custom network service:
- Go to **Administration **>** ****Network Services**.
- On the **Services** tab, select **Add Network Service**.
[See image.](#AddNetworkService)
[![Add Network Service in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/configuring-network-services/Add%20Network%20Service%20Brnch.jpg)
]
- In the **Add Network Service** window:
- **Name**: Enter a name for the application layer service that you want to control.
- **Definition**: This field displays **CUSTOM** to indicate that this is an admin-defined service.
- **Description**: Enter additional notes or information about the Network Service. The description cannot exceed 10,240 characters.
- In **TCP Source Ports**, **TCP Destination Ports**, **UDP Source Ports**, and **UDP Destination Ports**, enter the port number (for example `50`) or port number range (for example `1000-1050`) that is used by the network service.
You can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[See image.](#AddNetworkServiceWindow)
[![Add Network Service Window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/configuring-network-services/Add%20Network%20Service%20Window_0.jpg)
]
- Click **Save** and [activate the change.](/cloud-branch-connector/saving-and-activating-changes)