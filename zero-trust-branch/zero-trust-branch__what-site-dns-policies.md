# What Are Site DNS Policies?
Source: https://help.zscaler.com/zero-trust-branch/what-site-dns-policies
PDF: https://help.zscaler.com/pdf/com/en/1531224.pdf

The DNS is a key part of the internet, offering the power of quickly translating between the human language of FQDNs and the computer language of IP addresses.
Within Zero Trust Branch, you can use DNS policies to define rules that control DNS requests and responses to your Zero Trust Branch sites. To learn more about configuring site DNS policies, see [Configuring Site DNS Policies](/zero-trust-branch/configuring-site-dns-policies).
Key Features and Benefits
Within Zero Trust Branch, site DNS policies provide the following benefits and enable you to:
- Monitor and apply policies to all DNS requests and responses, regardless of the protocol. This includes UDP and TCP.
- Define granular DNS filtering rules using a number of criteria, such as source IP address or subnet, FQDN, wildcard domains, or any domain.
- Enforce condition-based actions on DNS traffic, such as allowing or rejecting DNS queries, redirecting queries to specific DNS gateways, or overriding DNS responses.
- Configure a system default rule that allows and forwards all DNS traffic. This rule maintains the lowest precedence and can modify the default behavior by establishing a policy that matches any domain.
[See image.](#dns-policies-tab)
[]![DNS Policies tab on the Sites page](/downloads/zero-trust-branch/administration/deployment-configuration/what-site-dns-policies/dns-policies-tab.png)