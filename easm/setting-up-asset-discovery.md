# Setting Up Asset Discovery
Source: https://help.zscaler.com/easm/setting-up-asset-discovery
PDF: https://help.zscaler.com/pdf/com/en/1503546.pdf

Asset Discovery, a core function of EASM, enables an organization to identify and inventory all their internet-facing assets and gain insights into an organization's external attack surface. To initiate a scan and discover assets, EASM requires seeds. A seed is a known legitimate asset of your organization. Domains, IP addresses, and IP blocks are assets that can be configured as seeds. While setting up asset discovery, EASM allows you to configure seeds by creating a [discovery profile](/easm/about-discovery-profiles). A discovery profile adds a layer of granular control to build the attack surface by including specific seeds. In addition, EASM allows you to set up [organizations](/easm/creating-managing-organizations) to help keep your attack surface discovery and inventory management separate for distinct entities, such as parent companies, subsidiaries, or acquisitions that are part of your company. For each organization, you can configure distinct discovery profiles with seeds for known legitimate assets of that specific organization.
When a discovery profile is created and submitted, EASM initially scans the configured seeds to discover assets that are immediately connected to the seeds. Then the first level of connections are scanned further to discover a second level of connected assets, followed by each consecutive level of connections being recursively scanned, leading up to the formation of a discovery chain and ultimately mapping the organization's attack surface. The assets discovered in each level of connections are evaluated to determine if their relationship with the previous seed is strong enough before being recursively scanned to discover subsequent connections. This recursive scanning continues until the weak links exposed in your online infrastructure, including unknown and unmonitored assets, are discovered. The scanning stops when all the internet-facing assets which your organization is responsible for managing are identified and tracked.
After discovering and inventorying the assets, EASM investigates a number of asset parameters to identify the associated risks, such as known vulnerabilities, misconfigurations, exposed credentials, sensitive enterprise information, etc. that can be potentially exploited as attack vectors. EASM continuously monitors the discovered assets and the changing attack landscape using periodic scans to provide real-time visibility into the risk exposure of your internet-facing asset infrastructure and to help prioritize risks with contextual and actionable information for risk remediation.
You need to complete the following steps to enable EASM to start discovering your internet-facing assets and building visibility into the attack surface:
- [1. Set up an organization.](#add-organization)
- [2. Create a discovery profile for the organization by including seeds.](#create-discovery-profile)
[]EASM provides a default organization out of the box, which you can configure to set up your discovery profile. Additionally, if your organization uses Zscaler's Risk Management platform, [Risk360](/risk360/what-risk360), and if you have a Risk360 tenant, an organization is created for you in the EASM Admin Portal through the seamless integration between Risk360 and EASM. You can also add custom organizations per your requirements.
To add a custom organization:
Only super admins can create and manage organization-specific configurations.
-
Go to **Administration** > **Organizations**.
The Organization window appears.
-
In the **Organization** window:
-
Click the **Add** icon on the left pane. If this is your first organization, you can alternatively use the **Add Organization** button.
A text box to enter the name for the organization appears on the left pane.
-
Enter a name for the organization in the text box and click the **Tick** icon.
[See image.](#add-org)
A new organization is added with options to configure the discovery profile and other details for the organization shown on the right side. By default, the organization is enabled and this is required to initiate the asset discovery scan.
[See image.](#new-org)
After creating an organization, you can set up a discovery profile for the organization. To learn more, see [Creating & Managing Organizations](/easm/creating-managing-organizations).
[]To create a discovery profile for an organization:
Only admins with full access permission to the target organization can perform this action.
-
Go to **Administration** > **Organizations**.
The **Organization** window appears.
- In the **Organization** window:
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
When you add the seeds manually, the seeds are displayed in a list under the **Include **section. To remove any seeds from the list, use the **Delete** icon that appears next to the seed name.
-
Click **Save**.
[See image.](#configure-discovery-profile)
When you save the discovery profile, EASM starts scanning the internet for asset connections using the seeds to map your organization's attack surface and build an inventory of the internet-exposed assets. This process typically takes 24–48 hours and then you can view the asset inventory and the associated risks identified for the assets within the EASM Admin Portal.
The discovery profile is saved and displayed under a new **Discovery Profile** tab created for the organization. Additionally, an **Included Seeds** tab appears for the organization where you can view the list of seeds configured for the entire organization. To learn more, see [Configuring & Managing Discovery Profiles](/easm/creating-managing-discovery-profiles).
[See image.](#discovery-profile-details)
[]![Adding a new organization for attack surface discovery and management](/downloads/easm/asset-discovery/setting-up-asset-discovery/easm-add-organization_0.png)
[]![New organization added for attack surface discovery and management](/downloads/easm/asset-discovery/setting-up-asset-discovery/easm-organization_0.png)
[]![The Add Discovery Profile button is annotated](/downloads/easm/asset-discovery/setting-up-asset-discovery/add-discovery-profile_1.png)
[]![Creating discovery profile by configuring seeds in EASM](/downloads/easm/asset-discovery/setting-up-asset-discovery/easm-discovery-profile-configuration_0.png)
[]![Discovery profile details in EASM Admin Portal](/downloads/easm/asset-discovery/setting-up-asset-discovery/easm-discovery-profile-details.png)