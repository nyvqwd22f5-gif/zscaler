# About DLP Resources
Source: https://help.zscaler.com/unified/about-dlp-resources
PDF: https://help.zscaler.com/pdf/com/en/1493206.pdf

The Zscaler service automatically supports Box, Dropbox, Google Drive, iCloud for macOS, and OneDrive personal cloud storage accounts. No extra configuration is available for those services as DLP resources.
[]Creating a Data Loss Prevention (DLP) resource is the first step in setting up an [Endpoint Data Loss Prevention (DLP) policy](/unified/configuring-endpoint-dlp-policy-rules). You can use the resources you create to configure an Endpoint DLP policy that protects your organization from data loss by monitoring and taking action on sensitive data that end users interact with on endpoints (i.e., printing, saving to removable storage, saving to network shares, or uploading to personal cloud storage accounts). The DLP resources are associated with rules that use Zscaler custom and predefined DLP engines to detect sensitive data, allow or block activities, and notify your organization's auditor when a user's activity on an endpoint triggers an Endpoint DLP rule.
To learn more, see [Step-by-Step Configuration Guide for Zscaler Endpoint DLP](/unified/step-step-configuration-guide-zscaler-endpoint-dlp).
DLP resources provide the following benefits and allow you to:
- Create rules to monitor and prevent the leakage of sensitive data on endpoints.
- Monitor printing, saving to removable storage, saving to network shares, and saving to personal cloud storage accounts.
- Use Zscaler custom and predefined DLP engines to detect and take action on sensitive data.
About the DLP Resources Page
[]On the DLP Resources page (Policies > Data Protection > Policy > Endpoint DLP Resources), you can view and add the following resources:
- [Network Shares](#network-shares)
- [Printers](#printers)
- [Removable Storage Devices](#removable-storage)
[]On the **Network Shares** page, you can do the following:
- Add and configure a [network share](/unified/adding-dlp-resources).
- [Import network shares](/unified/adding-dlp-resources) via CSV file.
- View a list of all configured DLP network shares for your organization. For network shares, you can see the following:
- **Number**: The numerical value of each network share.
- **Name**: The network share's name. You can sort this column.
- **Server Name**: The name of the server where the network share is located.
- Search for a network share.
- Edit or delete a network share.
- Go to the **Network Share Groups** page.
- Go to the **Printers** page.
- Go to the **Removable Storage Devices** page.
[]![ZIA Admin Portal DLP Resources page](/downloads/unified/policies/internet-saas/data-protection/endpoint-data-loss-prevention/about-dlp-resources/unified-dlp-resources-network-shares.png)
[]On the **Printers** page, you can do the following:
- Add and configure a [network printer](/unified/adding-dlp-resources).
- [Import network printers](/unified/adding-dlp-resources) via CSV file.
- View a list of all configured DLP network printers for your organization. For network printers, you can see the following:
- **Number**: The numerical value of each printer.
- **Name**: The printer's name. You can sort this column.
- **Domain**: The name of the domain where the network printer is located.
- **Printer Name**: The printer's name as it appears in the operating system list of printers.
- **IP Address**: The printer's IP address.
- **Description**: The printer's description.
- Search for a network printer.
- Edit or delete a printer.
- Go to the **Printer Groups** page.
- Go to the **Network Shares** page.
- Go to the **Removable Storage Devices** page.
[]![ZIA Admin Portal DLP Resources page](/downloads/unified/policies/internet-saas/data-protection/endpoint-data-loss-prevention/about-dlp-resources/unified-dlp-resources-printers.png)
[]On the **Removable Storage Devices** page, you can do the following:
- Add and configure a [removable storage device](/unified/adding-dlp-resources).
- [Import removable storage devices](/unified/adding-dlp-resources) via CSV file.
- View a list of all configured DLP removable storage devices for your organization. For removable storage devices, you can see the following:
- **Number**: The numerical value of each removable storage device.
- **Name**: The removable storage device's name. You can sort this column.
- **Vendor ID**: The removable storage device's manufacturer.
- **Product ID**: The removable storage device's product ID number.
- **Serial Number**: The removable storage device's serial number.
- **Description**: The removable storage device's description.
- Search for a removable storage device.
- Edit or delete a removable storage device.
- Go to the **Removable Storage Device Groups** page.
- Go to the **Network Shares** page.
- Go to the **Printers** page.
[]![ZIA Admin Portal DLP Resources page](/downloads/unified/policies/internet-saas/data-protection/endpoint-data-loss-prevention/about-dlp-resources/unified-dlp-resources-removable-storage-devices.png)