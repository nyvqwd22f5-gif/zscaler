# Adding NSS Collector Servers
Source: https://help.zscaler.com/zia/adding-nss-collector-servers
PDF: https://help.zscaler.com/pdf/com/en/1463361.pdf

The NSS Collector functionality and the data collected using this functionality are exclusive to Shadow IT Report. To enable this feature for your organization, contact Zscaler Support.
You can configure the [NSS Collector server](/zia/about-nss-collector-servers) in the ZIA Admin Portal to obtain the packaged software (VM image) that must be installed in your organization’s network perimeter. To learn more about NSS Collectors and their use in third-party log integration with Zscaler, see [Understanding Nanolog Streaming Service (NSS)](/zia/understanding-nanolog-streaming-service).
To add an NSS Collector server:
- Go to **Administration** > **Nanolog Streaming Service**.
- From the **NSS Collector Servers** tab, click **Add NSS Collector Server**.
- In the **Add NSS Collector Server** window:
- **Name**: Enter a name for the NSS Collector server.
- **Vendor**: Select the vendor of the third-party firewall or web proxy service used by your organization for which the logs must be integrated with Zscaler.
- **Status**: Select **Enabled** to allow the NSS Collector to process and stream logs from the third-party firewalls or web proxies to the Zscaler service. When disabled, the NSS Collector does not process or stream logs from third-party security solutions.
- Click **Save**.
[See image.](#add-nss-collector-server)
When the NSS Collector server is added to the ZIA Admin Portal, Zscaler generates the packaged software for installation and issues an SSL certificate to the server.
To download the packaged software and the SSL certificate for the server:
- Click the **Edit** icon displayed against the NSS Collector server.
- In the **Edit NSS Server** window:
- Under the **SSL Certificate** field, you can download the SSL certificate issued for the NSS Collector server. You can also regenerate a new certificate for the server as required. The SSL certificate must be installed on the NSS Collector VM so that the NSS Collector can authenticate as a client with the Zscaler service.
- Under the **Software** field, you can download the packaged software generated for the server. This packaged software must be deployed in your organization's network perimeter. To learn more about the deployment procedure, see [NSS Collector Deployment Guide for VMware vSphere](/zia/nss-collector-deployment-guide-vmware-vsphere).
[See image.](#edit-nss-collector-server)
You can also download the SSL certificate directly from the NSS Collector Servers table by clicking the **Download** button against the required NSS Collector server under the **SSL Certificate** column.
[See image.](#ssl-certificate-download)
An organization can have up to 4 NSS Collector servers.
[]![A screenshot of the Add NSS Collector Server window](/downloads/zia/nanolog-streaming-service/adding-nss-collector-servers/add-nss-collector.png)
[]![A screenshot of the Edit NSS Collector Server window](/downloads/zia/nanolog-streaming-service/adding-nss-collector-servers/edit-nss-collector.png)
[]![A screenshot of the SSL certificate download option for NSS Collector server](/downloads/zia/nanolog-streaming-service/adding-nss-collector-servers/nss-collector-ssl-certificate-download.png)