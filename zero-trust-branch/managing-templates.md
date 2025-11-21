# Managing Templates
Source: https://help.zscaler.com/zero-trust-branch/managing-templates
PDF: https://help.zscaler.com/pdf/com/en/1525136.pdf

In a large-scale global deployment of Zero Trust Branch, managing each site individually is time-consuming and prone to errors. Zscaler provides a set of templates so that you can build sites quickly. You can also create custom templates based on the default set. Templates support both standalone and high-availability configurations.
After you have created or selected the template you want to use, see[ Adding a Site](/zero-trust-branch/adding-site) to create a site using that template.
Predefined Templates
To start creating Zero Trust Branch sites, Zscaler provides templates for virtual machine (VM) and supported devices in both standalone and high-availability configurations. To learn more, see [Deployment Overview](/zero-trust-branch/deployment-overview).
You cannot delete or edit default templates, but you can clone them.
Managing Templates
You can perform the following actions from the Templates (Resources > Templates) page:
- [Add a New Template](#add)
- [Edit a Template](#edit)
- [Clone a Template](#clone)
- [Delete a Template](#delete)
[]To add a new template:
-
Click **Add Template** in the upper-right corner.
[See image.](#templates)
-
In the** Add Template** panel:
- **Name**: Enter a name to identify the template.
- **Primary DNS**: Enter the IP address of the primary DNS for this template.
- **Secondary DNS**: (Optional) Enter the IP address of the secondary DNS for this template.
- **DHCP Service**: If this template is for a DHCP server, select **server**; for a relay to a server, select **relay**.
- **Deployment Type**: Select **standalone **if this template is to be used for standalone sites or **standard_mode_ha** for high-availability sites.
- **Platform [Gateway-1]:** Select the platform this template will be used for: either **vm **for a VM or the device type.
- **Platform [Gateway-2]**: If you select a high-availability deployment, select the platform for the secondary gateway. You can have a different platform (e.g., VM for an appliance) for the secondary gateway.
- **NAT Enabled**: Enable if your Zero Trust Branch appliance uses NAT to route traffic leaving the branch appliance toward the non-Zero Trust Branch network.
[See image.](#add-template)
- Click **Save**.
[]To edit a template:
- Click the **Gear **icon next to a template and select **Edit**.
-
In the **Edit Template **panel:
- **Name**: Enter a name to identify the template.
- **Primary DNS**: Specify the primary DNS for this template.
- **Secondary DNS**: (Optional) Specify a secondary DNS for this template.
- **DHCP Service**: If this template is for a DHCP server, select **server**; for a relay to a server, select **relay**.
- **NAT Enabled**: Enable if your Zero Trust Branch appliance uses NAT to route traffic leaving the branch appliance toward the non-Zero Trust Branch network.
[See image.](#edit-template)
- Click **Save**.
[]To clone a template:
- Click the **Gear **icon next to a template and select **Clone**.
- Enter a name for the cloned template and click **Save**.
[]To delete a template:
- Click the **Gear **icon next to a template and select **Delete**.
- In the **Delete **dialog box, enter `DELETE` and click **Confirm **to delete the template.
[]
![Templates page](/downloads/device-segmentation/administration/resources/managing-templates/templates.png)
[]
![Add Template panel](/downloads/device-segmentation/administration/resources/managing-templates/add-template.png)
[]
![Edit Template panel](/downloads/device-segmentation/administration/resources/managing-templates/edit-template.png)