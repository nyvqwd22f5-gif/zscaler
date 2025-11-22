# Uninstalling Zscaler Client Connector
Source: https://help.zscaler.com/unified/uninstalling-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1492366.pdf

This article is for Zscaler Client Connector admin use only. If you are not a Zscaler Client Connector admin, contact your organization's support team about uninstalling Zscaler Client Connector.
This article provides instructions for uninstalling Zscaler Client Connector. When [configuring the app profile,](/unified/configuring-zscaler-client-connector-app-profiles) you have the option of providing an **Uninstall Password** that users must enter to uninstall the app. You can also utilize a single-use Uninstall One-Time Password (OTP) in [Enrolled Devices](/unified/viewing-device-fingerprint-enrolled-device).
You can manually uninstall the app from individual devices on each of the following platforms:
- [Manually Uninstall Zscaler Client Connector in Windows](#Windows)
- [Manually Uninstall Zscaler Client Connector in macOS](#macOS)
- [Manually Uninstall Zscaler Client Connector in Linux](#Linux)
- [Manually Uninstall Zscaler Client Connector in Android](#Android)
- [Manually Uninstall Zscaler Client Connector in Android on ChromeOS](#Chrome)
- [Manually Uninstall Zscaler Client Connector in iOS](#iOS)
[]To uninstall Zscaler Client Connector:
- On the device, go to **Zscaler >** **ZSAInstaller**.
-
Double-click the **uninstall **application.
![The Zscaler Client Connector uninstall application for Windows](/downloads/client-connector/downloading-deployment/uninstalling-zscaler-client-connector/clientconnector-uninstall-windows.png)
- Provide the **Uninstall Password** as [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles).
[]To uninstall Zscaler Client Connector:
- Go to the Zscaler folder on the device.
-
Double-click **UninstallApplication**.
![The Zscaler Client Connector uninstall application for macOS](/downloads/client-connector/downloading-deployment/uninstalling-zscaler-client-connector/clientconnector-uninstall-macos.png)
- Provide the **Uninstall Password** as [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles).
[]To uninstall Zscaler Client Connector:
-
Run the following command:
sudo /opt/zscaler/UninstallApplication
- Provide the **Uninstall Password** as [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles).
[]To uninstall Zscaler Client Connector:
- On the device, tap and hold the Zscaler Client Connector icon on the home screen.
- Drag the Zscaler Client Connector icon to the top of the home screen to the **Uninstall** icon.
- Click **OK** in the message that displays.
![Uninstalling the Zscaler Client Connector app from the Andriod home screen](/downloads/tech-pubs-drafts/client-connector-draft-articles/uninstalling-zscaler-client-connector/uninstall_zcc_Android.png)
A message appears at the bottom of the home screen indicating that the app was uninstalled.
[]To uninstall Zscaler Client Connector:
- Locate Zscaler Client Connector on the device.
- Touch and hold Zscaler Client Connector, and then tap the **Uninstall **icon (![The Uninstall icon for iOS](/downloads/z-app/downloading-and-deploying-zscaler-app/how-do-i-uninstall-zscaler-app/Uninstall-icon-iOS.png)
).
-
Tap **Delete**.
![Uninstalling the Zscaler Client Connector on iOS](/downloads/z-app/downloading-and-deploying-zscaler-app/how-do-i-uninstall-zscaler-app/Uninstall-ZApp-iOS.png)
- For iPhone X and later, tap **Done**. For iPhone 8 or earlier, tap the home button.
[]To uninstall Zscaler Client Connector:
- On the device, right-click the Zscaler Client Connector icon and select the **Uninstall **icon.
- Click **Uninstall** in the message that displays.
![Uninstalling the Zscaler Client Connector app from Chromebook](/downloads/tech-pubs-drafts/client-connector-draft-articles/uninstalling-zscaler-client-connector/ChromeOS_Uninstall_on_Device.png)
The icon and app are removed from the device.
You can also uninstall the app from your users' devices using one of the following options:
- [Uninstall from the command-line using the MSI file](#command-line-option)
- [Uninstall by removing the MST file from GPO](#remove-from-GPO)
- [Uninstall in macOS with a shell script](#shell-script)
- [Uninstall in Windows with a batch file](#batch-file)
- [Uninstall in Windows with PowerShell](#powershell)
If you are a Zscaler Client Connector admin and are unable to uninstall Zscaler Client Connector using the methods provided here, contact Zscaler Support.
[]To uninstall Zscaler Client Connector from your user's device:
- Start a command prompt as an administrator.
-
Enter the following command:
msiexec /x <complete path> /quiet UNINSTALLPASSWORD=<uninstall password>
- Replace <complete path> with the absolute pathname to the MSI install file (e.g., C:\Users\User\Downloads\Zscaler-windows-1.1.0.000213-installer.msi).
- Use the /quiet switch to uninstall the app in silent mode.
- Replace <uninstall password> with the password that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles). In this example, the organization's password is safemarch123.
- If you [configured a password for access in unattended mode](/unified/configuring-passwords-access-unattended-mode), replace `UNINSTALLPASSWORD` with `UNINSTALLPASSWORDCMDLINE`, and replace `<uninstall password>` with the uninstall **Password** that was generated in the platform settings.
![Running the MSI file with a command-line option to uninstall Zscaler Client Connector](/downloads/client-connector/downloading-deployment/uninstalling-zscaler-client-connector/clientconnector-uninstall-commandprompt.png)
[]Ensure that the [password you added to the MST file](/unified/customizing-zscaler-client-connector-install-options-msi) is the same as the **Uninstall Password** that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles) or, if you [configured a password for access in unattended mode](/unified/configuring-passwords-access-unattended-mode), the uninstall **Password** that was generated in the platform settings.
To remove the MST file from your users' devices in an Active Directory (AD) environment:
- Log in to the AD environment (Domain Controller) as an admin user.
- For your OU, right-click the GPO Policy and select **Edit**.
- Go to **User Configuration **>** Policies **>** Software Settings **>** Software installation**.
-
Right-click the MST file, then select **All Tasks **> **Remove...**.
![Removing the MST file from GPO to uninstall Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/removing-zscaler-app/how-do-i-uninstall-zscaler-app/a51298ed-c44c-4b13-9474-c86ab36de521_display.png?1603369003)
After the file is removed, the app is uninstalled from your users' devices.
[]To uninstall Zscaler Client Connector from your user’s macOS device:
- Go to the **Utilities** folder.
- Double-click the **Terminal** icon.
-
Enter the following command:
sudo sh /Applications/Zscaler/.Uninstaller.sh <uninstall password>
Replace <uninstall password> with the password that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles). In this example, the organization's password is safemarch123.
![Using a shell script to uninstall the Zscaler Client Connector from macOS devices](/downloads/z-app/removing-zscaler-app/how-do-i-uninstall-zscaler-app/shell-script-macos.png)
[]To uninstall Zscaler Client Connector from your users’ Windows device:
-
Create a `.bat` file with the following batch script:
@ECHO OFF
SET ZSCALER_PASSWORD=<uninstall password>
IF EXIST ""%PROGRAMFILES(X86)%"\Zscaler\ZSAInstaller\uninstall.exe" (
"%PROGRAMFILES(X86)%"\Zscaler\ZSAInstaller\uninstall.exe --mode unattended
) ELSE (
"%PROGRAMFILES%"\Zscaler\ZSAInstaller\uninstall.exe --mode unattended
)
Replace <uninstall password> with the password that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles). In this example, the organization’s password is safemarch123.
If you [configured a password for access in unattended mode](/unified/configuring-passwords-access-unattended-mode), replace `ZSCALER_PASSWORD` with `ZSCALLER_UNINSTALL_PASSWORD_JWT`, and replace <uninstall password> with the uninstall **Password** that was generated in the platform settings.
- Start a command prompt as an administrator.
-
To run the batch file, enter its absolute path. In this example, the batch file is Uninstall-Z-App.bat and its absolute path is C:\Users\Administrator\Desktop\batch\Uninstall-Z-App.bat
![Running the batch file to uninstall the Zscaler Client Connector](/downloads/z-app/downloading-deployment/uninstalling-zscaler-app/Running-Zscaler-App-batch-file.png)
If you are still running into issues with batch file, consider using Windows PowerShell as an alternative to uninstalling Zscaler Client Connector. For example, if you are using complex passwords that include a combination of numbers, letters, and special characters (e.g., 123jsf%2!!@&jaK), then Windows PowerShell is more suitable to use.
[]To uninstall Zscaler Client Connector via PowerShell from your user's device:
- Go to PowerShell.
-
Enter the following command to ensure `ExecutionPolicy` is not restricted:
Set-ExecutionPolicy RemoteSigned
- You can enter the commands individually or create a PowerShell script to start the uninstallation process.
- [To enter the commands individually](#PowerShellIndividual)
- [To create a PowerShell script in NotePad](#PowershellScript)
-
After uninstallation, enter the following to reset the password:
[Environment]::SetEnvironmentVariable('ZSCALER_PASSWORD','', 'User')
[]
-
To set the variable to your <uninstall password>, enter the following:
[Environment]::SetEnvironmentVariable('ZSCALER_PASSWORD','<uninstall password>','User')
Replace `<uninstall password>` with the password that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles).
If you [configured a password for access in unattended mode](/unified/configuring-passwords-access-unattended-mode), replace `ZSCALER_PASSWORD` with `ZSCALLER_UNINSTALL_PASSWORD_JWT`, and replace <uninstall password> with the uninstall **Password** that was generated in the platform settings.
-
To confirm the variable is set correctly, enter the following:
[Environment]::GetEnvironmentVariable('ZSCALER_PASSWORD', 'User')
The `<uninstall password>` is returned.
-
To start the uninstall process, enter the following.
Start-Process -FilePath "C:\Program Files\Zscaler\ZSAInstaller\uninstall.exe"--mode unattended"
You might need to change the file path if it is incorrect. Check where your `Zscaler` folder is located to find the file path to `uninstall.exe`.
[]
-
In NotePad, create a PowerShell script with the following script.
[Environment]::SetEnvironmentVariable('ZSCALER_PASSWORD','<uninstall password>','User')
[Environment]::GetEnvironmentVariable('ZSCALER_PASSWORD', 'User')
Start-Process FilePath "C:\Program Files (x86)\Zscaler\ZSAInstaller\uninstall.exe" -ArgumentList "-mode unattended"
Replace `<uninstall password>` with the password that was [configured in the app profile](/unified/configuring-zscaler-client-connector-app-profiles).
If you [configured a password for access in unattended mode](/unified/configuring-passwords-access-unattended-mode), replace `ZSCALER_PASSWORD` with `ZSCALLER_UNINSTALL_PASSWORD_JWT`, and replace <uninstall password> with the uninstall **Password** that was generated in the platform settings.
You might need to change the file path if it is incorrect. Check where your `Zscaler` folder is located to find the file path to `uninstall.exe`.
- Save it as `test.ps1`.
-
Return to PowerShell to enter the following to start uninstallation.
.\test.ps1