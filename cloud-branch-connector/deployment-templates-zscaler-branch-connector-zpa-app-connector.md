# Deployment Templates for Branch Connector & App Connector
Source: https://help.zscaler.com/cloud-branch-connector/deployment-templates-zscaler-branch-connector-zpa-app-connector
PDF: https://help.zscaler.com/pdf/com/en/1444481.pdf

Infrastructure as Code (IaC) deployment templates are available in [GitHub](https://github.com/zscaler) to assist in the deployment of Zscaler Branch Connector or Branch Connector & App Connector in VMware ESXi or Linux KVM. Infrastructure as Code (IaC) deployment templates are not available for Branch Connector deployment on Hyper-V platforms.
Downloading a Branch Connector image or a Branch Connector & App Connector image is one of the tasks you must complete before deployment. To learn more, see [Downloading Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images).
VMware ESXi Deployment Templates
You can use the following deployment templates for VMware ESXi:
- [Terraform](https://github.com/zscaler/terraform-esxi-branch-connector-modules): Use this repository to create the deployment resources required to deploy and operate Branch Connector or Branch Connector & App Connector.
- [Starter Deployment Template](#Template-1)
- [Starter Deployment Template with High-Availability](#Template-2)
- [Starter Deployment Template with App Connector](#Template-3)
- [Starter Deployment Template with App Connector and High-Availability](#Template-4)
[]Use the Starter Deployment Template (bc) to deploy your Branch Connector. The following resources are created:
- Zscaler Branch Connector virtual machine (VM)
- Key pair for SSH access
- Management interface
- Service interface
[]Use the Starter Deployment Template with High-Availability (bc_ha) to deploy your Branch Connector with high availability. The following resources are created:
- Two Zscaler Branch Connector VMs
- Key pair for SSH access
- Two Management interfaces
- Two Service interfaces
[]Use the Starter Deployment Template with App Connector (bc_ac) to deploy your Branch Connector & App Connector. The following resources are created:
- Zscaler Branch Connector VM
- Key Pair for SSH access
- Management interface
- Service interface
- Control interface
- App Connector provisioning key
[]Use the Starter Deployment Template with App Connector and High-Availability (bc_ha_ac) to deploy your Branch Connector & App Connector with high availability. The following resources are created:
- Two Zscaler Branch Connector VMs
- Key pair for SSH access
- Two Management interfaces
- Two Service interfaces
- Two Control interfaces
- App Connector provisioning key
Linux Deployment Templates
You can use the following deployment templates for Linux:
- [Terraform](https://github.com/zscaler/terraform-libvirt-branch-connector-modules): Use this repository to create the deployment resources required to deploy and operate Branch Connector or Branch Connector & App Connector.
- [Starter Deployment Template](#Template-5)
- [Starter Deployment Template with High-Availability](#template-6)
- [Starter Deployment Template with App Connector](#template-7)
- [Starter Deployment Template with App Connector and High-Availability](#template-8)
[]Use the Starter Deployment Template (bc) to deploy your Branch Connector. The following resources are created:
- Zscaler Branch Connector VM
- Key pair for SSH access
- Management interface
- Service interface
- Cloud-init provisioning ISO
- KVM storage volume
[]Use the Starter Deployment Template with High-Availability (bc_ha) to deploy your Branch Connector with high availability. The following resources are created:
- Two Zscaler Branch Connector VMs
- Key pair for SSH access
- Two Management interfaces
- Two Service interfaces
- Two Cloud-init provisioning ISOs
- Two KVM storage volumes
[]Use the Starter Deployment Template with App Connector (bc_ac) to deploy your Branch Connector & App Connector. The following resources are created:
- Zscaler Branch Connector VM
- Key pair for SSH access
- Management interface
- Service interface
- Control interface
- Cloud-init provisioning ISO
- KVM storage volume
- App Connector provisioning key
[]Use the Starter Deployment Template with App Connector and High-Availability (bc_ha_ac) to deploy your Branch Connector & App Connector with high availability. The following resources are created:
- Two Zscaler Branch Connector VMs
- Key pair for SSH access
- Two Management interfaces
- Two Service interfaces
- Two Control interfaces
- Two Cloud-init provisioning ISOs
- Two KVM storage volumes
- App Connector provisioning key