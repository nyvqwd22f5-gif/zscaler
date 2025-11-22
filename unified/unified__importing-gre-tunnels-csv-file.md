# Importing GRE Tunnels from a CSV File
Source: https://help.zscaler.com/unified/importing-gre-tunnels-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1495336.pdf

This article describes how to add, edit, or delete multiple GRE tunnels by importing a CSV file. You can add up to 3,000 GRE tunnels. For a complete list of ranges and limits, see [Ranges & Limitations](/unified/ranges-limitations).
To import a CSV file:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **> **Static IPs & GRE Tunnel**.
- On the** GRE Tunnels** page, click **Sample Import CSV file** to download the GRE tunnels template.
- Enter your GRE tunnels in the CSV file template in the following format so that the Zscaler service successfully imports the CSV file:
- **Action**:** **Enter + or - to indicate whether you want to add or delete a GRE tunnel.
- **Static IP**: Enter the static IP address that you want to map with your GRE tunnel. You can map only one static IP address with a GRE tunnel.
- **Primary Data Center VIP**: Enter a primary data center VIP address for the GRE tunnel.
- **Secondary Data Center VIP**: Enter a secondary data center VIP address for the GRE tunnel. Ensure that the primary and the secondary VIP destinations do not point to the same data center.
- **Internal IP Range**: Enter an internal IP address range for the GRE tunnel.
- **VIPs Within Country Only**:** **Enter* *`true` or `false` to indicate whether you prioritize Zscaler data centers from the country of origin of the IP address.
- **IP Unnumbered**: Enter* *`true` or `false` to indicate whether you require an internal IP address on each side of your GRE tunnel. For example, enter `true` if you do not require an internal IP address.
- **Description**: (Optional) Enter additional information or notes about the GRE tunnel.
- After you have the CSV file in the correct format, click **Import CSV**.
The **Import GRE Tunnel from CSV file** window appears.
- In the **Import GRE Tunnel from CSV file** window:
- Select **Override Existing Entries**, if you want to update existing GRE tunnels, including deleting existing GRE tunnels or adding new GRE tunnels. Do not select this option if you only want to add new GRE tunnels.
Review your CSV file and ensure that there is no duplication. If you attempt to add a new GRE tunnel that already exists without selecting this option, the Zscaler service displays an error message.
- Click **Choose File**, and then browse and select the CSV file you want to import.
- Click **Import**.
- After the CSV file successfully imports, click **Close**.