# Adding Domains Using a CSV
Source: https://help.zscaler.com/risk360/adding-domains-using-csv
PDF: https://help.zscaler.com/pdf/com/en/1504411.pdf

You can add domains on the Seeds Management page to run frequent scans on them to detect vulnerabilities for external attack surfaces. The Risk360 service then quantifies the risk determined on various parameters on exposed assets for potential breach and visualizes them as factors on the [Factors](/risk360/about-factors) page.
To add domains:
- Go to **Administration** > **Seeds Management**.
- In the **Domains** field, click **Upload File**.
-
Click **Download CSV Template**. A CSV template for uploading the domains is downloaded to your device.
[See image.](#adding-domains)
-
Update the file with the list of domains that you want to scan for external attack surface analysis. You can add up to 10 domains.
[See image.](#upload)
- Click **Upload CSV**, go to the file on your device, and select the file.
-
After a successful upload message is displayed, click **Save**.
If an error message is displayed, ensure that the domains are added in the correct format in the CSV file and reupload the file.
The [Seeds Management](/risk360/about-seeds-management) page displays all the domains from the CSV file. The Risk360 service takes up to 24–48 hours to scan and analyze the domains.
[]![Upload CSV window](/downloads/risk360/administration-authentication/adding-domains-using-csv/Risk360-Upload-Seeds-CSV.png)
[]![CSV Format](/downloads/risk360/administration-authentication/adding-domains-using-csv/Risk360-Seeds-CSV.png)