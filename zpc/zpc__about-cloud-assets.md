# About Cloud Assets
Source: https://help.zscaler.com/zpc/about-cloud-assets
PDF: https://help.zscaler.com/pdf/com/en/1394206.pdf

Organizations deployed in the cloud have multiple assets, such as web servers, databases, virtual machines (VMs), etc., running on their cloud infrastructure. Organizations are increasingly adopting multi-cloud service providers (CSPs) and are quickly deploying or terminating assets across their cloud infrastructure. Deploying or terminating assets poses an inventory management problem to security administrators.
ZPC collects asset configuration metadata across all CSPs, aggregates this data, and provides an inventory of all assets deployed on your cloud infrastructure (i.e., assets not protected by ZPC and assets that are protected by ZPC) using security policies. ZPC offers complete visibility across your cloud deployment, so you can easily identify and fix misconfigured assets.
Cloud asset data provides the following benefits and enables you to:
- View asset configuration metadata that's collected across all CSPs.
- Have complete visibility across your cloud deployment to easily identify and fix misconfigured assets.
The cloud assets are grouped by:
- Asset Types: CSP-defined services such as EC2 instances in AWS or VMs in Microsoft Azure.
- Asset Categories: ZPC-specific aggregations for similar asset types across all CSPs. For example, the VMs and EC2 instances belong to the Compute Asset category.
About the Cloud Assets Page
On the Cloud Assets page (Cloud Posture > Cloud Assets), you can do the following:
- Select an Asset Category to view all Asset Types in the Asset Category.
- Filter assets using available parameters. To learn more, see [Using Filters](/zpc/using-filters).
- Switch between viewing all Asset Categories and all Asset Types.
- Search for Asset Types or Asset Categories.
- Select an Asset Type to view all its assets and the following details:
- **Asset Name**: The name of the asset. Click to view [more details](/zpc/about-cloud-asset-details).
-
**Asset ID**: The cloud asset ID.
Azure Asset IDs are displayed in lowercase, regardless of the case in which they are originally created.
- **Cluster**: The Kubernetes cluster to which this asset belongs (if applicable).
- **Namespace**: The namespace to which this asset belongs (if applicable).
- **Account ID**: The cloud account ID.
- **Discovered On**: The date and time when the asset was first discovered by ZPC.
- **Last Modified On**: The date and time when the asset was last modified.
- **Risk Level**: The severity of the risk.
- **Asset Region**: The region where the asset is deployed.
- **Asset Compliance Status**: Whether the asset has passed, failed, or ignored [security policies](/zpc/about-security-policies) associated with it.
- **Publicly Exposed**: Whether the asset is publicly exposed or not.
- **Trusted IP**: Whether the asset is associated with a trusted IP list or not.
- **Alerts**: The number of [open alerts](/zpc/about-alert-status) for the asset.
- **Vulnerabilities**: The number of [vulnerabilities](/zpc/viewing-vulnerability-details) present on the asset.
[See image.](#cloud-asset-type)
- [Select and apply saved filters](/zpc/using-filters).
- [Hide the filters](/zpc/using-filters).
- Export the cloud asset details as an Excel file and download the report. To learn more, see [Downloading Reports](/zpc/downloading-reports).
![View the Cloud Assets](/downloads/zpc/cloud-posture/cloud-assets/about-cloud-assets/zpc-cloud-assets-page.png)
[![View the Cloud Asset Types](/downloads/zpc/cloud-posture/cloud-assets/about-cloud-assets/zpc_asset_types_table.png)
]