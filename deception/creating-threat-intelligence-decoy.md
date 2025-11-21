# Creating a Threat Intelligence Decoy
Source: https://help.zscaler.com/deception/creating-threat-intelligence-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531292.pdf

[Watch a video on Creating Threat Intelligence Decoys.](https://fast.wistia.net/embed/iframe/x1u6oijljq)
A Threat Intelligence (TI) decoy generates organization-specific intelligence about reconnaissance attempts and subsequent attacks against your public-facing assets.
Prerequisites
[]Before creating TI decoys, make sure that you have permissions to create DNS A records for the decoys you intend to create.
Creating a Threat Intelligence Decoy
[]To create a TI decoy:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Threat Intelligence Decoys**.
- Click **Add Decoy**, and choose one of the following options from the drop-down menu:
- **Static Application**: A decoy web application with static pages.
- **Dynamic Application**: A decoy web application with dynamic components that respond to the latest threats.
-
**High Interaction Applications**: A containerized version of the decoy application.
[See image.](#add-ti-decoy)
- In the decoy details window:
- **Enabled**: Select to enable the decoy.
- **Allow port 80**: Enable if you want the decoy to be accessible via HTTP port 80.
- **Subdomain FQDN**: Enter the decoy's FQDN.
- **Description**: Enter the description of the decoy.
- **Network Interface**: Select a network interface from the drop-down menu. If there is a TI Decoy Connector that the Deception team has provisioned, it is automatically populated.
- **Decoy Group**: A decoy group by name **Threat Intelligence** is automatically populated. To learn more, see [Creating a Network Decoy Group](/deception/creating-network-decoy-group).
- **Choose static application**: Select a static, dynamic, or high interaction decoy application based on your selection in step 3.
- **Web Server Banner**: Select a banner from the drop-down menu.
-
**Internal NAT IP**: Enter a private IP address to host the decoy. For a Deception-hosted TI decoy, the IP address is always 10.10.10.10.
This field doesn't appear if you selected a TI Decoy Connector for **Network Interface**.
- **Number of trusted proxies**: Enter the number of trusted proxies. Use this setting to configure a decoy when it is placed behind a web application firewall (WAF), load balancer, or content delivery network (CDN). By default, this field is set to zero. You can increase this number by one for every proxy.
-
**SSL Certificate** and **SSL Private Key**: (Optional) Upload an SSL certificate and its corresponding unencrypted SSL private key in the PEM format. By default, the SSL certificates are self-signed.
Deception doesn't support encrypted private keys for custom SSL certificates.
- Under **Response Headers**:
- **Enable Security Headers**: Select to add HTTP security headers, such as X-Content-Type-Options, Referrer-Policy, Permissions-Policy, and Content-Security-Policy to the web service.
- **Enable HTTP Strict-Transport-Policy Response Header**: Select to add the HTTP Strict-Transport-Security (HSTS) response header to the web service.
- Under **Custom Response Headers**:
- Click **Add** to add custom response headers that you can use to manipulate the HTTP response headers. The custom response headers are visible in a browser when an adversary accesses an Internal decoy. Custom headers make the decoy look realistic, so that an adversary engages with the decoy for a longer time.
- Enter the custom header key and value.
-
Click **Submit**.
[See image.](#configure-ti-decoy-details)
The TI decoy is created. The red status icon (![Red decoy deployment status icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-red-status-icon.png)
) next to the decoys indicates that the decoy is inactive.
[See image.](#ti-decoy-inactive)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
-
Go to **Deceive** > **Threat Intelligence Decoys**.
The decoy is deployed and active. The status icon turns green (![Green decoy deployment status icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-green-status-icon.png)
).
[See image.](#ti-decoy-active)
Avoid configuring a TI decoy behind a proxy that translates IPv6 to IPv4 (e.g., Cloudflare). This allows an adversary to connect to the decoy over IPv6, but the Zscaler Deception Admin Portal does not alert you about the IPv6 connection that is established. For Cloudflare, use a DNS pointer and not a proxied connection.
The number of trusted proxies depends on the number of layers of reverse proxies between the private IP address and the attacker. These layers can be load balancers, web application firewalls, distributed denial-of-service (DDoS) prevention solutions, etc. These systems must maintain the original attacker's IP address in the X-Forwarder-For request header.
Creating TI Decoys Based on AI-Powered Recommendations
Manually analyzing TI decoy configurations such as determining hostnames (subdomain FQDNs), datasets, server banners, IP addresses, etc. can be time consuming. To enhance efficiency, Deception leverages AI to generate decoy recommendations based on the provided domain name. These recommendations include preselected hostnames, datasets, server banners, and other configurations. This simplifies decoy creation and deployment, and reduces manual effort.
To create TI decoys based on AI-powered recommendations:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Threat Intelligence Decoys**.
-
Click **AI-Powered Recommendations**.
[See image.](#deception-ti-ai-recomm-create)
-
In the **AI-Powered Recommendations** window, enter a domain name.
[See image.](#deception-ai-recomm-ti-enter-domain)
Deception checks the domain to verify if wildcard DNS is enabled across the entire root domain (e.g., `bank.com`). If enabled, Deception cannot recommend decoys. This is because wildcard DNS returns a default or dummy address for any subdomain, making it look like all subdomains already exist. In such cases, you must manually create TI decoys.
-
Click **Next**.
Deception leverages AI to generate a list of decoy hostnames. Each hostname is automatically validated through real-time DNS checks to ensure it does not correspond to an active or existing application. If a conflict is found, Deception regenerates and revalidates new recommendations, with up to 5 retries. After successful validation, the AI-powered TI decoy recommendations appear with hostnames, type, dataset, server banner, etc.
[See image.](#deception-ai-recomm-ti-validate)
-
Validate the recommendations. You can modify the recommendations, if necessary.
[See image.](#deception-view-ai-powered-recomm)
-
Click **Save**.
The decoys are created. The red status icon (![Red decoy deployment status icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-red-status-icon.png)
) next to the decoys indicates that the decoy is inactive.
[See image.](#deception-ai-recom-ti-inactive)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
-
Go to **Deceive** > **Network Decoys** > **Zero Trust Network**.
The decoys are deployed and active. The status icon turns green (![Green decoy deployment status icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-green-status-icon.png)
).
[See image.](#deception-ai-recom-ti-active)
After the decoys are created, you can [test](/deception/testing-threat-intelligence-decoy) them to simulate an attack.
[]![Add a TI decoy](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ti-add-decoys-4.png)
![Image]()
[]![Configure TI decoy details](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ti-decoy-configuration-5.png)
[]![Inactive TI decoys](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ti-decoy-inactive-2.png)
[]![Active TI decoys](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ti-decoy-active-3.png)
[]![Create AI-powered TI decoys](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-create-ai-recomm-ti.png)
[]![Enter domain name](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ai-recomm-ti-enter-domain.png)
[]![Validate and generate decoys](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ai-recomm-ti-validation-1.png)
[]![View AI-powered recommendations](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ai-ti-recommendations-1.png)
[]![Inactive AI-powered TI decoys ](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ai-ti-decoys-created-inactive.png)
[]![Active AI-powered TI decoys](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-ai-ti-decoys-created-active.png)