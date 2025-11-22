# Enabling Domain Join for Remote Users on Windows Devices
Source: https://help.zscaler.com/zpa/enabling-domain-join-remote-users-windows-devices
PDF: https://help.zscaler.com/pdf/com/en/1484216.pdf

For remote users on Microsoft Windows devices logging into an Active Directory (AD) domain for the first time, make sure that the device is provisioned by your organization's IT team with a local account on the device. The user can then complete their first-time login using that local account in order to enroll into ZPA.
User Password Sync
In the situation where the remote user's password is expired and they cannot log into Windows, the password reset can be done over ZPA, even when the device's Zscaler Client Connector is not connected to ZPA. To learn more, see [About Machine Groups](/zpa/about-machine-groups) and [Configuring Machine Provisioning Keys](/zpa/configuring-machine-provisioning-keys).
Using the ZPA connection, the device can be joined to the domain, the remote user can log in, and their credentials can be cached on the device. The workflow for the user is as follows:
- User logs into the device using their local account.
- User enrolls into ZPA using the Zscaler Client Connector on the local account.
- User updates cached credentials using [one of the methods](/zpa/enabling-domain-join-remote-users-windows-devices#cache_methods) below.
- User logs out of Zscaler Client Connector and out of the local account.
- User logs in with their Windows domain account.
You can use a PowerShell script or the RunAs command to cache credentials on Windows 7 and 10 operating systems. Neither require local administrator rights, and the local account can be configured to be very limited in order to ensure that users do not continue to use it after they’ve been enrolled into ZPA.
It is also possible to use a different shell than the standard Windows shell (i.e., explorer.exe), in order to run the cache credentials procedure in a kiosk mode setup.
[]To have the remote user update their cached credentials using:
- [A PowerShell Script](#PowerShell)
- [The RunAs command in the Windows user interface](#RunAs_UI)
- [The RunAs command in a Batch File](#RunAs_CMD)
[]Using a PowerShell script allows you to automate the process and display user interface prompts for username and password. The script can also be configured to automatically start when the user logs in with their local account, so they don’t need to start the procedure on their own.
The following is an example PowerShell script:
$User = "purple\test1"
$Password = ConvertTo-SecureString "zscaler" -AsPlaintext -Force
$UserCredentials = New-Object System.Management.Automation.PSCredential -ArgumentList @($User,$Password)
Start-Process -FilePath 'CMD.EXE' -ArgumentList '/C ECHO' -Credential $UserCredentials -LoadUserProfile
[]While the user is logged into their the local account, they need to:
- Hold down the SHIFT key and right-click on any application on the Desktop (e.g., Microsoft Outlook, Google Chrome, etc.).
- In the right-click menu, select the **Run as different user** option to open an authentication prompt.
- Enter the new credentials at the prompt to update the cached credentials.
[]Using RunAs from the command prompt allows you to configure it via a batch (.bat) file so that it is automatically displayed when the user logs in with their local account, so they don’t need to start the procedure on their own.
The following is an example RunAs .bat file script:
@ECHO OFF
SET /P user=Please enter your username:
IF "%user%"=="" GOTO Error
runas /profile /user:yourdomain\%user% "cmd.exe /C ECHO"
GOTO End
:Error
ECHO Please enter your username
:End