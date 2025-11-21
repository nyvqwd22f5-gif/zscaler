# Viewing the Cloud Assets Dashboard
Source: https://help.zscaler.com/zpc/viewing-cloud-assets-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1394181.pdf

Organizations deployed on the cloud have multiple assets running on their cloud infrastructure, such as web servers, databases, virtual machines, etc. Organizations are increasingly adopting cloud technologies. The rate at which your developers deploy or terminate assets across your cloud infrastructure poses an inventory management problem. The Cloud Assets Dashboard provides an overview of all your assets, cloud services, and cloud accounts in a single place. It aggregates important metrics such as Asset Risk Level and Asset Status across your entire cloud infrastructure.
The Cloud Assets provide the following benefits and enable you to:
- View a summary of all cloud assets separated into categories (Threats, Assets, Identities, Infrastructure as Code (IAC), Compliance, etc.).
- View a graph of the trends for the numbers of assets by cloud provider type.
- View charts that display Status and Risk Level of all cloud assets.
- View charts that show the top 10 Asset Types, Regions, and Categories.
Most dashboard widgets and icons are interactive. You can drill down to view the Cloud Assets Dashboard in more detail.
On the Cloud Assets Dashboard page (Dashboard > Cloud Assets), you can do the following:
- Filter assets by the following parameters:
- **Business Units**: Select one or multiple business units. Business units are logical groups of multiple cloud accounts.
- **Cloud Type**: Select one or multiple cloud service providers for which you want to view assets.
- **Account**: Select one or multiple cloud accounts for which you want to view cloud assets.
- **Regions**: Select one or multiple regions for which you want to view cloud assets.
- View the following Cloud Asset trend for your cloud deployment:
- **Cloud Type Trend**: View asset distribution across all cloud types for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, last 90 days).
- **Status Posture Trend**: View asset status trend for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, last 90 days)
- View the **Cloud Type** donut chart:
- View the total number of assets and number of assets across all cloud service providers.
The total number of assets is the total number of assets ingested by ZPC in terms of metadata collection.
- Click the cloud type to view all assets of the cloud type on the [Cloud Assets](/zpc/about-cloud-assets) page.
- View the **Asset Status** donut chart:
- View the total number of assets that are being evaluated or those that have policies (either predefined or custom) in ZPC.
- View if an asset has failed or passed for all the assets protected by ZPC. An asset fails even if a single security policy against it fails.
- View the** Risk Level by Assets **donut chart:
- View the total number of assets evaluated based on the risk level of open alerts.
- Asset risk level is separated into **Low**, **Medium**, **High**, and **Critical**.
- View **Top 10 Asset Types by Asset**: View top 10 Asset Types with the highest number of assets.
- View **Top 10 Regions by Assets**: View top 10 regions with the highest number of assets.
- View **Top 10 Categories by Assets**: View top 10 Asset Categories with the highest number of assets.
[![View the Cloud Asset Dashboard on ZPC](/downloads/zpc/dashboards/about-cloud-assets-dashboard/zpc-cloud-assets-dashboard.png)
](undefined)