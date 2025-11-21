# About SIMs
Source: https://help.zscaler.com/zscaler-cellular/about-sims
PDF: https://help.zscaler.com/pdf/com/en/1519081.pdf

The SIMs page provides a comprehensive list of all Zscaler SIMs—both physical SIMs and eSIMs—provisioned to your organization. This page allows you to view essential details and statuses, and manage your Zscaler SIMs.
The SIMs page provides the following benefits and enables you to:
- View critical information for each SIM, such as ICCID, IMEI, IP address, and data usage, and track its status and connectivity.
- Identify high-usage or offline SIMs. Use this information to address issues proactively and ensure seamless connectivity or update the SIM status.
About the SIMs Page
On the SIMs page (left-side navigation > SIMs), you can do the following:
- [Filter the SIMs page based on different parameters](/zscaler-cellular/filtering-customizing-tables).
- Refresh the page to fetch and show the latest data. This action does not remove the applied filters.
- Update [SIM Status](/zscaler-cellular/changing-status-zscaler-sims) or [IMEI](/zscaler-cellular/changing-imei-association-zscaler-sims) for multiple SIMs. This option is displayed only when a SIM card is selected.
- Download the list of all SIMs and their details as a CSV file for the current view. If filters are applied, the downloaded file contains only the details of the SIMs that are shown for the selected filters.
- View the total data usage across all SIMs in the current view. If filters are applied, the Total Usage field shows only the data across the SIMs that match the applied filters.
-
View the list of all Zscaler SIMs provisioned for your organization. For each SIM, you can see:
- **ICCID**: The Integrated Circuit Card Identifier is a globally unique identifier assigned to each SIM card. It is used to track and manage the SIM within the network infrastructure.
- **IMEI**:** **The International Mobile Equipment Identity is a unique identifier for the mobile device associated with the SIM card. It helps with identifying and managing the devices in the network.
- **IP Address**: The IP address assigned to the device using the SIM card, allowing it to connect and communicate over the internet.
- **Form Factor**: The type of SIM, indicating whether it is a physical SIM or an eSIM.
- **Device Manufacturer**: The name of the company that produces the device associated with the SIM card.
- **Device Model**: The full official identifier of the type of device associated with the SIM card.
- **Device Type**: The category of the device associated with the SIM card (e.g., router, modem, and IoT gateway).
- **Usage**: The amount of data consumed during the session (the period between the start of the network connection to its termination), displayed in MB or GB.
- **Status**: The operational state of the SIM, either **Active **(available for use) or **Inactive **(not in use).
- **Country**: The country where the SIM is located.
- **Tags**: The tags associated with the SIM card. You can click a specific tag to filter the SIMs page and display only the SIMs that have the tag associated with them.
- **Connection**: The connectivity state of the SIM. The possible values are:
- **Online**:** **The SIM is** **connected to the network.
- **Offline**: The SIM is disconnected from the network.
- **Inventory**: The SIM is ready for assignment, or if already assigned, awaiting profile registration on a device. This option applies only to eSIMs.
You can also view additional columns by selecting them from the [column chooser](/zscaler-cellular/filtering-customizing-tables#show-hide-columns).
- Edit [status](/zscaler-cellular/changing-status-zscaler-sims), [update the IMEI](/zscaler-cellular/changing-imei-association-zscaler-sims), or [update tags](/zscaler-cellular/managing-tags-zscaler-sims) for a particular SIM card.
- [View detailed information for each SIM card](/zscaler-cellular/viewing-sim-details).
- Limit the number of records displayed per page. You can choose to display 10, 20, or 50 entries per page.
- Go to a specific page using the page number or move to the next or previous page.
![SIMs page with annotations showing various options](/downloads/zscaler-cellular/sims/about-sims/zscaler-cellular-about-sims-page-new.jpg)