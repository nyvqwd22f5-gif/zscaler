# Starting or Stopping a Scan
Source: https://help.zscaler.com/dspm/starting-stopping-scan
PDF: https://help.zscaler.com/pdf/com/en/1474756.pdf

You can stop an in-progress data scan in some of the following scenarios:
- The current full scan or data sampling scan has been running for a long time and there are significant cost overruns in your account.
- Changing the configuration from a full or data sampling scan to scanning only new or recent data to limit the scan to newly added or modified files.
- Modifying the resource scope by removing certain data stores from scanning and enabling new data stores for scan.
- Re-initiating the scan using a new DLP configuration of all the files in the data stores.
- You cannot stop a Delta scan. To stop the scan entirely, you need to [disable the scan rule](/dspm/enabling-or-disabling-scan-setting). Delta scan or Only New Files scan refers to scanning only new and modified files on the selected cloud storage resource (data store) as part of the scan setting.
- New S3 buckets that are added to the scan rule are included in the Delta scan automatically. Delta scan starts for the enumerated buckets from that point forward and the buckets are scanned with the latest DLP engine configuration.
- If an S3 bucket is removed from the scan rule, the scan stops for that bucket.
Starting a Scan
To start a data scan:
- Go to **Administration** > **Scan Settings**.
- Select the **Scan Rules** tab.
- Click the **Actions** icon (![ds-actionsicon.png](/downloads/dspm/scan-settings/managing-scan-settings/running-demand-scan/ds-actionsicon.png)
) for the resource you want to start scanning.
-
Select the **On-Demand Scan** option.
[See image.](#ds-startoption)
The **On-Demand Scan** confirmation window appears.
-
Read the message that appears, then click **Confirm**.
[See image.](#ds-startmsg)
The storage account is queued for scanning.
[]![Confirmation window to start the scan.](/downloads/dspm/scan-settings/managing-scan-settings/starting-stopping-scan/ds-scanrule-start-scan-confirm.png)
[]![Scan rule page with an annotation for Stop Scan option. ](/downloads/dspm/scan-settings/managing-scan-settings/starting-stopping-scan/ds-scan-start-scan.png)
Stopping a Scan
You can stop a scan that is currently in progress.
- The** Stop Scan** option is only visible when a scan is in** In-Progress** status.
- Stopping a scan only stops the scan currently in progress. Upcoming scans continue as scheduled.
To stop the scan:
- Go to **Administration** > **Scan Settings**.
- Select the **Scan Rules** tab.
- Click the **Actions** icon (![ds-actionsicon.png](/downloads/dspm/scan-settings/managing-scan-settings/running-demand-scan/ds-actionsicon.png)
) for the resource you want to stop scanning.
-
Select the **Stop Scan** option.
[See image.](#ds-stopoption)
The **Stop Scan** confirmation window appears.
-
Read the message that appears, then click **Confirm**.
[See image.](#ds-stopmsg)
The data scan is stopped.
[]![Scan rule page with an annotation for Stop Scan option. ](/downloads/dspm/scan-settings/managing-scan-settings/starting-stopping-scan/ds-scanrule-stop-scan.png)
[]![Confirmation window to stop the current in progress scan.](/downloads/dspm/scan-settings/managing-scan-settings/starting-stopping-scan/ds-scanrule-stop-scan-confirm.png)