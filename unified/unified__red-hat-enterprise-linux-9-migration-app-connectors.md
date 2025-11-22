# Red Hat Enterprise Linux 9 Migration for App Connectors
Source: https://help.zscaler.com/unified/red-hat-enterprise-linux-9-migration-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496171.pdf

This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new App Connectors can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the`/opt/zscaler/var` folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Create new [App Connector groups](/unified/about-app-connector-groups) and [provisioning keys](/unified/about-app-connector-provisioning-keys) for each location.
Do not reuse existing provisioning keys as this will add the new RHEL 9 App Connectors to the old App Connector groups. Mixing different host OS and Zscaler software versions in a single group is not supported.
- Ensure that either:
- The **Default **setting of the **Version Profile** is inherited from the tenant default.
[See image.](#persistdisabled)
- You manually set the **Version Profile** to **Default **if **Persist Local Version Profile** is **Enabled**.
[See image.](#persistenabled)
-
(Optional) If you have old App Connectors (el7/el8), use the following commands before clearing the contents of `/opt/zscaler/var/`
`# systemctl stop zpa-connector
# yum remove zpa-connector
# rm -rf /opt/zscaler/var/*`
- Follow the [step-by-step guide](/unified/app-connector-deployment-guide-vmware-platforms) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
-
Add the new App Connector groups to each respective server group.
![Edit server group.](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/edit-server-group-01.png)
- (Optional) [Disable the App Connector groups](/unified/editing-app-connector-groups) 5 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
-
During regional off hours, remove the CentOS 7 App Connector groups.
![Add server group.](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/add-server-group-01.png)
[]![Persist local version profile disabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-disabled-01.png)
[]![Persist local version profile enabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-enabled-01.png)