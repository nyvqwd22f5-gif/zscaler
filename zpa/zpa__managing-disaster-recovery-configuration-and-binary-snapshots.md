# Managing Disaster Recovery Configuration and Binary Snapshots
Source: https://help.zscaler.com/zpa/managing-disaster-recovery-configuration-and-binary-snapshots
PDF: https://help.zscaler.com/pdf/com/en/1485661.pdf

After an App Connector Group or ZPA Private Service Edge Group is designated for [disaster recovery](/zpa/understanding-disaster-recovery), a configuration and binary snapshot is saved in the local configuration files on your App Connector or ZPA Private Service Edge.
Configuration and binary snapshots are copies of the disaster recovery configuration and binary files used for backup when App Connectors or ZPA Private Private Service Edges are designated for disaster recovery. They are used when an admin wants to fix a misconfiguration during a disaster scenario. If the current binary is not compatible with an older configuration snapshot, then an older binary snapshot can be installed. For example, if an admin assigns an application to the wrong App Connector, a prior configuration snapshot with the correct application assignment can be installed to fix the issue. If the binary is not compatible with an older configuration snapshot (i.e., the binary fails to start up or logs unexpected errors with an older configuration snapshot), then an older binary snapshot can be installed.
The following configuration files are included in the configuration snapshots:
- `application_conf.json`: Contains application-specific configuration data.
- `customer_conf.json`: Contains customer-specific configuration data.
- `override_conf.json`: Contains override data.
- `other_conf.json`: Contains uncategorized configuration data (e.g., App Connector-specific configuration data within a ZPA Private Service Edge).
The snapshots are downloaded to the following directories:
- For App Connectors:
- Configuration snapshots: `/opt/zscaler/var/config_snapshots`
- Binary snapshots: `/opt/zscaler/var/binary_snapshots`
- For ZPA Private Service Edges :
- Configuration snapshots: `/opt/zscaler/var/service-edge/config_snapshots`
- Binary snapshots: `/opt/zscaler/var/service-edge/binary_snapshots`
The Zscaler cloud maintains up to 15 prior configuration snapshots and up to 5 prior binary snapshots, and updates both snapshots periodically. If necessary, contact Zscaler Support to change the limits for the configuration and binary snapshots.
If the disk space utilization of the App Connector or ZPA Private Service Edge exceeds 90%, the configuration and binary snapshots used for disaster recovery are not captured. To learn more, see [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors) and [Troubleshooting ZPA Private Service Edges](/zpa/troubleshooting-zpa-private-service-edges).
Use the following script with sudo privileges in your App Connector or ZPA Private Service Edge console:
snapshot_mgmnt_script.sh
Managing the Configuration and Binary Snapshots
[]To manage the configuration and binary snapshots:
- Ensure that Disaster Recovery Mode is enabled on your App Connector Group or ZPA Private Service Edge Group.
- Run the script with sudo privileges:
- For App Connectors, enter the following command in `/opt/zscaler/var`:
[admin@zpa-connector var]$ sudo sh snapshot_mgmnt_script.sh
- For ZPA Private Service Edges, enter the following command in `/opt/zscaler/var/service-edge/`:
[admin@zpa-service-edge service-edge]$ sudo sh snapshot_mgmnt_script.sh
- Enter `yes` or `y`, and then press `Enter`.
The following options appear in the console after running the scripts with sudo privileges:
- [Listing the Configuration or Binary Snapshots](#listing)
- [Installing the Configuration or Binary Snapshots](#installing)
[]To list the configuration or binary snapshots:
- Follow the steps to [manage](#managing) the configuration and binary snapshots.
- Press `1`, and then press `Enter`.
A prompt appears that asks if you want to list the configuration or binary snapshots.
- Press `1` to list the configuration snapshots, or press `2` to list the binary snapshots, and then press `Enter`.
The following is an example listing of a configuration snapshot:
snapshot_entry [1/1]:
age(in sec): 1306
associated binary version: 22.385.1-1168-g16424d2
Config files (modified time):
unknown (2023-01-11 09:29:44.685424664)
customer_conf.json (2023-01-11 07:29:44.685424665)
application_conf.json (2023-01-11 07:29:44.685424665)
override_conf.json (2023-01-11 07:29:44.685424665)
other_conf.json (2023-01-11 07:29:44.685424665)
snapshot dir: /opt/zscaler/var/service-edge/config_snapshots/config-2023-01-11
The following is an example listing of a binary snapshot:
snapshot_entry [1/1]:
bin: image.bin (2023-01-11 07:30:09.698442411)
meta: metadata (2023-01-11 07:30:09.698442411)
version file: version (2023-01-11 07:30:09.698442411)
version: 22.385.1-1168-g16424d2
age(in sec): 1395
snapshot dir: /opt/zscaler/var/service-edge/binary_snapshots/binary-2023-01-11-07-39_ver_22.385.1-1168-g16424d2
[]To install a configuration or binary snapshot:
- Follow the steps to [manage](#managing) the configuration and binary snapshots.
- Press `2`, and then press `Enter`.
- Press `1` to install a configuration snapshot, or press `2` to install a binary snapshot, and then press `Enter`.
- Enter the configuration or binary snapshot directory name (e.g., `/opt/zscaler/var/service-edge/config_snapshots/config-2023-01-11`) found when listing the snapshot, and then press `Enter`.
A confirmation response appears in the console when the snapshot is successfully installed:
Config snapshot /opt/zscaler/var/service-edge/config_snapshots/config-2023-01-11 is installed successfully !
After the configuration or binary snapshot is installed, the App Connector or ZPA Private Service Edge service restarts.
Snapshot Formats
The snapshots are organized in the directories by date and time in the following format: `config-<YYYY>-<MM><DD>` (e.g., `config-2022-09-19`). The binary snapshots are versioned and are in the following format: `binary-<YYYY>-<MM><DD>_ver<binary_version>` (e.g., `binary-2022-09-19-19_ver_22.284.2-1016`).
It might be necessary to use an older version of the binary snapshot if the current binary version does not match the binary version that was captured in the configuration snapshot.
The following table provides the date, time, and version formats for the snapshots:
| Format | Description | Value |
| ------ | ----------- | ----- |
| MM | Indicates the month (e.g., 01, 10, 12) | Supported values are 01 to 12 |
| DD | Indicates the date (e.g., 01, 15, 31) | Supported values are 01 to 31 |
| YYYY | Indicates the year | Supported values are 1971 to 9999 |
| HH | Indicates the hour | Supported values are 0 to 23 |
| MM | Indicates the minutes | Supported values are 0 to 59 |
| SS | Indicates the seconds | Supported values are 0 to 59 |
| ver_<binary version> | Indicates the binary version | Any valid Zscaler binary version |