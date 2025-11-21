# Importing Trusted IP Locations from a CSV File
Source: https://help.zscaler.com/unified/importing-trusted-ip-locations-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1505181.pdf

The article describes how to import IP locations using a CSV file.
To edit and import a CSV file:
- Go to **Infrastructure **> **Locations **> **Trusted IP Locations**.
-
Click **Import CSV**.
The **Import Location** window appears.
[See image.](#import-location)
- In the **Import Location** window, click **Download** **Sample** to download the user information template.
-
Enter the IP location details in the CSV file template in the following format so that the Zscaler service successfully imports the CSV file:
- The file name must have a .csv extension.
- The first row in the file is the header row.
- Enter the details in the following columns:
- A: Define the action:
- **+** (plus sign) to add a new IP location.
- **-** (minus sign) to delete an IP location.
- B: Enter the name of the IP location that must be displayed in the Admin Portal.
- C: Enter the country for this particular IP location.
- D: Enter the range of IP addresses. They can be IPV4 or IPV6 ranges.
- E: Enter the IP address.
- F: Enter the IP subnet for the location.
Each IP location must be on a separate row.
- (Optional) If you want to update your existing location information (e.g., country), including deleting IP locations, as well as add new locations, select **Override Existing Entries**. Do not select this option if you only want to add new locations. If you attempt to add an IP location that already exists and this option is not selected, the Zscaler service displays an error message stating that identical IP location cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication.
- When your CSV file is ready to import, click **Browse File**.
- Browse and select the CSV file, then click **Open**.
- Click **Import.** The CSV file is successfully imported.
[]![Importing Locations](/downloads/zslogin/administration/ip-locations/adding-ip-locations/zid-import-location.png)