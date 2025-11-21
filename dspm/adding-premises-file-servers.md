# Adding an On-Premises File Server
Source: https://help.zscaler.com/dspm/adding-premises-file-servers
PDF: https://help.zscaler.com/pdf/com/en/1532037.pdf

You can add an [on-premises file servers](/dspm/about-service-registration) to DSPM. DSPM scans the data assets for sensitive data and identifies any potential security posture risks.
Prerequisites
Before adding an on-premises file server to DSPM, ensure the following prerequisites are met:
- Integrate an on-premises scanner with DSPM to enable scanning of on-premises file servers. To learn more, see [Adding or Deleting a Scanner Integration](/dspm/adding-premises-scanner-integration).
- Create an on-premises data center and associate it with the configured on-premises scanner. To learn more, see [Adding an On-Premises Data Center](/dspm/adding-premises-data-center).
Supported Protocol Versions
The following protocol versions are supported for scanning file servers:
| Protocol | Versions |
| -------- | -------- |
| SMB | 2.0, 2.1, 3.0, 3.02, 3.1.1 |
| NFS | v4.0, v4.1, v4.2 |
Adding an On-Premises File Server
To add an on-premises file server:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **On-Premises File Servers** tab, and click **Add File Server**.
[See image.](#img_add)
The **Add On-Premises File Server** window appears.
-
In the **Add On-Premises File Server** window:
- **File Server Information**:
- **File Server Name**: Enter a unique name for the file server.
- **Protocol**: Select the communication protocol used to connect to the file server.
- **Version **(available only if **NFS** protocol is selected): Select the NFS version to use.
- **File Server Type**: Select the file server OS type.
- **NFS**: Select **Windows** or **Linux**.
- **SMB**: This field is set to **Windows**.
- **Connection Attributes**:
- **File Server IP / Hostname**: Enter the IP address or hostname of the file server.
- **Domain Name**: Enter the domain name associated with the file server.
- **Port**: Select the port used for communication protocol.
- **Default Port**: SMB uses `445` and NFS uses `2049`.
- **Custom Port**: Enter a valid port number based on your configuration requirements.
- **Authentication**:
- **Secret Provider Type**: This field is autopopulated with the provider used to manage authentication secrets, typically set to **Zscaler DSPM**.
- **Username**: Enter the username used to authenticate access to the file server.
- **Password**: Enter the password associated with the username.
- **Data Center Association**:
- **Data Center**: Select the [data center](/dspm/about-data-center) associated with the file server.
- **Location**: This field is autopopulated based on the data center selection.
[See image.](#ds-add-details)
-
Click **Save**.
The **Add On-Premises File Server** confirmation window appears.
-
In the** Add On-Premises File Server** confirmation window, read the message, and then click **Confirm and Save**.
[See image.](#ds-confirm)
The on-premises file server is added and displayed in the **On-Premises File Servers** tab on the [Service Registration](/dspm/about-service-registration) page. To configure the scan settings, see [Configuring Scan Rule for ](/dspm/configuring-scan-rule-premises-file-servers)[On-P](/dspm/configuring-scan-rule-premises-file-servers)[r](/dspm/configuring-scan-rule-premises-file-servers)[em](/dspm/configuring-scan-rule-premises-file-servers)[is](/dspm/configuring-scan-rule-premises-file-servers)[es](/dspm/configuring-scan-rule-premises-file-servers)[ ](/dspm/configuring-scan-rule-premises-file-servers)[File Se](/dspm/configuring-scan-rule-premises-file-servers)[r](/dspm/configuring-scan-rule-premises-file-servers)[v](/dspm/configuring-scan-rule-premises-file-servers)[e](/dspm/configuring-scan-rule-premises-file-servers)[rs](/dspm/configuring-scan-rule-premises-file-servers).
[]![Confirmation window for adding on-premises file server showing fields that can't be edited.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-add-onprem-file-server-confirm.png)
[]![TheOn-Premises File Servers page with a list of file servers and annotation around the Add On-Premises File Servers button.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/add-file-server-button.png)
[]![Add On-Premises File Servers drawer with the necessary details filled.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-add-inprem-file-server-details.png)