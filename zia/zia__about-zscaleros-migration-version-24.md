# About the ZscalerOS Migration to Version 24
Source: https://help.zscaler.com/zia/about-zscaleros-migration-version-24
PDF: https://help.zscaler.com/pdf/com/en/1402281.pdf

Zscaler continuously develops and integrates next-generation hardware, so our products and features require updated ZscalerOS versions and packages. As part of our efforts to improve our scalability and the robustness and performance of our security cloud, we will be migrating the ZscalerOS to version 24 on all the virtual platforms (ZIA Virtual Service Edge (formerly Virtual ZEN or VZEN), Zscaler Authentication Bridge (ZAB), and NSS).
Older versions of ZscalerOS will not be supported on next-generation hardware for new deployments.
Migration of ZscalerOS to version 24 comes with advanced security features and key benefits, such as:
- Security patches for the OS as well as new libraries
- TLS 1.3 support
- Enhancements to the performance of the Zscaler service
Zscaler backs up all the configurations that are needed to rebuild a new virtual machine (VM) in case of a migration failure and are non-recoverable.
Prerequisites
Ensure to download the SSL certificate and latest virtual machine (VM) from the ZIA Admin Portal for all of the virtual platforms used by your organization before migration.
- For Virtual Service Edge, see [Download Virtual Service Edge Certificates](/zia/downloading-virtual-service-edge-certificates) and [Downloading a Virtual Service Edge VM](/zia/downloading-virtual-service-edge-vm).
- For ZAB, see [Download the ZAB SSL Certificate](/zia/deploying-zscaler-authentication-bridge#downloadzabssl) and [Downloading the Zscaler Authentication Bridge VM](/zia/downloading-zscaler-authentication-bridge-vm).
- For NSS, download the SSL certificate and the VM based on your platform.
- For Azure, see [Download the NSS SSL Certificate](/zia/nss-deployment-guide-microsoft-azure#step_2) and [Deploy and then Download the NSS Virtual Appliance](/zia/nss-deployment-guide-microsoft-azure#step_3).
- For Amazon Web Services, see [Download NSS SSL Certificate](/zia/nss-deployment-guide-amazon-web-services#2) and [Deploy and then Download the NSS Virtual Appliance](/zia/nss-deployment-guide-amazon-web-services#3).
- For VMware Vsphere, see [Download NSS SSL Certificate](/zia/nss-deployment-guide-vmware-vsphere#2) and [Deploy and then Download the NSS Virtual Appliance](/zia/nss-deployment-guide-vmware-vsphere#3).
Troubleshooting
If the virtual platform is not accessible after migration, Zscaler Support will reach out if assistance is needed. You can also reach out to Zscaler Support if you observe any service interruption post migration.
If the VM is down or loses its connection with the CDS server when the migration package is pushed, wait until the connection is established with the CDS server again.
If a VM is migrated successfully, but the services are not starting, then enable remote access to the respective VM for Zscaler Support to troubleshoot:
- [Enabling remote access for Virtual Service Edge](#remote-access-vse)
- [Enabling remote access for ZAB](#remote-access-zab)
- [Enabling remote access for NSS ](#remote-access-nss)
If you have additional questions, contact your support team or open a Zscaler Support ticket.
[]An admin can request remote assistance and allow Zscaler Support to log in to their Virtual Service Edge instance without opening a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your Virtual Service Edge instance:
sudo vzen support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and then sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Virtual Service Edge instance.
- To disable Zscaler Support access to your Virtual Service Edge instance:
sudo vzen support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Virtual Service Edge instance:
sudo vzen support-access-status
This checks the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your Virtual Service Edge instance.
[]An admin can request remote assistance and allow Zscaler Support to log in to their ZAB without opening a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- Enter the following command to allow Zscaler Support remote access to examine and diagnose configuration errors. This feature is disabled by default.
zab enable-remote-debugging
- Enter the following command to allow Zscaler Support remote access to log in to your ZAB via SSH. An interactive shell is useful when additional troubleshooting assistance is required. This feature is disabled by default.
zab support-access-start
[]An admin can request remote assistance and allow Zscaler Support to log in to their NSS server without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your NSS server:
sudo nss support-access-start
This will create a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your NSS server.
- To disable Zscaler Support access to your NSS server:
sudo nss support-access-stop
This will bring down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your NSS server:
sudo nss support-access-status
This will check the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your NSS server.
- To enable a remote debugging session:
sudo nss enable-remote-debugging
- To disable a remote debugging session:
sudo nss disable-remote-debugging