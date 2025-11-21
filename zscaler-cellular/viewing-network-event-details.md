# Viewing Network Event Details
Source: https://help.zscaler.com/zscaler-cellular/viewing-network-event-details
PDF: https://help.zscaler.com/pdf/com/en/1518101.pdf

You can access in-depth information about specific network events associated with each SIM provisioned to your organization. This detailed view helps you analyze connectivity behavior, troubleshoot issues, and understand event-specific details for enhanced network management.
To view the details of a specific network event:
-
In the left-side navigation, select **Network Events**.
The **Network Events **page appears.
-
Locate the event of interest in the table and click the corresponding **Date**. This opens the detailed view for the selected network event with the following details:
- **IMSI**: The International Mobile Subscriber Identity associated with the SIM.
- **Operator Name**: The telecom operator managing the network connection.
- **SIM Name**: The name or alias assigned to the SIM.
- **Source System**: The system or node responsible for the event.
- **Timestamp**: The exact date and time when the event occurred.
- **IP Address**: The public or private IP address assigned to the SIM during the session when the event occurred.
- **Location Details**: Including Location Area Code (LAC), Cell Identifier (CID), Mobile Country Code (MCC), and Mobile Network Code (MNC).
- **RAT Type**: The Radio Access Technology used for the network connection (e.g., LTE, 5G).
- **Data Cap Reached**: Indicates whether the SIM has exceeded the allocated data usage limit.
- **Event Name**: The type of event that occurred, such as session initiated, authorized, or disconnected (e.g., DATA_SESSION_ONLINE).
- **Country**: The country where the event occurred.
- **SIM ID**: A unique identifier assigned to the SIM card used in the device.
- **SIM EID**: A unique identifier for the embedded SIM (eSIM) used in the device.
- **Connection Status Log**: Provides options to view, download, and copy network event details in JSON format.
[See image.](#network-events-page)
You can customize the table to show specific columns, limit rows per page, navigate through pages, filter the data to refine your view, or sort the columns to adjust the order of entries. To learn more, see [Filtering & Customizing Tables](/zscaler-cellular/filtering-customizing-tables).
[]![Viewing network event details with Connection Status Log icons highlighted](/downloads/zscaler-cellular/network-events-sim-sessions-and-logins-monitoring/viewing-network-event-details/cellular-edge-viewing-network-events.png)