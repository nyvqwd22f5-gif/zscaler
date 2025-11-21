# Configuring Credentials for a Windows High-Interaction Virtual Machine
Source: https://help.zscaler.com/deception/configuring-credentials-windows-high-interaction-virtual-machine
PDF: https://help.zscaler.com/pdf/com/en/1531389.pdf

You can configure credentials for Windows high-interaction virtual machines (VMs) that an attacker might use to connect to the Windows machine.
The supported Windows operating systems are:
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022
To configure the credentials for the VM:
- Go to **Settings** > **Virtual Machines**.
-
Locate the VM for which you want to configure the credentials, and click the **Edit **icon.
[See image.](#edit-credentials-icon-vm)
-
In the **VM Details** window, under **Credentials (Username,Password)**, enter the credentials.
[See image.](#save-vm-credentials)
Enter a username and password (separated by a comma) without any spaces.
-
Click **Save**.
It can take up to 30 minutes for the landmine agent to configure the credentials for Windows.
[]![Edit VM configuration](/downloads/deception/product-documentation/settings/virtual-machines/configuring-credentials-windows-high-interaction-virtual-machine/zscaler-deception-edit-vm-hi-2.png)
[]![Configure Windows high-interaction VM credentials](/downloads/deception/product-documentation/settings/virtual-machines/configuring-credentials-windows-high-interaction-virtual-machine/zscaler-deception-vm-hi-credentials-1.png)