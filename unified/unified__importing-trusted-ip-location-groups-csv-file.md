# Importing Trusted IP Location Groups from a CSV File
Source: https://help.zscaler.com/unified/importing-trusted-ip-location-groups-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1505206.pdf

The article describes how to import IP location groups using a CSV file.
To edit and import a CSV file:
- Go to **Infrastructure **> **Locations** > **Trusted IP Location Groups**.
- Click **Import CSV**.
The **Import Location Group** window appears.
[See image.](#import-location-groups)
- In the **Import Location Group** window, click **Download** **Sample** to download the user information template.
- Enter your location group information in the CSV file template in the following format so that the Zscaler service successfully imports the CSV file:
- The file name must have a .csv extension.
- The first line of the file is the header row.
- Enter one of the following for **Action**:
- **+** (plus sign) to add a new IP location group.
- **-** (minus sign) to delete an IP location group.
- Each IP Location group must be on a separate line.
- (Optional) If you want to update your existing location group information (e.g., locations), including deleting IP locations, as well as add new locations, select **Override Existing Entries**. Do not select this option if you only want to add new location groups. If you attempt to add an IP location group that already exists and this option is not selected, the Zscaler service displays an error message stating that identical IP location group cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication.
- When your CSV file is ready to import, click **Browse File**.
- Browse and select the CSV file, then click **Open**.
- Click **Import.** The CSV file is successfully imported.
[]![Importing Location Groups](/downloads/zslogin/administration/ip-locations/importing-ip-locations-csv-file/zid-import-location-groups.png)