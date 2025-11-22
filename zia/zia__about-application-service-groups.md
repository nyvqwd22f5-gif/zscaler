# About Application Service Groups
Source: https://help.zscaler.com/zia/about-application-service-groups
PDF: https://help.zscaler.com/pdf/com/en/1401961.pdf

Zscaler provides predefined application service groups that can be used in [Firewall Filtering](/zia/configuring-firewall-filtering-policy) and [Forwarding](/zia/configuring-forwarding-policies) policies to manage specific application traffic. These groups cover various categories of applications and services, including productivity, communication, and collaboration software applications (e.g., Microsoft 365 and Zoom) and cloud service providers (e.g., Amazon Web Services (AWS) and Google Cloud Platform (GCP)). Defined using metadata—including IP addresses, ports, protocols, and domains—these groups rely on the information published by the respective providers to identify the traffic belonging to their services. Zscaler continuously updates and validates the latest IP addresses and other information published by the providers, ensuring that organizations have up-to-date information for traffic identification and policy enforcement.
[List of Available Application Service Groups](#application-service-group-list)
Application service groups designated for cloud service providers, such as AWS and GCP (i.e., hyperscalers), can identify traffic not only to these services but also their subservices based on the metadata published by the providers. These groups include all IP addresses for AWS- or GCP-based services, so it is recommended to use a combination of criteria in Firewall rules to allow this traffic only for intended users under specified conditions to ensure security (e.g., a rule to allow only the Engineering department to access AWS services over HTTPS). The general recommendation for Firewall Allow rules is to have a minimum of three conditions with Application Service Groups as one of them.
Application service groups provide the following benefits and enable you to:
- Identify and manage specific application and service traffic by configuring Firewall policies based on predefined application service groups.
- Enforce condition-based actions on the predefined application service traffic, such as allowing or blocking traffic and forwarding traffic to specific destinations.
- Leverage application service groups to efficiently manage bidirectional traffic applications that rely on a large volume of IP addresses, avoiding the hassle of regularly updating IP lists or configuring individual IP addresses in policies.
Zscaler's application services are identified at the first packet and therefore can result in the policy action hitting that first packet. The custom firmware pre-assembles the metadata received from the first packet, such as the domain and subdomains, along with their destination IP addresses, protocol types, and ports to identify the associated application service. This is different from the identification of packets for network applications. This means that policies using application services should be in a higher priority rule than a similar policy using network applications so that the former can be matched first. To learn more, see [About Network Applications](/zia/about-network-applications).
The Application Service Groups page contains a list of application service groups that you can use as criteria when configuring your Firewall Filtering and Forwarding rules. On this page, you can view the list of available application service groups and search for a service group from the list.
About the Application Service Groups Page
On the Application Service Groups page (Administration > Application Services > Application Service Groups), you can do the following:
- View the list of predefined application service groups provided by Zscaler.
- Sort the application service groups alphabetically.
- Search for an application service group by name.
![A screenshot of the Application Service Groups page](/downloads/zia/policies/firewall/firewall-policy-resources/about-network-application-groups/application-service-groups-page.png)
- []AWS
- GCP
- GoTo
- Microsoft 365
- RingCentral
- Webex
- Zoom
- Zscaler Cloud Endpoints