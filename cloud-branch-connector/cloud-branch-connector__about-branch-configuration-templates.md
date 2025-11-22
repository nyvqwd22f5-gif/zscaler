# About Branch Configuration Templates
Source: https://help.zscaler.com/cloud-branch-connector/about-branch-configuration-templates
PDF: https://help.zscaler.com/pdf/com/en/1420651.pdf

[Watch a video about Branch Configuration Templates.](https://fast.wistia.net/embed/iframe/fip1hlj1kl)
The Branch Connector configuration template is required for both virtual machines (VMs) and hardware devices. The configuration template provides configuration information for virtual and physical branch devices, and the configuration URL is required for deploying both virtual and physical branch devices. For virtual branch devices, the administrator provides the configuration URL to the virtual device. For physical branch devices, the Zero Touch Provisioning process retrieves the configuration URL.
Branch Connector Configuration Templates provide the following benefits and enable you to:
- Configure your Branch Connector instances.
- Set up high-availability deployment.
- Set the Zero Trust Branch Device to run as an inline gateway or non-gateway (One-Arm Mode).
- Preconfigure your Zero Trust Branch Devices for Zero Touch Provisioning.
About the Branch Connector Configuration Template Page
On the Branch Configuration Templates page (Administration > Provisioning & Configuration > Branch Configuration), you can do the following:
- [Add Branch Connector Configuration Template](/cloud-branch-connector/configuring-branch-provisioning-template).
- View a list of all branch configuration templates that are configured for your organization.
- **Template Name**: The name of the template.
- **Branch Type**: The hypervisor host (i.e., **Red Hat Linux**, **VMware ESXi**, or **Microsoft Hyper-V**) or the hardware device (**ZT400**, **ZT600**, or **ZT800**) of the template.
- **Gateway**: The status of whether the hardware device was deployed as a gateway (i.e., **Yes** or **No**). Gateway mode is only supported on hardware devices.
- **Serial Number**: The serial number of the hardware device.
- **Status**: The status of the deployment template (i.e., **Staged**, **Not Deployed**, or **Deployed**).
- **VM Size**: The size of the virtual machine. This field only applies to VMs.
- **Last Modified By**: The last admin to modify the template.
- **Last Modified On**: The date and time when the template was last modified.
- Click the arrow in the **Template Name** field to copy the branch configuration URL.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items#edit) the branch configuration template. Branch configuration templates are editable before and after provisioning and deployment.
- [Delete](/cloud-branch-connector/editing-deleting-or-duplicating-items#delete) the branch configuration template.
- View the settings of the branch configuration template.
- Modify the table and its columns.
- Search for a branch configuration template.
- View the [Cloud Provisioning Template](/cloud-branch-connector/about-cloud-provisioning-templates) page.
![The Branch Configuration Template page](/downloads/cloud-branch-connector/administration/provisioning-configuration/about-branch-configuration-templates/About%20Branch%20Configuration%20Templates%20MVP1.png)