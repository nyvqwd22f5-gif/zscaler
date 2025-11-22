# Adding DLP Resources
Source: https://help.zscaler.com/unified/adding-dlp-resources
PDF: https://help.zscaler.com/pdf/com/en/1493211.pdf

[]Adding Data Loss Prevention (DLP) resources is the first step you complete when [configuring Endpoint Data Loss Prevention (DLP) policy rules](/unified/configuring-endpoint-dlp-policy-rules). The Zscaler service supports the following DLP resources:
- Network shares
- Printers
- Removable storage devices
The Zscaler service automatically supports Box, Dropbox, Google Drive, iCloud for macOS, and OneDrive personal cloud storage accounts. No extra configuration is available for those services as DLP resources.
When you add DLP resources, you can then use them to create Endpoint DLP policy rules to monitor and take action on sensitive data. Additionally, you can create restrictive Endpoint DLP rules (i.e., block all users from printing sensitive data), and then you can add rule exceptions that allow users or groups in your organization to perform tasks that might otherwise violate restrictive rules.
For example, your organization has an Endpoint DLP policy that blocks all users from saving sensitive data to removable storage devices. However, you have a banking customer that can't access files outside their corporate intranet. As a result, users in your Finance Department share Excel files that contain sensitive data with the customer via a set of USB flash drives. In that case, you can use specific identifiers to create a DLP resource for each of the flash drives that move between your Finance Department and the banking customer, and then you can create a rule exception that allows users in your Finance department to save Excel files to those specific flash drives.
To learn more, see [Configuring Endpoint DLP Policy Rules](/unified/configuring-endpoint-dlp-policy-rules).
You can use the following methods to DLP resources:
- [Add a single DLP resource](#add-single-resource)
- [Import multiple DLP resources](#import-resources)
[]
- Go to **Policies **>** Data Protection **>** Policy **>** Endpoint DLP Resources**.
- On the **DLP Resources** page:
- [Add a network share](#network-shares-single)
- [Add a network printer](#printers-single)
- [Add a removable storage device](#removable-storage-single)
- [Activate](/unified/saving-and-activating-changes-admin-portal) your changes.
[]On the **Network Shares** page:
- Click **Add Network Share**.
The **Add Network Share** window is displayed.
- In the **Add Network Share** window:
- Enter the following **Network Share Details**:
- **Name**: The name of the network share
- **Server Name**: The server name where the network share is located (e.g., the server's IP address)
- (Optional) **Description**: A description of the network share
- Select one of the following **Directories** attributes:
- **All files and directories on this server**: Select this option if you want to include all files and directories on the specified server.
- **Files in the following directories and subdirectories**: Select this option if you want to specify the directories and subdirectories to be included. If you select this option, the **Directory Paths** field is displayed. Add paths (e.g., `/<folder>/<subfolder>`) separated by line breaks, then click **Add Items**.
- Click **Add**.
[See image.](#add-network-share)
[]![A screenshot of the Add Network Share window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Network-Share.png)
[]On the **Printers** page, you can do the following:
- Click **Add Printer**. The **Add Network Printer** window is displayed.
- In the **Add Network Share** window:
- **Name**: Enter a name for the network printer.
- **Domain**: Enter the name of the domain where the printer is located.
- **Printer Name**: Enter the name of the printer as it appears in the operating system list of printers.
- **IP Address**: Enter the IP address for the network printer.
- (Optional) **Description**: Enter a description for the network printer.
- Click **Add**.
[See image.](#add-network-printer)
[]![A screenshot of the Add Network Printer window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Network-Printer.png)
[]On the **Removable Storage Devices** page, you can do the following:
- Click **Add Removable Storage** **Device**. The **Add Removable Storage Device** window is displayed.
- In the **Add Removable Storage Device **window:
- Enter the following **Removable Storage Device Details**:
- **Name**: The name of the removable storage device
- (Optional) **Description**: A description of the removable storage device
- Enter at least one of the following **Criteria** for the device:
- **Vendor ID**: The manufacturer of the removable storage device
- **Product ID**: The product ID of the removable storage device
- **Serial Number**: The serial number of the removable storage device
- Click **Add**.
[See image.](#add-removable-storage-device)
[]![A screenshot of the Add Network Printer window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Removable-Storage.png)
[]You can import multiple resources at the same time using a CSV file. There is a sample template available to download for each resource type.
To import multiple DLP resources:
- Go to **Policies **>** Data Protection **>** Policy **>** Endpoint DLP Resources**.
- On the **DLP Resources** page:
- [Import network shares](#network-shares-import)
- [Import network printers](#printers-import)
- [Import removable storage devices](#removable-storage-import)
- [Activate](/unified/saving-and-activating-changes-admin-portal) your changes.
[]On the **Network Shares** page:
- Click **Import Network Shares**.
The **CSV Import - Network Shares** window is displayed.
- Click **Download csv template** to download the import network shares template.
- Enter your network shares in the CSV file template in the following format:
<name>,<description>,<server name>,<paths>
For example:
Network share 1,imported network drive,Server 3234,"path1,path2,path3,path4,path5,path6,path7,path8"
- After you have the CSV file saved in the correct format, click **Choose a file**.
- Browse and select the CSV file you want to import, then click **Open**.
- Click **Next**.
[See image.](#add-multiple-network-shares-01)
- In the **Preview** pane, confirm the details of the network shares you are importing.
- (Optional) Add the network shares to a group:
- Click **Add the imported resources to a group**.
- To add the resources to a new group, click **New Group**, then specify a name and description for the group.
- To add the resources to an existing group, click **Existing Group**, then select a group from the **Select Group** drop-down menu.
- Click **Import**.
[See image.](#add-multiple-network-shares-02)
The network shares appear in the list in the **Network Shares** window.
[]![A screenshot of the CSV Import Network Shares window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Network-Shares-01.png)
[]![A screenshot of the CSV Import Network Shares window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Network-Shares-02.png)
[]On the **Printers** page:
- Click **Import Printers**.
The **CSV Import - Printers** window is displayed.
- Click **Download csv template** to download the import network printers template.
- Enter your network shares in the CSV file template in the following format:
<name>,<description>,<UNC>,<IP address>,<domain>
For example:
Printer1,Printer outside Conference Room 1,blr/resources/folder1,1.1.1.1,printer.safemarch.com
- After you have the CSV file saved in the correct format, click **Choose a file**.
- Browse and select the CSV file you want to import, then click **Open**.
- Click **Next**.
[See image.](#add-multiple-network-printers-01)
- In the **Preview** pane, confirm the details of the network printers you are importing.
- (Optional) Add the printers to a group:
- Click **Add the imported resources to a group**.
- To add the resources to a new group, click **New Group**, then specify a name and description for the group.
- To add the resources to an existing group, click **Existing Group**, then select a group from the **Select Group** drop-down menu.
- Click **Import**.
[See image.](#add-multiple-network-printers-02)
The network printers appear in the list in the **Printers** window.
[]![A screenshot of the CSV Import Printers window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Network-Printers-01.png)
[]![A screenshot of the CSV Import Printers window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Network-Printers-02.png)
[]On the **Removable Storage Devices** page, you can do the following:
- Click **Import Removable Storage Devices**.
The **CSV Import - Removable Storage Devices** window is displayed.
- Click **Download csv template** to download the import removable storage devices template.
- Enter your removable storage devices in the CSV file template in the following format:
<name>,<description>,<vendor ID>,<product ID>,<serial number>
For example:
Finance Department 1,Thumb drive for use by the Finance Deparment,11029,11926,59695
- After you have the CSV file saved in the correct format, click **Choose a file**.
- Browse and select the CSV file you want to import, then click **Open**.
- Click **Next**.
[See image.](#add-multiple-storage-devices-01)
- In the **Preview** pane, confirm the details of the removable storage devices you are importing.
- (Optional) Add the removable storage devices to a group:
- Click **Add the imported resources to a group**.
- To add the resources to a new group, click **New Group**, then specify a name and description for the group.
- To add the resources to an existing group, click **Existing Group**, then select a group from the **Select Group** drop-down menu.
- Click **Import**.
[See image.](#add-multiple-storage-devices-02)
The removable storage devices appear in the list in the **Removable Storage Devices** window.
[]![A screenshot of the CSV Import Removable Storage Devices window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Removable-Storage-01.png)
[]![A screenshot of the CSV Import Removable Storage Devices window for Zscaler Endpoint DLP](/downloads/zia/policies/endpoint-data-loss-prevention/adding-dlp-resources/ZIA-EndpointDLP-Add-Multiple-Removable-Storage-02.png)