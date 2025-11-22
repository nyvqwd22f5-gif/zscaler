# Red Hat Enterprise Linux 9 Migration for Private Service Edges
Source: https://help.zscaler.com/unified/red-hat-enterprise-linux-9-migration-private-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1496766.pdf

This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new  Private Service Edges can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the`/opt/zscaler/var` folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
- Requires ESXi version 7.0 Update 2 or newer, including ESXi 8.x.
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Create new [Private Service Edge groups](/unified/about-private-service-edge-groups-private-applications) and [provisioning keys](/unified/about-private-service-edge-provisioning-keys-private-applications) for each location.
Do not reuse existing provisioning keys as this will add the new RHEL 9 Private Service Edges to the old  Private Service Edge groups. Mixing different host OS and Zscaler software versions in a single group is not supported.
- Ensure that either:
- The **Default **setting of the **Version Profile** is inherited from the tenant default.
[See image.](#persistdisabled)
- You manually set the **Version Profile** to **Default** if **Persist Local Version Profile** is **Enabled**.
[See image.](#persistenabled)
-
(Optional) If you have old Private Service Edges (el7/el8), use the following commands before clearing the contents of `/opt/zscaler/var/`
`# systemctl stop zpa-service-edge
# yum remove zpa-service-edge
# rm -rf /opt/zscaler/var/service-edge/*`
- Follow the [step-by-step guide](/zpa/service-edge-deployment-guide-vmware) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
- Add trusted networks and enable **Publicly Accessible** (if applicable) on the new Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-01.png)
- (Optional) [Disable the Private Service Edge groups](/unified/editing-private-service-edge-groups-private-applications) 15 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
- During regional off hours, remove trusted networks and disable public access (if applicable) on CentOS 7 Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-02.png)
[]![Persist local version profile disabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-disabled-01.png)
[]![Persist local version profile enabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-enabled-01.png)