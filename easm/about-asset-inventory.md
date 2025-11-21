# About Asset Inventory
Source: https://help.zscaler.com/easm/about-asset-inventory
PDF: https://help.zscaler.com/pdf/com/en/1503566.pdf

Asset Discovery and Inventory are core functionalities of EASM that enable scanning the internet for identifying exposed assets and inventorying them periodically to provide actionable insights into the organization's external attack surface. The scanning process starts with one or more legitimate assets of the organization configured as seeds. The initial scan of the seeds brings up assets that are directly associated with the seeds, forming the first level of connections. Then the first level of connections are scanned to discover the second level of linked assets, and so on. This process of recursively scanning assets from each level of connection to the seed leads to the discovery of exposed assets sprawling up to the periphery of the organization's asset infrastructure with the seed at the center of the web of connections, ultimately mapping the attack surface of the organization. To learn more, see [Understanding Asset Discovery](/easm/understanding-asset-discovery).
Asset Inventory provides the following benefits and enables you to:
- Continuously scan and index internet-facing assets to maintain a detailed inventory of your organization's external attack surface, enabling proactive identification and monitoring of potentially vulnerable assets.
- Leverage risk insights associated with each discovered asset to prioritize risk mitigation efforts, ensuring that your organization addresses the most critical vulnerabilities effectively and efficiently.
All assets discovered through the scanning process are indexed, inventoried, and populated on the Assets page. Following the discovery process, the assets are investigated to identify the risks and vulnerabilities associated with them, and these risk insights are populated for the respective assets for further examination and risk mitigation. Furthermore, the assets are continuously monitored through periodic scans, and any changes in the asset's status and risk exposure are reflected on the Assets page.
About the Assets Page
On the Assets page, you can do the following:
- View the list of assets discovered by EASM for your organization. For each asset, you can view:
- **Name**: An identifier for the asset sourced from the scan. Depending on the type of asset, this field might contain a domain name, host name, IP address or IP block, web page URL, autonomous system number (ASN), or certificate ID.
- **Type**: The type of the asset classified as Domain, Host, Web Page, Certificate, ASN, IP Address, or IP Block.
- **Risk Level**: The risk level assigned to the asset from Minimum, Low, Medium, High, and Critical.
- **Findings Count**: The number of risk findings that are identified and tracked for the asset.
- **Status**: The status of the asset represented by the values Approved, Candidate, and Archived, indicating the relationship status between the asset and the organization for determining whether the asset must be included in subsequent scans.
- **First Seen**: The timestamp when the asset was first discovered in a scan.
- **Last Seen**: The timestamp when the asset was last observed in a scan.
- **UUID**: A Universally Unique Identifier (UUID) generated and assigned to the asset by EASM.
- [Click an asset record to view comprehensive details about the asset and its associated risk insights](/easm/understanding-asset-details).
- [Filter the asset data based on specific parameters such as Status, Risk Level, Last Seen, and Type](/easm/filtering-customizing-assets-page).
- [Modify the table and its columns](/easm/filtering-customizing-assets-page).
- [Download the list of all assets for the selected organization into a CSV file](/easm/downloading-assets).
- Search for an asset by name.
- Select a different organization for which you want to view the asset inventory details. The default organization is automatically selected when the Assets page is accessed.
- View the timestamp when the asset inventory details were last updated.
![The Assets page in EASM showing the assets discovered and inventoried for the selected organization](/downloads/easm/asset-inventory/about-asset-inventory/assets-about-page.png)