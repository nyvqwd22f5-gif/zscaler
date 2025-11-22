# Managing SNMP Configurations
Source: https://help.zscaler.com/zero-trust-branch/managing-snmp-configurations
PDF: https://help.zscaler.com/pdf/com/en/1532443.pdf

Zero Trust Branch supports the Simple Network Management Protocol (SNMP) standard for network monitoring and management. You can use the following standard management information bases (MIBs):
- IF-MIB
- SYS-MIB
- Standard Linux MIBs
Custom MIBs are not supported.
Both SNMPv2 and SNMPv3 are supported. You can enable both versions of SNMP on Zero Trust Branch simultaneously.
- [Configure SNMPv2.](#configure-snmpv2)
- [Configure SNMPv3.](#configure-snmpv3)
[]
- From the Zero Trust Branch Admin Portal, go to **Settings > Global**.
-
In the **SNMP Configurations** panel, click **Settings** to open the** SNMP Settings** window.
[See image.](#snmpv2-config)
-
In the **SNMP Settings **window, select **Enable SNMPv2**. The following additional fields appear:
- **Community**: Enter the community string (plain-text password) to access network devices via SNMPv2.
- **Client IPs**: Enter the client IP addresses that will do SNMP monitoring via SNMPv2.
- **SNMP MIB (Management Information Base)**: Click the **Download **icon to download the MIB to your computer.
Click **Save**.
[See image.](#enable-snmpv2)
-
To verify the configuration, from the SNMP server, run the command `snmpwalk` for the IP address of the WAN management interface to view the MIBs.
[See image.](#snmp-walk)
[]To configure SNMPv3, enable it and manage its configuration via SNMP profiles.
- From the Zero Trust Branch Admin Portal, go to **Settings > Global**.
-
In the **SNMP Configurations** panel, click **Settings **to open the** SNMP Settings** window.
[See image.](#snmpv3-config)
- In the **SNMP Settings **window, select **Enable SNMPv3**.
-
Click **Save** to close the **SNMP Settings **window.
[See image.](#enable-snmpv3)
-
Back in the **SNMP Configurations** panel, click **Manage SNMPv3** to open the **SNMPv3 **page.
[See image.](#manage-snmpv3)
-
On the **SNMPv3** page, click **Add SNMP Profile** to create a new profile, or click the **Gear **icon to edit an existing profile.
[See image.](#edit-snmp)
-
In the **Edit SNMP Profile **window, complete the information on all tabs.
-
On the **SNMP Profile Info** tab:
- **Profile name**: Enter a name for this profile.
- **Profile description**: Enter a description for this profile.
Click **Next.**
[See image.](#snmp-profile-info)
-
On the **Security Group & View **tab, provide information about this profile's security level, the object identifiers (OIDs) you are monitoring, and the login information for this profile. OIDs are unique identifiers used to identify specific variables included in SNMP MIBs, such as device serial numbers, interface status, memory, temperature, and so on.
**Security Group Details**:
- **Choose or create a new security group**: Select an existing group from the drop-down menu or select **Create a new group**.
- **Security Group Name**: If creating a new group, enter a name for the group. If using an existing group, the current name displays.
- **Choose Security Group Level**: Select the security group level for this group: `authPriv` (provides authentication and encryption) or `authNoPriv` (provides authentication but no encryption).
**View Details**:
- **Choose or create a new security view**: Select an existing security view from the drop-down menu or select **Create a new view**.
- **View name**: If creating a new view, enter a name for the view. If using an existing view, the current name displays.
- **OIDs to include**: Enter one or more OIDs that you want to include in this security view and click **Add** after each one.
- **OIDs to exclude**: Enter one or more OIDs that you want to exclude from this security view and click **Add** after each one.
**User Details**:
- **Username**: Enter the username to log in to SNMPv3 for this profile.
- **Authentication protocol**: Select the authentication protocol to use with this username and password, such as `sha`.
- **Authentication Password**: Enter the password for this username.
- **Privacy method**: If you selected `authPriv` as the security level, select the encryption algorithm, e.g., `aes` (Advanced Encryption Standard).
- **Authpriv Password**: If you selected `authPriv` as the security level, select the password for this encryption method.
Click **Next.**
[See image.](#snmp-group-view)
-
On the **Trap **tab, enter information about the SNMP trap for this profile. An SNMP trap is an asynchronous message sent from the device to the SNMP manager when a critical event happens, such as a link down, high CPU, power failure, and so on.
- **Choose or create a new trap**: Select an existing trap from the drop-down menu or select **Create a new trap**.
- **Trap Name**: If creating a new trap, enter a name for the trap. If using an existing trap, the current name displays.
- **Receiving server IP address**: Enter the IP address at which the SNMP manager will receive SNMP traps.
- **Receiving server port**: Enter the UDP port where the SNMP manager is listening for SNMP traps. Typically, port 162 is used. Port 161 is used for queries from SNMP managers. Both ports must be enabled on the firewall.
Click **Next.**
[See image.](#snmp-trap)
Click **Save configuration**.
-
To apply a profile to a site, select **Deployment > Sites** and click the name of the site you want in the **Site Name **column.
[See image.](#snmp-site-select)
-
On the site details page, click the **Settings **tab, then click **SNMPv3 **in the left-side navigation. Then select the SNMPv3 profile you want to use from the drop-down menu and click **Save**.
[See image.](#snmp-profile-select)
-
To verify the configuration, from the SNMP server, run the command `snmpwalk` for the IP address of the device to view the MIBs.
[See image.](#snmp-walk-v3)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-config-settings.png)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-config-settings.png)
[]
![SNMP Settings panel](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-settings.png)
[]
![SNMP Settings panel](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-settings.png)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-manage-snmpv3.png)
[]
![Adding and editing SNMP profiles on the SNMPv3 page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/manage-snmp.png)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-profile-info.png)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-group-view.png)
[]
![Accessing SNMP Configurations Settings on the Global settings page](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-trap.png)
[]
![Sample iptables output used to verify SNMP configuration.](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmp-walk.png)
[]
![Sample iptables output used to verify SNMP configuration.](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/site-list-snmp.png)
[]
![Sample iptables output used to verify SNMP configuration.](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/site-snmp.png)
[]
![Sample iptables output used to verify SNMP configuration.](/downloads/zero-trust-branch/analytics-monitoring/managing-snmp-configurations/snmpwalk-v3.png)