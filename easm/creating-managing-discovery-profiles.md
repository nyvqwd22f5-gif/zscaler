# Creating & Managing Discovery Profiles
Source: https://help.zscaler.com/easm/creating-managing-discovery-profiles
PDF: https://help.zscaler.com/pdf/com/en/1503561.pdf

While setting up asset discovery, EASM allows you to configure seeds by creating a discovery profile. A discovery profile adds a layer of granular control to build the attack surface by including specific seeds. For each custom organization that you add, you can configure discovery profiles by adding seeds. To learn more, see [About Discovery Profiles](/easm/about-discovery-profiles).
Only admins with full access permissions can create and manage discovery profiles. To learn more, see [Creating and Managing Roles](/easm/creating-and-managing-roles).
The following sections explain how you can create and manage discovery profiles in the EASM Admin Portal. To learn how to configure and initiate asset discovery in EASM, see [Setting Up Asset Discovery](/easm/setting-up-asset-discovery).
[]Creating a Discovery Profile
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the **Organization **window:
- Locate and click the organization for which you want to create a discovery profile on the left pane.
-
Click the **Add Discovery Profile** button.
[See image.](#add-discovery-profile)
The **Profile Details** window appears.
- In the **Profile Details** window:
- **Name**: Enter a name for the discovery profile.
- **Description**: Enter a brief description for the profile.
- The **Scan Frequency** is automatically set to **Weekly** and is non-editable.
- Under **Manage Seeds** section:
-
Select the type of the seed asset by clicking the respective tab.
Currently, you can configure domains, IP addresses, and IP blocks as seed assets.
-
When you are in the respective tab for adding seeds of a specific asset type, you can add seeds for that particular asset type. To add the list of seeds that must be included in the discovery profile, enter the seed name in the text box provided under the **Include** section. To add multiple seeds manually, press `Enter` or click **Add** after specifying each item. Alternatively, you can import a list of seeds from a CSV file by using the **Upload File** option.
When you add the seeds manually, the seeds are displayed in a list under the **Include** section. To remove any seeds from the list, use the **Delete** icon that appears next to the seed name.
-
Click **Save**.
[See image.](#discovery-profile-configuration)
The discovery profile is saved and displayed under a new **Discovery Profile** tab created for the organization. Additionally, an **Included Seeds **tab, appears for the organization where you can view the list of seeds configured for the entire organization. You can view the list of seeds along with their name, domain type, and the discovery profile to which they are mapped.
[See image.](#discovery-profile)
When you submit the discovery profile, EASM starts scanning the internet for asset connections using the seeds to map your organization’s attack surface and build an inventory of the internet-exposed assets. This process typically takes 24–48 hours and then you can view the asset inventory and the associated risks identified for the assets within the EASM Admin Portal.
Managing a Discovery Profile
You can perform actions such as editing, disabling or enabling, and deleting discovery profiles within an organization. You can disable a discovery profile if you no longer want to monitor the inventoried assets or continue mapping the attack surface for a specific set of seeds. When a discovery profile is disabled, periodic scans for the inventoried assets are discontinued and the asset data and the associated risk information are no longer updated. Also, the asset discovery process using the seeds and their connections is suspended and no new asset links in the attack surface are identified.
After disabling a discovery profile, you can still view the asset and findings data reported henceforth via the discovery profile in the EASM Admin Portal. However, you cannot perform any actions on the data (e.g., changing asset status) or modify the discovery profile configuration, including the seeds.
If you no longer require the assets and findings data reported via a disabled discovery profile, you can take a further step to delete the discovery profile if needed. However, this action of deleting a discovery profile requires careful consideration about data backup and restoration before implementation. EASM allows you to download the list of assets and findings for an organization on the respective [Assets](/easm/about-asset-inventory) and [Findings](/easm/about-findings) page.
Zscaler recommends exercising great caution when disabling or deleting a discovery profile for the following reasons:
- If you disable a discovery profile, all scans defined within the profile are disabled. Only an admin user can re-enable the discovery profile.
- If you delete a discovery profile, all associated assets and findings data are permanently removed. This action cannot be reversed and the deleted data cannot be restored.
Editing a Discovery Profile
To edit a discovery profile:
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the **Organization** window, under the **Discovery Profile** tab:
- Locate the discovery profile that you want to modify and click the **Edit** icon displayed under the **Actions** column.
- Under **Profile Details**, you can make changes to the **Name** and **Description** fields as needed.
- Under **Manage Seeds**, you can select the respective tab for the seeds that you want to modify to add or remove seeds. To learn more about how to perform these actions, see [Creating a Discovery Profile](#creating-discovery-profile).
- Click **Save**.
Deleting a Discovery Profile
Exercise caution when deleting a discovery profile because this permanently deletes all associated components, including the historical assets and findings discovered and inventoried via the discovery profile. This action cannot be reversed and the deleted data cannot be restored.
You can delete only discovery profiles that have been disabled.
To delete a discovery profile:
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the **Organization** window under the **Discovery Profile** tab, locate the discovery profile that you want to delete and click the **Delete** icon displayed under the **Actions** column.
[]![The Add Discovery Profile button is annotated in EASM Admin Portal](/downloads/easm/asset-discovery/creating-managing-discovery-profiles/add-discovery-profile_0.png)
[]![The discovery profile configuration details in EASM Admin Portal](/downloads/easm/asset-discovery/creating-managing-discovery-profiles/easm-discovery-profile-configuration.png)
[]![The discovery profile list view with discovery profile configuration details in EASM](/downloads/easm/asset-discovery/creating-managing-discovery-profiles/easm-discovery-profile-details.png)