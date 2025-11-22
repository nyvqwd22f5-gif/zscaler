# Downloading Internet & SaaS Virtual Service Edge Certificates
Source: https://help.zscaler.com/unified/downloading-internet-saas-virtual-service-edge-certificates
PDF: https://help.zscaler.com/pdf/com/en/1495721.pdf

Downloading an Internet & SaaS Virtual Service Edge certificate is one of the tasks you must complete when deploying Virtual Service Edge clusters for production. To learn more, see [Configuring Internet & SaaS Virtual Service Edge Clusters](/unified/configuring-internet-saas-virtual-service-edge-clusters).
The Virtual Service Edge certificate is used to authenticate each Virtual Service Edge instance to the Zscaler cloud. You must download the certificate for each Virtual Service Edge instance that you added. For example, if your cluster has two Virtual Service Edges, you'll need to download two certificates. You will upload each certificate to the appropriate vSphere client. To learn more, see [Adding Internet & SaaS Virtual Service Edge Instances](/unified/adding-internet-saas-virtual-service-edge-instances).
To download a Virtual Service Edge certificate:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Virtual Service Edges**.
-
In the** SSL Certificate** column, click **Download** for the [Virtual Service Edge that you added](/unified/adding-internet-saas-virtual-service-edge-instances) previously, and then save the certificate.
[See image.](#Image)
If you're downloading multiple certificates, you might want to change the certificate name so that you can differentiate between them. For example, if the Virtual Service Edge instances in a cluster are called VSE1 and VSE2, you can rename the certificate's ZIP files to VSE1.zip and VSE2.zip.
[]![Screenshot of the SSL Certificate column and download link on the Virtual Service Edge page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/downloading-virtual-service-edge-certificates/ZIA-Virtual-Service-Edge-SSL-Certificate-v6.2.png?1662123037)