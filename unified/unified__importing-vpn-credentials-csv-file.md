# Importing VPN Credentials from a CSV File
Source: https://help.zscaler.com/unified/importing-vpn-credentials-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1495366.pdf

Configuring a VPN credential is one of the tasks you must complete when configuring an IPSec VPN tunnel. To learn more, see [Configuring an IPSec VPN Tunnel](/unified/configuring-ipsec-vpn-tunnel). You can import up to 3,000 entries per CSV file. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations). You can also [manually add VPN credentials](/unified/adding-vpn-credentials) to the Admin Portal.
To add or remove VPN credentials using a CSV file:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** VPN Credentials**.
- Click **Sample Import CSV file** to download a sample file, which can be used as a template for your VPN credentials.
- Within the CSV file, enter your VPN credential information. To learn more, see [Formatting CSV Files](/unified/importing-vpn-credentials-csv-file#format_csv).
- Click **Import VPN Credentials**.
The **Import Location** window appears.
- In the **Import VPN Credentials** window, click **Choose file**, navigate to the CSV file, then click **Open**.
- Click **Import**.
VPN User IDs are automatically converted to lowercase after import.
- Under **Import Results**, verify that all of the information was successfully imported from your CSV file. Ensure that nothing appears under **Failed Records**. If a credential (or record) was not properly added or deleted, you must re-import the file.
- Click **Close**.
[]Formatting CSV Files
The following list contains the field values you must enter when adding or deleting VPN credentials using a CSV file. The field values are listed in the order they must be entered on each row. All required fields, including fields that are required only under certain conditions, are also specified. You must place a comma between each field value; a space between commas is not required but can be added if preferred.
You can use one CSV file to add or delete VPN credentials for different authentication types. The authentication type is used to identify the peer when configuring IPSec VPN tunnels. For example, in one CSV file, you can have several lines for adding and deleting FQDN credentials followed by several more lines adding and deleting IP credentials.
The following are the fields for adding or deleting VPN credentials for each authentication type:
- **Action (Required)**:** **Enter + or - to indicate whether you want to add or delete a VPN credential. This field is required.
- **PSK Type (Required)**: Enter the proper authentication type for the VPN credential:
- UFQDN
- IP
- XAUTH
You can delete (-) an existing XAUTH VPN credential but cannot add (+) a new VPN credential using the CSV file. However, you can edit an existing XAUTH VPN credential directly from the Admin Portal.
- **VPN User Name (Required)**: Depending on the **PSK Type** entered, enter one of the following:
- The proper user ID of the FQDN. It must be valid and cannot include special characters (e.g., <, @, [], etc.) or end in a period (e.g., safemarch.).
- The proper user ID of the XAUTH. It must be valid and cannot include special characters (e.g., <, @, [], etc.) or end in a period (e.g., safemarch.).
- The IP address of your local gateway. This is the address that you sent to Zscaler beforehand. If you have not already done so, submit your static IP addresses to Zscaler Support, who can then ensure that these IP addresses are properly added to the service.
- **Comment**: Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **Pre-Shared Key (Required)**: Enter the pre-shared key or XAuth password, depending on the **PSK Type** entered.
- **Managed_By**: If this VPN credential is being managed by an [SD-WAN partner](/unified/about-partner-integrations), enter the name of the partner. If the credential is not being managed by a partner, enter a comma instead. The valid partner names are:
- Cisco Viptela
- Citrix SD-WAN
- CloudGenix
- HPE Aruba
- ngena
- Riverbed SteelConnect
- Silver Peak
- VMware VeloCloud
The following example adds an FQDN VPN credential and removes an IP VPN credential:
+,UFQDN,jane.doe@example.com,My example FQDN VPN Credential,12345,,
-,IP,123.123.12.33,My example IP VPN Credential,54321,,