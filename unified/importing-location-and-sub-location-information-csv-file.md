# Importing Location and Sub-Location Information from a CSV File
Source: https://help.zscaler.com/unified/importing-location-and-sub-location-information-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1495536.pdf

This article describes how to add, edit, or delete multiple locations and sub-locations by importing a CSV file. You can add up to 32,000 locations and 2,000 sub-locations per location. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
To import a CSV file to add, edit, or delete locations and sub-locations:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding** >** Location Management**.
- Click **Import Locations**.
The **Import Location** window appears.
- In the **Import Location** window, click **Choose File**, navigate to the CSV file, then click **Open**.
Make sure that the CSV file you are importing is using same format as the **Sample Import CSV file** provided by Zscaler.
- (Optional) If you want to update your existing locations, including deleting locations, as well as add new locations, select the **Override Existing Entries** checkbox. Do not select this option if you only want to add new locations. If you attempt to add a location that already exists and this option is not selected, the Zscaler service displays an error message stating that identical locations cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication. To learn more, see [Configuring Multiple Locations and Sub-Locations](/unified/configuring-multiple-locations-and-sub-locations).
- Click **Import**.
- After the CSV file is successfully imported, click **Close**.