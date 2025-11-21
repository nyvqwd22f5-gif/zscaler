# Using Application Segment Import
Source: https://help.zscaler.com/unified/using-application-segment-import
PDF: https://help.zscaler.com/pdf/com/en/1519236.pdf

Users can bulk import application information to ease the process of application segment configuration. This speeds up the data entry process and eliminates the need to re-enter data if it changes over time. To learn more, see [About Application Segment Import](/unified/about-application-segment-import).
To bulk import application segment data:
- Go to **Policies** > **Access Control** > **Private Applications** > **App Segments**.
- Click **Application Segment Import**.
- Click **Download CSV template**. The sample template downloads to your local machine. If you already have a CSV file containing your data, you can [import the file](#Step_5.).
- Open, edit, and save the template on your local machine with information for the following fields:
- Application Name
- Application FQDN/IP
- Server IP
- TCP Ports
- UDP Ports
- App Owner Contact
- Application Importance
- Hosting Location
- Environment
- []Click **Import CSV**.
[See image.](#Click-Import-CSV)
- Click **Browse File **to select your CSV file.
[See image.](#Import-CSV)
- Click **Import**. The data might take some time to import. You can leave the page and return to it later. If you import a file with entries that were included in a previous import, the new entries are automatically added as additional information to the existing entries of the same name.
[See image.](#Import-CSV_file-selected)
-
After the data from the file is imported, the page refreshes to show a table of all the application information. A message appears confirming the number of successfully imported entries, as well as the number of failed downloads. You can click the link in the message to download a new file containing the failed entries and the reasons for their import failure.
The table of imported application segment data is categorized alphabetically by the **Application Segment Name**.
The limit of application segments that can be imported is 50,000. If you attempt to import a file with more than 50,000 entries of application segment data, the import fails. Depending on how many application segments you import, the import time might increase.
After you import the data for the application segments, you can merge the application segments together. To learn more, see [Merging Imported Application Segments](/unified/merging-imported-application-segments).
[]![The window to import a CSV file appears.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/using-application-segment-import/Import-CSV_Browse-File_Import.png)
[]![The Import window with a CSV file selected.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/using-application-segment-import/Import_file-added.png)
[]![Click Import CSV.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/using-application-segment-import/Application-Segment-Import_import-CSV_squircle.png)