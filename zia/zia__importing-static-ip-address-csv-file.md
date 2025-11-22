# Importing Static IP Address from a CSV File
Source: https://help.zscaler.com/zia/importing-static-ip-address-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1447901.pdf

This article describes how to add, edit, or delete multiple static IP addresses by importing a CSV file. You can add up to 3,000 static IP addresses. For a complete list of ranges and limits, see [Ranges & Limitations](/zia/ranges-limitations).
To import a CSV file:
- Go to **Administration** > **Static IPs & GRE Tunnels **>** Static IPs**.
- Click **Sample Import CSV file** to download the static IP address template.
- Enter your static IP addresses in the CSV file template in the following format so that the Zscaler service successfully imports the CSV file:
- **Action**:** **Enter + or - to indicate whether you want to add or delete a static IP address.
- **Static IP**: Enter the static IP address that you want to provision with the Zscaler service.
- **Publicly Routable**: Enter `true` or `false` to indicate whether the IP address is publicly routable. For example, enter `true` if it is a public IP address.
- **Latitude**: Enter the latitude of the region that you want to map with the static IP address.
- **Longitude**: Enter the longitude of the region that you want to map with the static IP address.
- **IP Region**: Enter the name of the region or city that you want to map with the static IP address.
- **Managed By**: Enter if the static IP address is managed by self or by a specific Zscaler partner.
- **Description**: (Optional) Enter additional information or notes about the static IP address.
- After you have the CSV file in the correct format, click **Import CSV**.
The **Import Static IP from CSV file** window appears.
- In the **Import Static IP from CSV file** window:
- Select **Override Existing Entries**, if you want to update existing static IP addresses, including deleting existing static IP addresses or adding new static IP addresses. Do not select this option if you only want to add new static IP addresses.
Review your CSV file and ensure that there is no duplication. If you attempt to add a new static IP address that already exists without selecting this option, the Zscaler service displays an error message.
- Click **Choose File**, and then browse and select the CSV file you want to import.
- Click **Import**.
- After the CSV file successfully imports, click **Close**.