# Understanding Third-Party Proxy Chaining
Source: https://help.zscaler.com/zia/understanding-third-party-proxy-chaining
PDF: https://help.zscaler.com/pdf/com/en/1401541.pdf

Users who are subscribed to Zscaler service may also subscribe to other cloud security, archival or other services. For example, organizations that require Zscaler’s security service for all of their outbound traffic may still want to use third-party services for additional layers of security or compliance purposes. The Third-Party Proxy Chaining feature allows Zscaler to successfully integrate with these services.
This feature uses forwarding policies, which allow you to define what traffic needs to be forwarded to a third-party proxy service of your choice. Based on the forwarding rules configured, Zscaler forwards the matching web traffic to the proxies specified in the policy for further processing. Here, Zscaler functions as a child proxy or a down-stream proxy to the third-party service.
To learn the step-by-step configuration of this feature, see [Configuring Third-Party Proxy Chaining](/zia/configuring-third-party-proxy-chaining).