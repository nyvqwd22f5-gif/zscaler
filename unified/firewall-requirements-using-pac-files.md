# Firewall Requirements for Using PAC Files
Source: https://help.zscaler.com/unified/firewall-requirements-using-pac-files
PDF: https://help.zscaler.com/pdf/com/en/1495451.pdf

Review the firewall configuration requirements and the destination IP addresses of the service, and then make the necessary configuration changes.
To review the firewall requirements:
- Go to [https://config.zscaler.com/](https://config.zscaler.com/)
- In the **Cloud** drop-down menu, ensure your appropriate Zscaler cloud is selected (e.g., zscaler.net).
- Review the **Firewall Config Requirements** section.
To restrict web access to the Zscaler service only, configure your firewalls to allow outbound traffic from all clients to the service.
Additionally, ensure that you define firewall policies that do not allow traffic to bypass the service and go directly to the internet, unless it’s explicitly allowed. To deter users with admin rights from installing non-standard browsers to circumvent the Zscaler service, you can use firewall rules to force users to browse through the Zscaler service only.