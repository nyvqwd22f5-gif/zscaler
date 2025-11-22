# Editing DLP Resources
Source: https://help.zscaler.com/unified/editing-dlp-resources
PDF: https://help.zscaler.com/pdf/com/en/1493216.pdf

[]Zscaler Endpoint Data Loss Prevention (DLP) supports the following resources:
- Network shares
- Printers
- Removable storage devices
The Zscaler service automatically supports Box, Dropbox, Google Drive, iCloud for macOS, and OneDrive personal cloud storage accounts. No extra configuration is available for those services as DLP resources.
To learn more, see [Adding DLP Resources](/unified/adding-dlp-resources).
To edit a DLP resource:
- Go to **Policies **>** Data Protection **>** Policy **>** Endpoint DLP Resources**.
- On the **DLP Resources** page:
- [Edit a network share](#network-shares)
- [Edit a network printer](#printers)
- [Add a removable storage device](#removable-storage)
- [Activate](/unified/saving-and-activating-changes-admin-portal) your changes.
[]On the **Network Shares** page:
- Locate the network share in the list, then click the **Edit** icon.
The **Edit Network Share** window is displayed.
- In the **Edit Network Share** window:
- Edit the following **Network Share Details**:
- **Name**: Enter a name for the network share.
- **Server name**: Enter the server name where the network share is located (e.g., the server's IP address).
- (Optional) **Description**: Enter a description for the network share.
- Edit the following **Directories** attributes:
- **All files and directories on this server**: Select this option if you want to include all files and directories on the specified server.
- **Files in the following directories and subdirectories**: Select this option if you want to specify the directories and subdirectories to be included. If you select this option, the **Directory Paths** field is displayed. Add paths (e.g., `<folder>/<subfolder>`) separated by line breaks, then click **Add Items**. To delete existing directory paths, click the **Delete** icon next to the directory path in the list.
- Click **Save**.
[See image.](#edit-network-share)
[]![A screenshot of the Edit Network Share window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/editing-dlp-resources/ZIA-EndpointDLP-Edit-Network-Share.png)
[]On the **Printers** page:
- Locate the network printer in the list, then click the **Edit** icon.
The **Edit Printer** window is displayed.
- In the **Edit Printer** window:
- **Name**: Enter a name for the network printer.
- **Domain**: Enter the name of the domain where the printer is located.
- **Printer Name**: Enter the printer name as it appears in the list of printers on your operating system.
- **IP Address**: Enter the IP address for the network printer.
- (Optional) **Description**: Enter a description for the network printer.
- Click **Save**.
[See image.](#edit-network-printer)
[]![A screenshot of the Edit Printer window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/editing-dlp-resources/ZIA-EndpointDLP-Edit-Network-Printer.png)
[]On the **Removable Storage Devices** page, you can do the following:
- Locate the removable storage device in the list, then click the **Edit** icon.
The **Edit Removable Storage Device** window is displayed.
- In the **Edit Removable Storage Device** window:
- Edit the following **Removable Storage Device Details**:
- **Name**: Enter a name for the removable storage device.
- (Optional) **Description**: Enter a description for the removable storage device.
- Edit the following **Criteria** for the device, as needed:
- **Vendor ID**: Enter the manufacturer of the removable storage device.
- **Product ID**: Enter the product ID of the removable storage device.
- **Serial Number**: Enter the serial number of the removable storage device.
- Click **Save**.
[See image.](#edit-removable-storage)
[]![A screenshot of the Edit Removable Storage Device window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/editing-dlp-resources/ZIA-EndpointDLP-Edit-Removable-Storage-Device.png)