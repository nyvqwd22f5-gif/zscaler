# Adding IP Addresses to the Allowlist
Source: https://help.zscaler.com/deception/adding-ip-addresses-allowlist
PDF: https://help.zscaler.com/pdf/com/en/1531390.pdf

You can enhance security for the Zscaler Deception Admin Portal by configuring an allowlist, specifying IP addresses that are allowed to access it. This extra layer of control minimizes unauthorized access and reduces threats.
To configure the IP address allowlist:
- Go to **Settings** > **Network Settings** > **Allowed IPs**.
- Select **Enabled**.
-
Click **Add**.
[See image.](#add-ip-allowlist-access-portal)
- Enter the following details:
- **Name**: Enter a name for the allowlist.
-
**IP/CIDR**: Enter the IP or CIDR address. You can enter `all` to allow all IP addresses.
Certain IP addresses for aggregators, Threat Intelligence (TI) management, Decoy Connectors, and Zscaler Private Access (ZPA) App Connectors are added to the allowlist by default. If you try to add these IP addresses again, an overlapping IP/CIDR found error message is displayed.
-
Enable the following modules to access the Deception Admin Portal:
- **UI/APIV2**: Allow access via user interface (UI) or V2 API endpoints.
- **Decoy Connector**: Allow Decoy Connectors and aggregators to connect.
- **Endpoint**: Allow Landmine agents to connect.
- **APIV1**: Allow access via V1 API endpoints.
[See image.](#add-ip-allowlist)
- Click **Save**.
- In the confirmation window, click **OK**.
You can lock out users and components such as Decoy Connectors, aggregators, and Landmine agents if their IP addresses are not on the allowlist. Make sure you verify the IP addresses before saving the configuration.
[]![Add an allowlist](/downloads/deception/settings/network-settings/adding-ip-addresses-allowlist/zscaler-deception-allowed-IP-add-button-1.png)
[]![Configure an allowlist](/downloads/deception/settings/network-settings/adding-ip-addresses-allowlist/zscaler-deception-configure-allowed-ip-1.png)