# About Gateways for Proxies
Source: https://help.zscaler.com/zia/about-gateways-proxies
PDF: https://help.zscaler.com/pdf/com/en/1401506.pdf

You can create gateway objects to configure the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature which enables you to forward traffic to a third-party proxy service.
This page provides the following benefits and enables you to:
- Create gateway objects for proxies that can be used in forwarding policies to redirect certain web traffic to a third-party proxy service of your choice.
- Configure two proxies, primary and secondary proxy, for a gateway object to support failover to the secondary proxy when the primary proxy is unreachable.
- Define if the traffic should be dropped or forwarded directly to the destination server when both third-party proxies are not reachable.
About the Proxy Gateways Page
On the Proxy Gateways (Administration > Proxies & Gateways > Proxy Gateways) page, you can do the following:
- [Add gateways for third-party proxies](/zia/configuring-gateways-proxies)
- Search for a gateway.
- View a list of all gateways. For each gateway, you can view the following information:
- **Gateway Name**: The name of the gateway. You can sort this column.
- **Primary Proxy**: The primary proxy for the gateway.
- **Secondary Proxy**: The secondary proxy for the gateway.
- **Description**: Additional notes or information about the gateway.
- **Fail Close**: Indicates whether the fail close is enabled to drop the traffic or disabled to allow the traffic when both primary and secondary proxies defined in this gateway are unreachable.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit a gateway](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Go to the** **[Proxies](/zia/about-third-party-proxies) page.
- Go to the [DNS Gateways](/zia/about-dns-gateways) page.
![Gateways Page](/downloads/zia/policies/forwarding-control/third-party-proxy-chaining/about-gateways-proxies/ZIA-Proxy-Gateways-Page.png)