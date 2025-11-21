# Configuring Scan Rule for Azure Virtual Machines
Source: https://help.zscaler.com/dspm/configuring-scan-rule-azure-virtual-machines
PDF: https://help.zscaler.com/pdf/com/en/1483241.pdf

You can configure the scan rule to scan virtual machines (VMs) in your Azure cloud accounts. DSPM scans the databases for any sensitive data and vulnerabilties. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the Azure accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
The following systems are excluded from scanning:
- VMs encrypted using ADE.
- Windows desktop VMs running with Windows version 10 or 11.
- Windows Server 2012 VMs.
- Azure VMs created using unmanaged disks (`.vhd` from storage account).
- Storage accounts with public network access disabled.
To configure a scan rule for Azure virtual machines:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#azurevm1)
- [3. Select the accounts that must be scanned.](#azurevm2)
- [4. Exclude virtual machines (Optional).](#ds-aws-vm-exclude)
- [5. Set up the scan schedule.](#azurevm3)
- [6. Select the scan scope.](#scanscope)
- [7. Review and complete the configuration.](#azurevm4)
- []Go to **Administration** > **Scan Settings**.
-
Select the **Scan Rules **tab.
If you are configuring the scan rule for the first time, the following page appears:
[See image.](#scan-initial)
-
Click **Add Scan Rule**.
[See image.](#new-scan)
The **General Information** page appears.
-
On the **General Information **page:
- **Scan Rule Name**: Enter a unique and descriptive name for the scan rule.
- **Scan Rule Description (Optional)**: Enter a description for the scan rule (maximum is 500 characters).
[See image.](#ds-scan-gen-info)
- Click **Next**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
-
[]On the **Select Cloud and Resource Type** page:
- For **Cloud Type**: Select **Azure**.
- For **Resource Type**: Select **Virtual Machine**.
[See image.](#azurevm-selectcloudtype)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, select one of the following options:
-
**Scan All Resources**: Scans all the virtual machines across all the onboarded Azure accounts.
[See image.](#azurevm-selectdata)
-
**Scan Specific Resources: **Scan only specific subscriptions. When you select this option, select the checkbox for the subscriptions that must be scanned.
- **Select Specific Subscriptions and Regions**: Scan only specific subscriptions. When you select this option, select the checkbox for the subscriptions that must be scanned.
- **Scan Specific Instances**: Specify the virtual machines that must be scanned.
- **Select from the List**: Select the checkbox for the virtual machines that must be scanned from the list. If you choose **Manual**, enter the instance IDs separated by commas.
-
**Select by Tags**: Enter the key-value pairs for the instances. All the instances that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all instances that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a instance is included if it matches any of the key-value pairs.
[See image.](#azurevm-scanspecificsub)
You can [optionally exclude](#ds-exclude) some VMs from the scan.
-
**Enable Malware Scanning**: Enable this option if the resources must be scanned for malware. This option is disabled by default.
[See image.](#malwarescan)
- Click **Next**.
[][]On the **Exclude Virtual Machines (Optional)** page, you can specify the VMs that must be excluded from the scan.
- Enter the instance IDs separated by commas.
-
**Exclude Virtual Machines By Tags**: Enable this option and enter the key-value pairs of the VMs that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any VMs that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a VM is excluded if it matches any of the key-value pairs.
-
**Exclude Operating System Directories Files from Scanning**: Disable this option if you want to scan the OS directories. This option is enabled by default.
The following directories are excluded from the scan:
- [Linux](#linux)
- [Windows](#windows)
- [Packages](#packages)
[See image.](#azurevm-optional)
- Click **Next**.
-
[]On the **Scan Schedule** page, select the scan frequency:
- **On Demand **(Default): Scan the data manually when needed.
- **Daily**: Scan the data daily.
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu.
- **Monthly**: Scan the data once a month.
[See image.](#azurevm-schedule)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#azurevm-review)
- Click **Finish**.
- []`/usr/local/`
- `/usr/lib/`
- `/usr/lib64/`
- `/usr/share/`
- `/usr/bin/`
- `/usr/sbin/`
- `/usr/src/`
- `/usr/include/`
- `/usr/libexec/`
- `/var/app/`
- `/var/log/`
- `/var/lib/`
- `/var/cache/`
- `/etc/`
- `/boot/`
- []`C:\Program Files\`
- `C:\Program Files (x86)\`
- `C:\Windows\`
- []`/smui/`
- `/smca/`
- `/opt/elasticbeanstalk/`
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![Select Cloud and Resource Type page with an annotation around the Azure Cloud Type and Virtual Machine Resource.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-virtual-machine/ds-scanrule-azure-select-vm.png)
[]![The Select Resources to Scan page with Scan All Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-virtual-machine/ds-scanrule-azure-vm-scanall.png)
[]![Select Resources to Scan page with Scan Specific Subscription option selected and selected few subscriptions to scan.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-virtual-machine/ds-scanrule-azure-vm-scan-specific.png)
[]![Enable malware scanning option is enabled with the toggle button.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-enable-malware-scan.png)
[]![The Exclude virtual machines screen to exclude resources from scanning.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-virtual-machine/ds-scanrule-azure-vm-exclude.png)
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-scan-weekly.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-virtual-machine/ds-scanrule-azure-vm-review.png)