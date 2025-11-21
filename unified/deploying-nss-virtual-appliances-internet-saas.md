# Deploying NSS Virtual Appliances for Internet & SaaS
Source: https://help.zscaler.com/unified/deploying-nss-virtual-appliances-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1496621.pdf

New or clean deployment of Nanolog Streaming Service (NSS) requires VM image running on ZscalerOS version 24.
Depending on your platform, the Zscaler service needs to compute the appropriate resources for your NSS virtual appliance.
The NSS buffers the logs for at least one hour. If a security information and event management (SIEM) system goes offline for maintenance or if the connection between the NSS and the SIEM is disrupted, the NSS buffers the logs and sends them when the connection is re-established. The amount of memory required to buffer the logs is incorporated into the VM spec computation. The buffer size increases proportionally to the amount of RAM allocated to the NSS.
To deploy your NSS virtual appliance, see the deployment guide for your platform:
- [NSS Deployment Guide for Amazon Web Services](/unified/nss-deployment-guide-amazon-web-services)
- [NSS Deployment Guide for Google Cloud Platform](/unified/nss-deployment-guide-google-cloud-platform)
- [NSS Deployment Guide for Microsoft Azure](/unified/nss-deployment-guide-microsoft-azure)
- [NSS Deployment Guide for VMware vSphere](/unified/nss-deployment-guide-vmware-vsphere)