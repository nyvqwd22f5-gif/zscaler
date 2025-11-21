# About Third-Party Proxies
Source: https://help.zscaler.com/zia/about-third-party-proxies
PDF: https://help.zscaler.com/pdf/com/en/1401496.pdf

You can add proxies to gateways and configure the [Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining) feature which enables you to forward traffic to a third-party proxy service.
This page provides the following benefits and enables you to:
- Configure proxy objects (IP address or the FQDN) of a third-party proxy service that you want to integrate with Zscaler services to provide an additional security layer for the outbound traffic.
- Configure proxies that can be added to the gateways to forward specific web traffic through the third-party proxy service before reaching the destination server.
About the Proxies Page
On the Proxies (Administration > Proxies & Gateways > Proxies) page, you can do the following:
- [Add proxies for a third-party proxy service](/zia/configuring-third-party-proxies)
- Search for a proxy.
- View a list of all proxies. For each proxy, you can view the following information:
- **Proxy Name**: The name of the proxy. You can sort this column.
- **IP/FQDN**:** **The IP address or the FQDN configured for this proxy.
- **Port**: The port number configured for this proxy.
- **Description**: Additional notes or information about the proxy.
- **Root Certificate**: The root certificate included in this proxy which is used by Zscaler to perform SSL inspection on the traffic being forwarded by Zscaler.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit a proxy](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Go to the [DNS Gateways](/zia/about-dns-gateways) page.
- Go to the [Proxy Gateways](/zia/about-gateways-proxies) page.
![Proxies Page](/downloads/zia/policies/forwarding-control/third-party-proxy-chaining/about-third-party-proxies/ZIA-Proxies-Page.png)