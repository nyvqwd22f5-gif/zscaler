# DNS Request Failure in Zscaler Client Connector version 4.1.0.89
Source: https://help.zscaler.com/zscaler-client-connector/dns-request-failure-zscaler-client-connector-version-4.1.0.89
PDF: https://help.zscaler.com/pdf/com/en/1451016.pdf

In Zscaler Client Connector version 4.1.0.89 for Windows, the nslookup command, which targets a DNS request to a specific DNS server by domain, fails on devices running Zscaler Client Connector with only an IPv4 address if the DNS domain is a Zscaler Private Access (ZPA) application (e.g., *.company.com).
This issue was fixed in Zscaler Client Connector version 4.1.0.98 for Windows.