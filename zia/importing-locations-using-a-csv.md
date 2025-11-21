# Importing Location and Sublocation Information from a CSV File
Source: https://help.zscaler.com/zia/importing-locations-using-a-csv
PDF: https://help.zscaler.com/pdf/com/en/1399256.pdf

This article describes how to add, edit, or delete multiple locations and sublocations by importing a CSV file. You can add up to 32,000 locations and 2,000 sublocations per location. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations#Locations).
To import a CSV file to add, edit, or delete locations and sublocations:
- Go to **Administration **>** Location Management**.
-
Click **Import Locations**.
The **Import Location** window appears.
-
In the **Import Location** window, click **Choose File**, navigate to the CSV file, then click **Open**.
Make sure that the CSV file you are importing is in the same format as the **Sample Import CSV file** provided by Zscaler.
- (Optional) If you want to update your existing locations, including deleting locations, as well as add new locations, select the **Override Existing Entries** checkbox. Do not select this option if you only want to add new locations. If you attempt to add a location that already exists and this option is not selected, the Zscaler service displays an error message stating that identical locations cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication. To learn more, see [Configuring Multiple Locations and Sublocations](/zia/configuring-multiple-locations-and-sublocations).
- Click **Import**.
- After the CSV file is successfully imported, click **Close**.