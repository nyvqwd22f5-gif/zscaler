# Detecting and Controlling DNS Tunnels
Source: https://help.zscaler.com/zia/detecting-and-controlling-dns-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1400861.pdf

By using sophisticated machine learning techniques, the Zscaler service can detect DNS tunneling occurring in your network. You can [create granular rules](/zia/configuring-dns-control-policy) to control DNS tunnels as part of your [DNS Control](/zia/about-dns-control) policy. You can also analyze and visualize your DNS tunnels and network applications. The service logs all detected DNS tunnels and network apps in [DNS Insights](/zia/about-insights). You can also view the most commonly encountered tunnels and apps in the DNS Overview [dashboard](/zia/about-dashboards).
DNS Tunnels
DNS tunneling is commonly used to circumvent security. Tunneling can be used for benign reasons. For example, an anti-virus update done by endpoint software. However, it is also used for more malicious purposes, such as evading captive portals.
To create a DNS tunnel, a user sets up a tunnel client that sends out a request on port 53 to a DNS tunnel server. The DNS tunnel server can use this newly created tunnel to compromise the TXT field of the DNS response message. These payloads can introduce a variety of security hazards which are often not detected due to the trusted character of DNS traffic. If malicious DNS tunneling goes unobserved it creates significant risk, with companies leaving themselves open to data exfiltration, command and control activity, as well as other hazards.
![Diagram showing basic tunneling process](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies-resources/about-dns-application-groups/dns%20tunneling%20diagram.png)
How Zscaler DNS Tunneling Detection Works
The Zscaler service enables you to detect and control DNS tunneling occurring in your networks. The service provides a DNS proxy. You can use this proxy as a firewall to DNS traffic. All traffic that goes through this proxy is logged by the service. The Zscaler analytics system then fetches these logs, processes them, and sends them to the DNS tunneling detection engine. The detection engine uses advanced machine learning techniques to compute a risk score to classify domains. Once the engine detects a tunnel hostname, the information is propagated to all [ZIA Public Service Edges](/zia/about-zscaler-enforcement-nodes). The proxy server then acts according to your policy configuration.
![Diagram demonstrating how Zscaler's tunneling detection works](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policies/dns-control/about-dns-tunnel-detection/zia-about-tunneling-detection0.png)
The service places any tunnels it detects into one of three categories. These are:
- Commonly Allowed DNS Tunnels: This contains tunnels that use DNS tunneling for productive reasons. It is mostly composed of traffic from security services.
- Commonly Blocked DNS Tunnels: This contains tunnels that are malicious, can cause a loss of productivity, or can cause a loss of data.
- Unknown DNS Tunnels: This contains tunnels that are not yet classified.
DNS Applications
There are four additional categories that you can control alongside the DNS tunnels. These are:
- Network Service: This contains different network protocols, such as TCP and UDP.
- Social Networking: This contains popular websites with social networking components, such as Facebook and LinkedIn.
- Web: This contains widely used websites, such as Amazon and CNN.
- Web Search: This contains popular search engines, such as Google and Bing.
These categories give administrators the flexibility to control any of these items at the DNS level.
From these categories, users can either select the whole category or individual items to make up a DNS Application Group. To learn more, see [About DNS Application Groups](/zia/about-dns-application-groups).