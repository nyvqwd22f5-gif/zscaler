# About Discovery Profiles
Source: https://help.zscaler.com/easm/about-discovery-profiles
PDF: https://help.zscaler.com/pdf/com/en/1503556.pdf

EASM requires you to configure seed assets to initiate the scan for discovering your internet-facing assets. The seeds are known legitimate assets of your organization that are used as the first and central node in a series of asset connections that are discovered across your online asset infrastructure using recursive scanning, including assets that might otherwise be unknown or left unmonitored. While setting up asset discovery, EASM allows you to configure seeds by creating a discovery profile. A discovery profile adds a layer of granular control to build the attack surface by including specific seeds. To learn more, see [Understanding Asset Discovery](/easm/understanding-asset-discovery).
Discovery profiles provide the following benefits and enable you to:
- Configure discovery profiles with specific seed assets to tailor your attack surface mapping, ensuring all internet-facing assets—including those that might be overlooked—are identified and monitored effectively.
- Manage discovery and asset inventory for different entities within your organization (such as subsidiaries or business verticals) separately, allowing for more organized and efficient management of each entity’s unique attack surface.
In addition, EASM allows you to set up [organizations](/easm/creating-managing-organizations) to help keep your attack surface discovery and inventory management separate for distinct entities, such as parent companies, subsidiaries, acquisitions, or business verticals that are part of your business enterprise. For each organization, you can configure distinct discovery profiles by configuring seeds using known legitimate assets of that specific organization.
About the Discovery Profiles Page
On the Discovery Profiles page (Administration > Organization > [Organization Name]), you can do the following:
-
[Create a new discovery profile.](/easm/creating-managing-discovery-profiles)
Currently, only one discovery profile can be configured for an organization. When a discovery profile is added, the **Add New Discovery** button disappears.
- View the list of discovery profiles configured for the organization. For each discovery profile, you can see:
- **Name**: The name of the discovery profile.
- **Included Seeds**: The seeds that are included in the asset scan performed via the discovery profile.
- **Last Scan**: The timestamp when the last scan was performed via the discovery profile.
- **Duration**: The time taken for the last discovery scan to run to completion.
- **Frequency**: The frequency of asset scan.
- **Status**: The status of the discovery profile indicating whether it is enabled or disabled.
- [Edit a discovery profile or modify its status.](/easm/creating-managing-discovery-profiles)
- [Delete a discovery profile that has already been disabled.](/easm/creating-managing-discovery-profiles)
- Modify the table and its columns.
- Go to the **Included Seeds** tab.
![Add Discovery Profile in EASM](/downloads/easm/asset-discovery/about-discovery-profiles/add-new-discovery-profile.png)
![The Discovery Profile page with a list of discovery profiles added for an organization in EASM Admin Portal](/downloads/easm/asset-discovery/about-discovery-profiles/about-discovery-profiles_0.png)