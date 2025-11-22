# Upgrading Zscaler Client Connector
Source: https://help.zscaler.com/unified/upgrading-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1492421.pdf

This feature applies only to Zscaler Client Connector version 4.2.1 for Windows or later.
You can require an upgrade password if you update Zscaler Client Connector in unattended mode on your users' devices (e.g., you use GPO, SCCM, or other device management methods).
You can [configure update settings](/unified/configuring-app-update-zscaler-client-connector-app-store) to update Zscaler Client Connector automatically to the latest version or to a version you specify. If you disable the auto-update option, you can use this password to provide additional security.
Before you can upgrade using the password, you need to configure it. To learn more, see [Configuring Passwords for Access in Unattended Mode.](/unified/configuring-passwords-access-unattended-mode)
You can upgrade the app on your users' devices using one of the following options:
- [Create an MST and Deploy it Using GPO or a Compatible Device Management Tool](#CreateMST)
- [Upgrade From a CLI Using the MSI File](#UpgradeMSI)
- [Upgrade Using the EXE Install File with CLI Options](#InstallEXE)
[]To create an MST file:
- Download the Zscaler Client Connector MSI installer file in the [Admin Portal](/unified/about-zscaler-client-connector-app-store).
- Follow the instructions to [create an MST file using Orca](/unified/customizing-zscaler-client-connector-install-options-msi), and add UPGRADEPASSWORDCMDLINE as one of the install options:
- Click **Tables** from the top menu, and then click **Add Row**.
- In the **Add Row** window:
- For **Property**, enter `UPGRADEPASSWORDCMDLINE`.
- Press `Enter` or click the **Value** field.
- For **Value**, enter the [generated upgrade password from the platform settings](/unified/configuring-passwords-access-unattended-mode).
- Click **OK**.
The install option appears on a new line.
After creating the MST, you can use it when [deploying Zscaler Client Connector to your users with Active Directory](/unified/deploying-zscaler-client-connector-active-directory-windows).
[]To upgrade from a CLI using the MSI file:
- Start a command prompt as an administrator.
- Enter the following command:
msiexec /i <complete path> /quiet UPGRADEPASSWORDCMDLINE=<upgrade password>
- Replace `complete path` with the absolute pathname to the MSI install file. For example, `C:\Users\User\Downloads\Zscaler-windows-1.1.0.000213-installer.msi`
- Use the `/quiet` switch to upgrade the app in silent mode.
- Replace `upgrade password` with the upgrade password that was [generated in the platform settings](/unified/configuring-passwords-access-unattended-mode).
[]To upgrade using the EXE install file:
- Start a command prompt as an administrator.
- Click **Start**.
- In the **Start Search** box, enter `cmd`, then press `CTRL+SHIFT+ENTER`.
- If the User Account Control (UAC) dialog window appears, confirm that you want to continue.
- Add the upgrade password install option to the absolute path. To add this option, enter `--upgradePasswordCommandLine ``<upgrade password>`, and replace `<upgrade password>` with the upgrade password that was [generated in the platform settings](/unified/configuring-passwords-access-unattended-mode).
- Add additional install options to customize the file based on your organization's needs. To learn more, see [Customizing Zscaler Client Connector Install Options for EXE](/unified/customizing-zscaler-client-connector-install-options-exe).