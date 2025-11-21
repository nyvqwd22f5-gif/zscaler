# Red Hat Enterprise Linux 9 Migration for App Connectors
Source: https://help.zscaler.com/zpa/app-connector-red-hat-enterprise-linux-9-migration
PDF: https://help.zscaler.com/pdf/com/en/1487736.pdf

This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new App Connectors can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the`/opt/zscaler/var` folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Use a current [provisioning key](/zpa/about-connector-provisioning-keys) or create a new [App Connector group](/zpa/about-connector-groups) with a provisioning key for each location.
- Verify the [version profile](/zpa/configuring-version-profile) is **Default**, **Previous Default**, or **New Release** by doing one of the following:
- If **Persist Local Version Profile** is **Disabled**, check the **Version Profile** that was inherited from the tenant.
[See image.](#persistdisabled)
- If **Persist Local Version Profile** is **Enabled**, select an option for the **Version Profile**.
[See image.](#persistenabled)
- Follow the [step-by-step guide](/zpa/connector-deployment-guide-vmware-platforms) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
-
Add the new App Connector groups to each respective server group.
![Edit server group.](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/edit-server-group-01.png)
- (Optional) [Disable the App Connector groups](/zpa/editing-connector-groups) 5 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
-
During regional off hours, remove the CentOS 7 App Connector groups.
![Add server group.](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/add-server-group-01.png)
[]![Persist local version profile disabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-disabled-01.png)
[]![Persist local version profile enabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-enabled-01.png)