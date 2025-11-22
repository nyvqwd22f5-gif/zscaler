# Viewing Firewall Requirements for Using PAC Files
Source: https://help.zscaler.com/zia/viewing-firewall-requirements-using-pac-files
PDF: https://help.zscaler.com/pdf/com/en/1399436.pdf

This article guides you on how to review the required firewall configurations for using PAC files and the destination IP addresses of the service to make the necessary firewall configuration changes.
To view the firewall requirements:
-
In the left-side navigation, click the **Help** icon and then select **Cloud Configuration Requirements**.
The **Zscaler Config** page appears with the** Firewall Configuration Requirements**.
-
On the **Firewall Configuration Requirements **page, review the **Traffic Forwarding Requirements** section.
[See image.](#firewall-configuration-requirements)
To restrict web access entirely to the Zscaler service, configure your firewalls to allow outbound traffic from the clients only to the Zscaler service.
Ensure that you configure firewall policies to prevent traffic from bypassing the Zscaler service and accessing the internet directly, unless explicitly allowed. Additionally, to prevent users with admin rights from installing non-standard browsers to bypass Zscaler, implement firewall rules that force admins to browse through the Zscaler service only.
![The Zscaler Config page displaying the Firewall Configuration Requirements > Traffic Forwarding Requirements](/downloads/zia/traffic-forwarding/pac-files/using-pac-files/firewall-requirements-using-pac-files/zia-firewall-requirements-using-pac-files-zscaler-config-page.png)
[]