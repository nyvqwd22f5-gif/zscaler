# SFTP
Source: https://help.zscaler.com/uvm/sftp
PDF: https://help.zscaler.com/pdf/com/en/1528241.pdf

![The SFTP tile](/downloads/uvm/configure/sources/sftp/mceclip0.png)
The SFTP source allows you to retrieve your files from any remote server that supports SFTP.
Required Parameters
- Host
- Port: The default port for SFTP is 22. If you use a different port, enter it here.
- Username: A valid username associated with the host server.
- Password
- File Type: Choose from the drop-down menu. Only CSV and JSON formats are supported.
-
Folder Path: Enter the path to the specific folder you wish to retrieve. If left empty, all relevant files are retrieved. For example, entering `reports/2023` only retrieves files from that specific folder. Files from the `reports/2024` or personnel folders are not retrieved.
Main
| - Reports
|   | - 2023
|   | - 2024
|
| - Personel
|   | - 2023
|   | - 2024
- Start Date: Enter a start date for the data retrieval in the `YYYY-MM-DDT00:00:00Z` format.