# Configuring Endpoint Data Scan and Endpoint Settings
Source: https://help.zscaler.com/zia/configuring-endpoint-data-scan-endpoint-settings
PDF: https://help.zscaler.com/pdf/com/en/1515466.pdf

You can configure the endpoint data scan, allowing administrators to enable or disable sensitive data reporting to the cloud. You can also configure continuous classification, which allows enabling or disabling file scans locally on the endpoint to detect sensitive data.
Endpoint Data Loss Prevention (DLP) performs classification scans on an endpoint to detect and categorize data. Whenever the DLP Engines or dictionaries are modified, a classification scan is applied on the endpoint.
On the Configuration page (Analytics > Endpoint Data Scan > Configuration), you can configure the following:
-
**Endpoint Data Scan**:
- **Report Endpoint Data Scan to the Cloud**: Enable the toggle to view the data on the Endpoint Data Scan page.
[See Image.](#endpoint_data_scan_img)
-
**Endpoint Settings**:
- **Classification**:
- **Continuous Classification**: Enable the toggle to enhance performance.
- **Maximum File Size for Continuous Classification**: Select the maximum file size from the drop-down menu. The available file sizes are 10 MB, 30 MB, 50 MB, and 100 MB. Although you set a value for the maximum file size, Endpoint DLP continues to inspect files with a size of up to 100 MB during data exfiltration.
- **Run the Continuous Classification on HDD drives**: Enable the toggle to run the continuous classification on HDD drives. By default, only SSD drives are scanned.
- **Miscellaneous:**
- **Exemption Duration**: Select the exemption duration of the Endpoint DLP and Device Control, during which the user activities are not blocked but are monitored from the drop-down menu. You can set the duration for 5 Minutes, 10 Minutes, 15 Minutes, 60 Minutes, 2 Hours, 6 Hours, or 12 Hours.
[See Image.](#endpoint_settings_img)
![This image shows the Endpoint Data Scan tab](/downloads/data-protection/endpoint-data-loss-prevention/Endpoint_datascan_configuration.png)
[]
![This image shows the Endpoint Settings in the Configuration tab](/downloads/data-protection/endpoint-data-loss-prevention/Endpoint_settings_configuration.png)
[]