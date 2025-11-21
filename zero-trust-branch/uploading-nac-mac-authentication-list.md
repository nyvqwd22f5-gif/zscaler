# Uploading a NAC-MAC Authentication List
Source: https://help.zscaler.com/zero-trust-branch/uploading-nac-mac-authentication-list
PDF: https://help.zscaler.com/pdf/com/en/1529368.pdf

Rather than allowing Zero Trust Branch to scan and discover your devices, for greater network security, you can upload a comma-separated values (CSV) list of MAC addresses that you want to include in your installation. Zero Trust Branch uses this list to verify devices and authenticate them during network access control (NAC).
To upload a list of MAC addresses to Zero Trust Branch:
-
Go to **Firewall > NAC-MAC Authentication** and click **Upload CSV**.
[See image.](#nac-mac-auth1)
-
In the **Upload CSV **panel, click **Download Template **to download a CSV template. The template consists of two fields: MAC address and a corresponding description for each device.
[See image.](#download-template)
-
On your computer, complete the CSV template with the MAC addresses and descriptions of the devices that you want to include in your installation, then save the template file.
[See image.](#mac-csv)
-
In the **Upload CSV** panel, drag the template file to the box, or click** Upload a CSV file** and select the file location on your computer.
[See image.](#mac-upload)
-
Click **Validate **to view a preview of the information you are uploading.
[See image.](#mac-validate)
-
Verify that the information is correct, and click **Submit **to add the devices to Zero Trust Branch.
[See image.](#mac-submit)
-
The **NAC-MAC Authentication** list displays with the devices that you added.
[See image.](#nac-mac-auth2)
[]![NAC-MAC Authentication page.](/downloads/zero-trust-branch/administration/policy-management/managing-segmentation-policies/mac-nac-upload-csv.png)
[]![Downloading a template from the Upload CSV panel.](/downloads/zero-trust-branch/administration/policy-management/managing-segmentation-policies/mac-nac-download-template.png)
[]![Sample CSV file](/downloads/zero-trust-branch/administration/policy-management/managing-segmentation-policies/mac-csv.png)
[]![Uploading a CSV file from the Upload CSV panel](/downloads/zero-trust-branch/administration/policy-management/uploading-mac-nac-authentication-list/mac-nac-upload-button.png)
[]![Validating a CSV file from the Upload CSV panel](/downloads/zero-trust-branch/administration/policy-management/uploading-mac-nac-authentication-list/upload-csv-validate.png)
[]![Submitting a CSV file from the Upload CSV panel](/downloads/zero-trust-branch/administration/policy-management/managing-segmentation-policies/upload-csv-submit.png)
[]![NAC-MAC Authentication page with a device.](/downloads/zero-trust-branch/administration/policy-management/managing-segmentation-policies/mac-nac-auth-list.png)