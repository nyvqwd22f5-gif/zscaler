# Red Hat Enterprise Linux 9 Migration for Private Service Edges
Source: https://help.zscaler.com/zpa/zpa-private-service-edge-red-hat-enterprise-linux-9-migration
PDF: https://help.zscaler.com/pdf/com/en/1487746.pdf

This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new ZPA Private Service Edges can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the`/opt/zscaler/var` folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
- Requires ESXi version 7.0 Update 2 or newer, including ESXi 8.x. To learn more about ESXi support, see [End-of-Support for VMware vSphere Hypervisor (ESXi) Version 5.5](/eos-eol/end-support-vmware-vsphere-hypervisor-esxi-version-5.5).
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Use a current [provisioning key](/zpa/about-zpa-service-edge-provisioning-keys) or create a new [ZPA Private Service Edge group](/zpa/about-zpa-private-service-edge-groups) with a provisioning key for each location.
- Verify the [version profile](/zpa/configuring-version-profile) is **Default**, **Previous Default**, or **New Release** by doing one of the following:
- If **Persist Local Version Profile** is **Disabled**, check the **Version Profile** inherited from the tenant.
[See image.](#persistdisabled)
- If **Persist Local Version Profile** is **Enabled**, select an option for the **Version Profile**.
[See image.](#persistenabled)
- Follow the [step-by-step guide](/zpa/service-edge-deployment-guide-vmware) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
- Add trusted networks and enable **Publicly Accessible** (if applicable) on the new ZPA Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-01.png)
- (Optional) [Disable the ZPA Private Service Edge groups](/zpa/editing-service-edge-groups) 15 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
- During regional off hours, remove trusted networks and disable public access (if applicable) on CentOS 7 ZPA Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-02.png)
[]![Persist local version profile disabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-disabled-01.png)
[]![Persist local version profile enabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-enabled-01.png)