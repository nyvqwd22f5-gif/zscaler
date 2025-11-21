# Migrating Nanolog Streaming Service (NSS) ZscalerOS to Version 24 for Microsoft Azure
Source: https://help.zscaler.com/zia/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1402361.pdf

As part of our efforts to improve the scalability and robustness, and performance of our cloud, Zscaler has released ZscalerOS version 24, which is to be used across all virtual cloud nodes. The latest ZscalerOS 24 comes with advanced security features and key benefits, such as security patches for the OS as well as new libraries, TLS 1.3 support, and enhancements to the performance of the Zscaler service.
If you are running NSS on Azure with ZscalerOS 10 or earlier, you must copy the latest NSS on Azure OS Virtual Hard Drive (VHD) image from Zscaler's storage account and swap out the existing OS disk with the new one using PowerShell.
Log streaming is not available during the manual migration procedure, but automatically resumes from where it stopped after the upgrade is completed successfully.
To migrate ZscalerOS to version 24 on NSS:
- [Step 1: Check the ZscalerOS Version on the Virtual Machine (VM)](#step-1)
Steps 2 through 8 apply only to NSS on Azure VM running ZscalerOS 10 or earlier.
- [Step 2: Copy the New OS Disk VHD File to the Original OS Disk VHD File Location](#step-2)
- [Step 3: Check the Backup Archive Status](#step-3)
Zscaler automatically takes a backup of several configuration items from the old OS disk and restores them automatically after the OS disk replacement. This step is to confirm that the backup has been taken properly.
- [Step 4: Check the NSS Feed Status](#step-4)
- [Step 5: Check the Support Tunnel Status](#step-5)
- [Step 6: Shut Down the VM](#step-6)
- [Step 7: Stop and Deallocate the VM in the Azure Portal](#step-7)
- [Step 8: Replace the Original OS Disk VHD File With the New OS Disk VHD File](#step-8)
- [Step 9: Log In to the New VM After 10 Minutes](#step-9)
- [Step 10: Check the Health of the New VM](#step-10)
- [Step 11: Check the NSS Feed Status Again](#step-11)
Troubleshooting
- [Zbridge Service for MCAS Log Collection is Not Running](#zbridge-service)
- [Changing Property 'os.Disk.vhd.uri' is Not Allowed](#changing-property-osdisk)
- [Target VM's original provisioning status is not Succeeded and Exiting migration](#provisioning-status-not-succeeded)
[]Run the following command on an SSH terminal connection to check the ZscalerOS version on the VM:
uname -a
[See image.](#ZSOS-version)
[]![Screenshot of possible outputs for uname -a command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/Azure-NSS-ZSOS-Version.png)
[]You can copy the OS disk VHD file using Azure CLI, PowerShell, or Azure Storage Explorer. Only the procedure for Azure Storage Explorer is included here.
Use the following information to ensure the fastest copy time:
| Value | Description |
| ----- | ----------- |
| Blob Service SAS URL | https://zos24migrationprod.blob.core.windows.net/?sv=2020-08-04&ss=bf&srt=sco&sp=rlitfx&se=2023-03-30T22:00:53Z&st=2022-03-29T14:00:53Z&spr=https&sig=gu8oKymSqIh6mD1MagqPsG4zoQKuqqPPCZxNoLgi5RM%3D |
| Storage Account Name | zos24migrationprod |
| Blob Container Name | zos24-migration-osdisk |
[See image.](#ase-storage-account)
To copy the new OS disk VHD file to the original OS disk VHD file location using Azure Storage Explorer:
- Download and launch [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/).
If you are running Azure Storage Explorer on a machine that is behind ZIA with SSL Inspection enabled, you might need to bypass the following FQDN from inspection: zos24migrationprod.blob.core.windows.net.
- Click the **Add Account** icon (plug icon).
[See image.](#azure-storage-explorer-plug)
The **Microsoft Azure Storage Explorer - Connect** window appears.
- In the **Microsoft Azure Storage Explorer - Connect** window, under the **Select Resource** section, select **Storage account or service**.
The **Select Connection Method** section appears.
- In the **Select Connection Method** section, select **Shared access signature URL (SAS)**.
[See image.](#azure-storage-explorer-connect)
- Click **Next**.
The **Enter Connection Info** section appears.
- In the **Enter Connection Info** section, configure the following attributes:
- **Display name**: The display name is automatically populated based on the service URL.
- **Service URL**: Enter the service URL shared by Zscaler.
[See image.](#azure-storage-explorer-sas)
- Click **Next**.
[See image.](#azure-storage-explorer-connection-summary)
The **Summary** section appears.
- Review the connection summary and click **Connect**.
- Once the connection is successful, in the left panel, go to **Storage Accounts** > **zos24migrationprod (SAS)** > **Blob Containers** > **zos24-migration-osdisk**. The VHD file is located here.
- Select the VHD file and click **Copy**.
[See image.](#azure-storage-explorer-copy-vhds)
- On the left panel, go to the blob container of your personal storage account that contains the original OS disk VHD file, and click **Paste** to add the new OS disk VHD file to your blob container. The transfer may take some time. The **Activities** tab at the bottom indicates when the transfer is complete.
The new OS disk VHD file appears in the blob container.
[See image.](#azure-storage-explorer-paste-vhds)
- Log in to the Azure Portal.
- Go to your destination blob container. The VHD file in the blob container is shown.
[See image.](#azure-portal-blob-container)
[]![Screenshot of the Add Account Icon (plug icon) in the Azure Storage Explorer](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Plug-icon-ZSOS24.png)
[]![Screenshot of the Connect window in the Azure Storage Explorer with SAS URI selected](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Connect-Azure-Storage-ZSOS24.png)
[]![Screenshot of Attach with SAS URI window in the Azure Storage Explorer](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Attach-SAS-URI-ZSOS24.png)
[]![Screenshot of a storage account's blob container with highlighted VHD. The Copy icon is highlighted.](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Portal-ASE-Copy.PNG)
[]![Screenshot of a personal storage account with VHD being pasted in the blob container](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Portal-ASE-Paste.PNG)
[]![Screenshot of Azure Portal connection summary.](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Connection-Summary-ZSOS24.png)
[]![Screenshot of an Azure Portal blob container with VHD](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Portal-Blob-Container.PNG)
[]Run the following command on an SSH terminal connection to check the status of the backup archive:
sudo vm-backup-status
[See image.](#vm-backup-status)
[]![Screenshot of SSH terminal showing the output of vm-backup-status command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/NSS-VM-Backup-status.png)
[]Run the following command on an SSH terminal connection to check the status of the NSS feed:
nss troubleshoot feeds
[See image.](#nss-troubleshoot-feeds)
[]![Screenshot of SSH terminal showing the output of nss troubleshoot feeds command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/NSS-Troubleshoot-feeds.png)
[]To shut down the VM using an SSH terminal connection:
- Run the following command to stop the NSS instance:
sudo nss stop
- Run the following command to shut down the VM:
sudo shutdown -h now
[]Run the following command on an SSH terminal connection to check the status of the support tunnel:
nss support-access-status
[See image.](#support-tunnel-status-possible-outputs)
The possible outputs are `Tunnel opened` or `No active Zscaler support tunnel found`.
If the support tunnel is opened, run the following command to stop it:
nss support-access-stop
[]![Screenshot of SSH terminal showing the output of nss support-access-status command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Support-Tunnel-Status-Tunnel-Open.png)
![Screenshot of SSH terminal showing the output of nss support-access-status command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Support-Tunnel-Status-No-Tunnel.png)
[]To deallocate the VM in the Azure Portal:
- In the Azure Portal, go to the **Overview** tab.
- Click **Stop**.
The **Stop this virtual machine** window appears.
- In the **Stop this virtual machine** window, click **OK**.
Ensure that the status of the VM changes to **Stopped (deallocated)**.
[See image.](#VM-stopped-deallocated)
[]![Screenshot of Azure Portal with VM stopped and deallocated.](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-virtual-service-edge-zscaleros-version-24-microsoft-azure/Azure-Portal-VM-Stopped-Deallocated.png)
[]To replace the original OS disk VHD file with the new OS disk VHD file:
- Populate the values in the Config.txt file.
- [See the table for the description of each value.](#value-table)
- [See the sample file.](#sample-config-file)
You can download the sample Config file: [Download sample Config file](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-virtual-service-edge-zscaleros-version-24-microsoft-azure/config_03_03-2022.txt)
- Run the script.
- [See the DiskSwap PowerShell script file.](#disk-swap-script-sample-file)
You can download the DiskSwap PowerShell script file: [Download DiskSwap PowerShell script file](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/DiskSwap.ps1)
The script prompts you to start the VM after successfully replacing the original OS disk VHD file with the new OS disk VHD file. Enter `y` to immediately start the VM, otherwise, you can boot the VM from the Azure Portal.
[]
| Value | Description |
| ----- | ----------- |
| vmname | Name of the virtual machine |
| newdisk | VHD URI of the new OS disk |
| rgname | Resource group where VM is provisioned |
[]vmname=migration-nss-demovm
newdisk=https://ZS24migration.blob.core.windows.net/57nssshaunak1/zsos24_nss_rev3.vhd
rgname=nssrg
[]#Test if the azure powershell modules are present on the system
$scmd="Connect-AzAccount"
$cmdout=Get-Command $scmd -eA SilentlyContinue -EV $serr -OV $sout
if(!$cmdout.CommandType) {
echo "Required powershell modules are missing. Please install the azure modules and retry"
exit
}
#Sign in for this session
Connect-AzAccount
#Fetch the config file to be loaded
if( $args[0] -ne $null ){
$filename=$args[0]
}
else
{
$filename="./config.txt"
}
$SubSelect = 'n'
Do {
$subs=Get-AzSubscription
echo "Listing available subscriptions in your account"
$subid=0
$ProvisionSub=99999
foreach ($sub in $subs) {
echo "Subscription $subid :"
echo $sub
$subid++
}
if($subid -ge 1)
{
$ProvisionSub=Read-Host -Prompt "Select one of the above for provisioning"
}
else
{
$ProvisionSub=0
}
echo "Selected subscription for provisioning :"
echo $subs[$ProvisionSub]
$SubSelect=Read-Host -Prompt "Enter `"y`" to continue with this subscription or `"n`" to choose again"
} While($SubSelect -eq 'n' -or $SubSelect -eq 'N')
if($SubSelect -ne 'y' -and $SubSelect -ne 'Y') {
echo "You did not choose a subscription to deploy in, script will exit now"
exit
}
$subscription=$subs[$ProvisionSub]
echo "Script will continue to provision in the selected subscription $subscription "
Set-AzContext -SubscriptionId $subscription.Id
echo "Azure Subscription for current session set to the following"
Get-AzContext
$select=Read-Host -Prompt "Do you wish to continue(y/n):"
if($select -ne 'y' -or $select -ne 'Y')
{
echo "Script terminating per user input"
exit
}
echo "Provisioning will continue with the selected subscription"
if ( -not (Test-Path $filename))
{
echo "Config file not found at $filename"
exit
}
else
{
echo "Found the configuration file, populating parameters from $filename"
}
$vmname=""
$osdisk=""
$rgname=""
$docopy=""
$disksize=225
foreach ($line in Get-Content $filename) {
if($line -match "^#.*") {
#Commented
continue
}
if( [string]::IsNullOrWhitespace($line)) {
#Empty line
continue
}
$entries=$line.split("=",2,[StringSplitOptions]'RemoveEmptyEntries')
#$entries=$line.split("=")
$e1=$entries[0]
$e2=$entries[1]
#Write-Host $e1 $e2 -Separator ","
$key=$e1.Trim()
$value=$e2.Trim()
#echo "Got entries" $entries[0] "->" $entries[1]
if($key -eq "vmname") {
$vmname=$value
continue
}
if($key -eq "rgname") {
$rgname=$value
continue
}
if($key -eq "newdisk") {
$osdisk=$value
continue
}
if($key -eq "copy") {
$docopy=$value
continue
}
if($key -eq "size") {
$disksize=$value
}
}
Write-Host -ForegroundColor Green -NoNewline "VM Name: "
Write-Host -ForegroundColor Cyan $vmname
Write-Host -ForegroundColor Green -NoNewline "Resource Group: "
Write-Host -ForegroundColor Cyan $rgname
Write-Host -ForegroundColor Green -NoNewline "New OS Disk location: "
Write-Host -ForegroundColor Cyan $osdisk
#sleep 30
$proceed=Read-Host "Continue? (y/n)"
if ($proceed -ne "y" -or $proceed -ne "Y") {
Write-Host -ForegroundColor Red "Script terminating..."
exit
}
$vm=Get-AzVm -Name $vmname -ResourceGroupName $rgname
if( $vm.ProvisioningState -ne "Succeeded" ) {
Write-Host -ForegroundColor Red "The target vm original provisioning status is not \" Succeeded\""
Write-Host -ForegroundColor Red "Exiting migration. Please contact zscaler support for further assistance"
exit
}
$vmstatuses=Get-AzVm -Name $vmname -ResourceGroupName $rgname -Status
$vmstatus="Nil"
foreach ($status in $vmstatuses.Statuses){if ($status.Code -Match "Power" ){ $vmstatus=$status.Code}}
if ($vmstatus -NotMatch "deallocated") {
Write-Host -ForegroundColor Red "VM state should be de allocated before proceeding. Script will exit now. "
Write-Host -ForegroundColor Red -NoNewLine "Current VM state:"
Write-Host -ForegroundColor Red $vmstatus
exit
}
Write-Host "Proceeding to replace disks."
$vm=Set-AzVMOSDisk -VM $vm -VhdUri $osdisk -DiskSizeInGB $disksize
Update-AzVM -ResourceGroupName $rgname -VM $vm
sleep 30
Write-Host "Attempting to start the vm now"
$start=Read-Host "Continue? (y/n)"
if ($start -ne "y" -or $start -ne "Y") {
Write-Host -ForegroundColor Red "Script terminating. Start VM from the portal."
exit
}
Start-AzVM -Name $vmname -ResourceGroupName $rgname
[]In the Azure Portal, enter the following credentials at the ZscalerOS command prompt to log in:
- Username: zsroot
- Password: zsroot
The following guidelines apply:
- Zscaler strongly recommends that you change this default password by running the passwd command.
- Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
[]Run the following command on an SSH terminal connection to check the health of the new VM:
sudo vm-restore-status
[See image.](#vm-restore-status)
[]![Screenshot of SSH terminal showing the output of vm-restore-status command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/NSS-VM-Restore-Status.png)
[]Run the following command on an SSH terminal connection to check the status of the NSS feed:
nss troubleshoot feeds
[See image.](#nss-troubleshoot-feeds-post-migration)
[]![Screenshot of SSH terminal showing the output of nss troubleshoot feeds command](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/NSS-Troubleshoot-feeds.png)
[]![Screenshot of the Azure Storage Account with Migrator VHD file.](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/ASE-Storage-Account.png)
[]The zbridge service is responsible for uploading logs to the MCAS log collector.
Run the following command to check the service status of the zbridge:
/sc/bin/smctl.sh status
[See image.](#nss-zbridge-not-running)
If the zbridge service is not running, run the following command to fix the issue by restarting the NSS service:
nss restart
[]![Screenshot of NSS Zbridge not running](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/NSS-Zbridge-Not-Running.png)
[]If the following error message appears while executing the migration PowerShell script, then it's likely that the current NSS VM was deployed manually through the Azure Portal rather than using the Zscaler-recommended PowerShell script and was assigned a managed disk:
![Screenshot of Changing property 'osDisk.vhd.uri' is not allowed](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/Changing-Property-osDisk-VHD-URI.png)
Since the migration is intended to be done using unmanaged disks, you need to redeploy the VM. To learn more, see [NSS Deployment Guide for Microsoft Azure](/zia/nss-deployment-guide-microsoft-azure).
Contact Zscaler Support for further information.
[]If the following error message appears while executing the migration PowerShell script, then the VM might not have been successfully provisioned due to a timed-out Azure command. However, the VM creation succeeded, and the instance is up:
"The target vm original provisioning status is not \" Succeeded\""
"Exiting migration. Please contact zscaler support for further assistance"
[See image.](#vm-original-provisioning-status-not-succeeded)
To fix this error:
- Run the script:
- [See the DiskSwap_nocheck PowerShell script file.](#diskswap-nocheck)
You can download the DiskSwap_nocheck PowerShell script file: [Download DiskSwap_nocheck PowerShell script file](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/DiskSwap_nocheck.ps1)
The expected outcome is as follows:
The target vm original provisioning status is not \" Succeeded
Proceeding with migration....
- Continue from [Step 9](/zia/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure#step-9).
[]![Screenshot of VM Original Provisioning Status not Succeeded](/downloads/zia/getting-started/zscaleros-migration-version-24/migrating-nanolog-streaming-service-zscaleros-version-24-microsoft-azure/VM-Original-Provisioning-Status-not-Succeeded.png)
[]#Test if the azure powershell modules are present on the system
$scmd="Connect-AzAccount"
$cmdout=Get-Command $scmd -eA SilentlyContinue -EV $serr -OV $sout
if(!$cmdout.CommandType) {
echo "Required powershell modules are missing. Please install the azure modules and retry"
exit
}
#Sign in for this session
Connect-AzAccount
#Fetch the config file to be loaded
if( $args[0] -ne $null ){
$filename=$args[0]
}
else
{
$filename="./config.txt"
}
$SubSelect = 'n'
Do {
$subs=Get-AzSubscription
echo "Listing available subscriptions in your account"
$subid=0
$ProvisionSub=99999
foreach ($sub in $subs) {
echo "Subscription $subid :"
echo $sub
$subid++
}
if($subid -ge 1)
{
$ProvisionSub=Read-Host -Prompt "Select one of the above for provisioning"
}
else
{
$ProvisionSub=0
}
echo "Selected subscription for provisioning :"
echo $subs[$ProvisionSub]
$SubSelect=Read-Host -Prompt "Enter `"y`" to continue with this subscription or `"n`" to choose again"
} While($SubSelect -eq 'n' -or $SubSelect -eq 'N')
if($SubSelect -ne 'y' -and $SubSelect -ne 'Y') {
echo "You did not choose a subscription to deploy in, script will exit now"
exit
}
$subscription=$subs[$ProvisionSub]
echo "Script will continue to provision in the selected subscription $subscription "
Set-AzContext -SubscriptionId $subscription.Id
echo "Azure Subscription for current session set to the following"
Get-AzContext
$select=Read-Host -Prompt "Do you wish to continue(y/n):"
if($select -ne 'y' -or $select -ne 'Y')
{
echo "Script terminating per user input"
exit
}
echo "Provisioning will continue with the selected subscription"
if ( -not (Test-Path $filename))
{
echo "Config file not found at $filename"
exit
}
else
{
echo "Found the configuration file, populating parameters from $filename"
}
$vmname=""
$osdisk=""
$rgname=""
$docopy=""
$disksize=225
foreach ($line in Get-Content $filename) {
if($line -match "^#.*") {
#Commented
continue
}
if( [string]::IsNullOrWhitespace($line)) {
#Empty line
continue
}
$entries=$line.split("=",2,[StringSplitOptions]'RemoveEmptyEntries')
#$entries=$line.split("=")
$e1=$entries[0]
$e2=$entries[1]
#Write-Host $e1 $e2 -Separator ","
$key=$e1.Trim()
$value=$e2.Trim()
#echo "Got entries" $entries[0] "->" $entries[1]
if($key -eq "vmname") {
$vmname=$value
continue
}
if($key -eq "rgname") {
$rgname=$value
continue
}
if($key -eq "newdisk") {
$osdisk=$value
continue
}
if($key -eq "copy") {
$docopy=$value
continue
}
if($key -eq "size") {
$disksize=$value
}
}
Write-Host -ForegroundColor Green -NoNewline "VM Name: "
Write-Host -ForegroundColor Cyan $vmname
Write-Host -ForegroundColor Green -NoNewline "Resource Group: "
Write-Host -ForegroundColor Cyan $rgname
Write-Host -ForegroundColor Green -NoNewline "New OS Disk location: "
Write-Host -ForegroundColor Cyan $osdisk
#sleep 30
$proceed=Read-Host "Continue? (y/n)"
if ($proceed -ne "y" -or $proceed -ne "Y") {
Write-Host -ForegroundColor Red "Script terminating..."
exit
}
$vm=Get-AzVm -Name $vmname -ResourceGroupName $rgname
if( $vm.ProvisioningState -ne "Succeeded" ) {
Write-Host -ForegroundColor Red "The target vm original provisioning status is not \" Succeeded\""
Write-Host -ForegroundColor Red "Proceeding with migration...."
}
$vmstatuses=Get-AzVm -Name $vmname -ResourceGroupName $rgname -Status
$vmstatus="Nil"
foreach ($status in $vmstatuses.Statuses){if ($status.Code -Match "Power" ){ $vmstatus=$status.Code}}
if ($vmstatus -NotMatch "deallocated") {
Write-Host -ForegroundColor Red "VM state should be de allocated before proceeding. Script will exit now. "
Write-Host -ForegroundColor Red -NoNewLine "Current VM state:"
Write-Host -ForegroundColor Red $vmstatus
exit
}
Write-Host "Proceeding to replace disks."
$vm=Set-AzVMOSDisk -VM $vm -VhdUri $osdisk -DiskSizeInGB $disksize
Update-AzVM -ResourceGroupName $rgname -VM $vm
sleep 30
Write-Host "Attempting to start the vm now"
$start=Read-Host "Continue? (y/n)"
if ($start -ne "y" -or $start -ne "Y") {
Write-Host -ForegroundColor Red "Script terminating. Start VM from the portal."
exit
}
Start-AzVM -Name $vmname -ResourceGroupName $rgname