# Configuring Passwords for Access in Unattended Mode
Source: https://help.zscaler.com/unified/configuring-passwords-access-unattended-mode
PDF: https://help.zscaler.com/pdf/com/en/1491361.pdf

You can require a password when uninstalling, upgrading, or reverting Zscaler Client Connector in unattended mode. These passwords provide an extra layer of security if you use your own mechanism for deploying Zscaler Client Connector on your users' devices (e.g., GPO, SCCM, or other device management methods).
This feature applies only to Zscaler Client Connector version 4.2.1 and later for Windows. These passwords are not used when users manually update, uninstall, or revert Zscaler Client Connector from their own devices. You can set up required passwords for those actions on the app profile. To learn more, see [Configuring Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
To configure the passwords for access in unattended mode:
- In the Admin Portal, go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **Windows** and click the **Platform Settings** tab.
- In the **Zscaler Client Connector Passwords for Unattended Mode** section:
- **Uninstall Password**: Enable to require the generated password when uninstalling Zscaler Client Connector using a command line.
- **Upgrade Password**: Enable to require the generated password when upgrading Zscaler Client Connector using a command line.
- **Revert Password**: Enable to require the generated password when reverting Zscaler Client Connector using a command line.
- **Password Expiration (Hours)**: Select the number of hours after which the generated password expires for each enabled password.
- **Generate Passwords**: Click to generate a new password for each enabled password.
![Configuring Passwords for Unattended Mode Access](/downloads/zscaler-client-connector-passwords-unattended-mode.png)
- Click **Save**.