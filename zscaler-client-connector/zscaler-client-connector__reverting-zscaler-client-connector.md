# Reverting Zscaler Client Connector to the Previous Version
Source: https://help.zscaler.com/zscaler-client-connector/reverting-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1404826.pdf

If a recent upgrade wasn't successful for some users (e.g., they have issues connecting to Zscaler Client Connector), they can revert to the previous version. This feature applies to Zscaler Client Connector version 3.9 and later for Windows and Zscaler Client Connector version 4.1 and later for macOS.
Only admins can enable this option. If you're not a Zscaler Client Connector admin, contact your organization's support team about enabling this option.
After this feature is enabled, users can revert to the previous version in Zscaler Client Connector.
The revert option is not supported for non-persistent virtual desktop infrastructure (VDI).
Enabling the Revert Option in the Zscaler Client Connector Portal
- [Windows](#windows)
- [macOS](#macOS)
[]Enable this option before installing Zscaler Client Connector version 3.9 or later for Windows.
- Verify that auto-update to the latest version is not enabled. If it is enabled, disable it. To learn more, see [Configuring Update Settings for Zscaler Client Connector](/zscaler-client-connector/configuring-update-settings-zscaler-client-connector).
- In the Zscaler Client Connector Portal, go to **App Profiles** > **Windows**.
- Click **Add Windows Policy**.
- Click **Enable Zscaler Client Connector Revert**.
- If you want to require users to enter a password to revert to the previous version, add a password in the **Revert Password** field.
- To run the revert process in unattended mode and require a password, configure a revert password in platform settings. To learn more, see [Configuring Passwords for Access in Unattended Mode](/zscaler-client-connector/configuring-passwords-access-unattended-mode).
[]Enable this option before installing Zscaler Client Connector version 4.1 or later for macOS.
- Verify that auto-update to the latest version is not enabled. If it is enabled, disable it. To learn more, see [Configuring Update Settings for Zscaler Client Connector](/zscaler-client-connector/configuring-update-settings-zscaler-client-connector).
- In the Zscaler Client Connector Portal, go to **App Profiles** > **macOS**.
- Click **Add macOS Policy**.
- In the General section, click **Enable Zscaler Client Connector Revert**.
- If you want to require users to enter a password to revert to the previous version, add a password in the **Revert Password** field.
Reverting to a Previous Version in Zscaler Client Connector
- [Windows](#windows-revert)
- [macOS](#macOS-revert)
[]There are two ways users can revert to the previous Zscaler Client Connector version for Windows:
- In Zscaler Client Connector, click **More**. In the **Troubleshoot **menu, click **Revert App**.
- On the CLI, enter one of the following commands depending on your system:
- 32-bit system: `%ProgramFiles(x86)%\Zscaler\RevertZcc\``<previous version installer>`` --revertzcc 1 --exportLogs 1 --mode unattended`
- 64-bit system: `%ProgramFiles(x64)%\Zscaler\RevertZcc\``<previous version installer>`` --revertzcc 1 --exportLogs 1 --mode unattended`
For `<previous version installer>`, make sure to use the path of the version before the upgrade. On devices that are upgraded, there are two installers in the `\Zscaler\RevertZcc` folder. One installer is the upgraded version. The other installer is the version before the upgrade. If you [configured a revert password for access in unattended mode](/zscaler-client-connector/configuring-passwords-access-unattended-mode), add `--revertPasswordCommandLine ``<revert password>` to the command and replace `<revert password>` with the generated revert password in platform settings.
When users revert to a previous version, Zscaler Client Connector does the following with updates made since the most recent upgrade:
- Retains configuration files for any users and partner tenants that have been added.
- Retains any changes to service entitlements.
- Removes configuration files for any deleted or logged-out users and any deleted partner tenants.
- Retains the ZPA certificate if an updated certificate has been uploaded.
- Retains any certificates and keys that have been set up for authenticating machine tunnel access.
[]There are two ways users can revert to the previous Zscaler Client Connector version for macOS:
- In Zscaler Client Connector, click **More**. In the **Troubleshoot **menu, click **Revert App**.
- On the CLI, enter the following command:
`sudo sh /Applications/Zscaler/RevertZcc/``<previous version installer>``/Contents/MacOS/installbuilder.sh --revertzcc 1 --exportLogs 1 --mode unattended`