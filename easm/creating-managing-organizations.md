# Creating & Managing Organizations
Source: https://help.zscaler.com/easm/creating-managing-organizations
PDF: https://help.zscaler.com/pdf/com/en/1503551.pdf

EASM allows you to add custom organizations to help keep your attack surface discovery and inventory management separate for distinct entities, subsidiaries, or business verticals that are part of your company. For each custom organization, you can configure distinct discovery profiles by adding seeds, which are known legitimate assets belonging to that specific organization. A discovery profile adds a layer of granular control to build the attack surface by including specific seeds. To learn more, see [Understanding Asset Discovery](/easm/understanding-asset-discovery).
EASM provides a default organization out of the box, which you can configure to set up your discovery profile. Additionally, if your organization uses Zscaler's Risk Management platform, Risk360, and if you have a Risk360 tenant, an organization is created for you in the EASM Admin Portal through the seamless integration between Risk360 and EASM. To learn more, see [What is Risk360?](/risk360/what-risk360)
Only super admins can create and manage organization-specific configurations.
The following sections explain how you can add and manage organizations in the EASM Admin Portal. To learn more about how to configure asset discovery in EASM, see [Setting Up Asset Discovery](/easm/setting-up-asset-discovery).
Adding an Organization
To add a new organization:
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
-
In the **Organization** window:
-
Click the **Add** icon on the left pane. If this is your first organization, you can alternatively use the **Add Organization** button.
A text box to enter the name for the organization appears on the left pane.
-
Enter a name for the organization in the text box and click the **Tick** icon.
[See image.](#add-org)
A new organization is added with options to configure the discovery profile and other details for the organization shown on the right side. By default, the organization is enabled and this is required to initiate the asset discovery scan. To learn about discovery profiles, see [About Discovery Profiles](/easm/about-discovery-profiles).
[See image.](#new-org)
Managing an Organization
You can perform actions such as editing, disabling or enabling, and deleting the organizations added to the EASM Admin Portal. You can disable an organization if you no longer want to monitor the inventoried assets or continue mapping the organization's attack surface. When an organization is disabled:
- all discovery profiles configured for the organization are disabled.
- periodic scans for the inventoried assets performed via the discovery profiles are also discontinued and the asset data and the associated risk information are no longer updated.
- the asset discovery process using the seeds within the discovery profiles and their connections is suspended, and no new asset links in the organization’s attack surface are identified.
After disabling an organization, you can still view the assets and findings data reported henceforth for the organization in the EASM Admin Portal. However, you cannot perform any actions on the data (e.g., changing asset status) or modify any organization details. If you want to disable scans performed through specific discovery profiles, you can disable that discovery profile instead. To learn more, see [Creating & Managing Discovery Profiles](/easm/creating-managing-discovery-profiles).
If you no longer require the historical assets and findings data reported for a disabled organization, you can take a further step to delete the organization if needed. However, this action of deleting an organization requires careful consideration about data backup and restoration before implementation. EASM allows you to download the list of assets and findings for an organization on the respective [Assets](/easm/about-asset-inventory) and [Findings](/easm/about-findings) pages.
Zscaler recommends exercising great caution when disabling or deleting an organization for the following reasons:
- If you disable an organization, all associated discovery profile scans are disabled and the admins are locked out of the organization.
- If you delete an organization, all associated components, including the historical assets and findings that were discovered and inventoried for that organization, are permanently removed. This action cannot be reversed and the deleted data cannot be restored.
Editing an Organization
To modify the name or the status of an organization:
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the Organization window, locate and click the organization for which you want to make changes.
- You can make the following changes to the organization:
- To modify the name of the organization, click the **Edit** icon, modify the name in the text box, and click the **Tick** icon to save the changes.
- To disable or re-enable the organization, use the **Enabled** slider provided and confirm your action in the confirmation pop-up window.
Deleting an Organization
Exercise caution when deleting an organization because this would permanently delete all associated components, including historical assets and findings discovered and inventoried for the organization. This action cannot be reversed and the data deleted cannot be restored.
You can only delete organizations that have been disabled. To delete an organization:
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the Organization window, locate and click the organization for which you want to make changes.
-
Click the **More** icon on the top-right corner of the page and click **Delete**.
A confirmation window appears.
- In the confirmation window, click **Delete**.
[]![Add EASM organization for attack surface discovery and management](/downloads/easm/asset-discovery/creating-managing-organizations/easm-add-organization_0.png)
[]![EASM organization added for attack surface discovery and management](/downloads/easm/asset-discovery/creating-managing-organizations/easm-organization_0.png)