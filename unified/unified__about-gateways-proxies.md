# About Gateways for Proxies
Source: https://help.zscaler.com/unified/about-gateways-proxies
PDF: https://help.zscaler.com/pdf/com/en/1497091.pdf

You can create gateway objects to configure the [Third-Party Proxy Chaining](/unified/understanding-third-party-proxy-chaining) feature which enables you to forward traffic to a third-party proxy service.
This page provides the following benefits and enables you to:
- Create gateway objects for proxies that can be used in forwarding policies to redirect certain web traffic to a third-party proxy service of your choice.
- Configure two proxies, primary and secondary proxy, for a gateway object to support failover to the secondary proxy when the primary proxy is unreachable.
- Define if the traffic should be dropped or forwarded directly to the destination server when both third-party proxies are not reachable.
About the Gateways Page
On the Proxy Gateways page (Infrastructure > Internet & SaaS > Network Policies > Proxies and Gateways > Proxy Gateways), you can do the following:
- [Add gateways for third-party proxies](/unified/configuring-gateways-proxies)
- Search for a gateway.
- View a list of all gateways. For each gateway, you can view the following information:
- **Gateway Name**: The name of the gateway. You can sort this column.
- **Primary Proxy**: The primary proxy for the gateway.
- **Secondary Proxy**: The secondary proxy for the gateway.
- **Description**: Additional notes or information about the gateway.
- **Fail Close**: Indicates whether the fail close is enabled to drop the traffic or disabled to allow the traffic when both primary and secondary proxies defined in this gateway are unreachable.
- [Modify the table and its columns](/unified/using-tables).
- Edit a gateway.
- Go to the [Proxies](/unified/about-third-party-proxies) page.
- Go to the [DNS Gateways](/unified/about-dns-gateways) page.
![Screenshot of About Gateways page showing buttons and list used to manage Zscaler Third-Party Proxies](/downloads/zia/policies/forwarding-control/third-party-proxy-chaining/about-gateways-proxies/ZIA-Proxy-Gateways-Page.png)