# App Connector Software by Platform
Source: https://help.zscaler.com/unified/app-connector-software-platform
PDF: https://help.zscaler.com/pdf/com/en/1496096.pdf

App Connectors are supported on [many different platforms](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms). Each supported platform has an App Connector image you can use to deploy App Connectors on that platform. To learn more, see [App Connector Deployment Guides for Supported Platforms](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) for detailed deployment instructions.
The following platforms support App Connector software packages. Where applicable, see the download links for images, public keys, and checksums.
[](/unified/app-connector-deployment-guide-nutanix-ahv)
[](https://dist.private.zscaler.com/vms/VMware/2024.12/zpa-connector-el9-2024.12.ova)
[](https://dist.private.zscaler.com/vms/VMware/2024.12/zpa-connector-el9-2024.12.ova.sha256sum)
[](/unified/app-connector-deployment-guide-vmware-platforms)
[](https://dist.private.zscaler.com/vms/VMware/2024.12/zpa-connector-el9-2024.12.ova)
[](https://dist.private.zscaler.com/vms/VMware/2024.12/zpa-connector-el9-2024.12.ova.sha256sum)
[](/unified/app-connector-deployment-guide-amazon-web-services#deploy)[](https://aws.amazon.com/marketplace/pp/prodview-cvvqe5hxw2bku?sr=0-1&ref_=beagle&applicationId=AWSMPContessa)[](/unified/app-connector-deployment-guide-google-cloud-platform)[](https://console.cloud.google.com/marketplace/product/zpa-gcp-marketplace/zscaler-private-access-connector)[](/unified/app-connector-deployment-guide-microsoft-azure#Deployment)[](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/zscaler.zscaler-private-access?tab=overview)[](/unified/app-connector-deployment-guide-docker)[](https://hub.docker.com/r/zscaler/zpa-connector/tags?page=1&ordering=last_updated)[](/unified/app-connector-deployment-guide-kubernetes)[](/unified/app-connector-deployment-guide-kubernetes)[](/unified/app-connector-deployment-guide-openshift)[](/unified/app-connector-deployment-guide-openshift)[](/unified/app-connector-deployment-guide-linux)
- [](https://yum.private.zscaler.com/yum/el8/zpa-connector-25.42.4-1.el8.x86_64.rpm)
- [](https://yum.private.zscaler.com/yum/el8/gpg)
- [](https://yum.private.zscaler.com/yum/el9/zpa-connector-25.42.4-1.el9.x86_64.rpm)
- [](https://yum.private.zscaler.com/yum/el9/gpg)
[](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x)
| Platform | Software |
| -------- | -------- |
| Colocation / Data Centers |
| Nutanix AHV | STIG OVASTIG OVA checksum |
| VMware | STIG OVASTIG OVA checksum |
| Clouds |
| Amazon Web Services (AWS) | ZPA - AWS Marketplace (STIG Image) |
| Google Cloud Platform (GCP) | ZPA - GCP Marketplace (STIG Image) |
| Microsoft Azure | ZPA - Azure Marketplace (STIG Image) |
| Containers |
| Docker | Docker Hub |
| Kubernetes | To learn more, see the App Connector Deployment Guide for Kubernetes. |
| OpenShift | A Helm Chart must be installed in order to deploy an App Connector on OpenShift. To learn more, see the App Connector Deployment Guide for OpenShift. |
| Linux Operating Systems |
| App Connector Deployment Guide for Linux | The following RPM package is supported for RHEL App Connector deployments:RHEL 8-based:RPM packageGPG public keyRHEL 9-based:RPM packageGPG public keyYou must have the RHEL operating system deployed and running. To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x. |