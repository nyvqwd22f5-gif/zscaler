# Interacting with Zscaler Client Connector Remotely
Source: https://help.zscaler.com/zscaler-client-connector/interacting-zscaler-client-connector-remotely
PDF: https://help.zscaler.com/pdf/com/en/1474686.pdf

This feature is available only for Zscaler Client Connector version 4.4 and later for Windows and Zscaler Client Connector version 4.3 and later for macOS.
You can use a CLI to interact with Zscaler Client Connector remotely to do the following:
- View the status of services.
- Enable or disable the Zscaler Private Access (ZPA) service.
- Enable or disable the Zscaler Internet Access (ZIA) service and the Zscaler Digital Experience (ZDX) service (Zscaler Client Connector version 4.8 and later for Windows only).
- Upgrade the Zscaler Digital Experience (ZDX) Module for Windows (Zscaler Client Connector version 4.7 and later for Windows only).
This feature is useful if you must interact with services on behalf of users (for example, an outage requires you to disable ZPA for all users).
Enabling the CLI
You can enable the CLI for the following OSs:
- [Windows](#win-enable-CLI)
- [macOS](#macOS-enable-CLI)
[]To enable the CLI for Windows devices:
- In the Zscaler Client Connector Portal, go to **App Profiles**. To learn more, see [Configuring Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-profiles).
- Click Windows, and then click **Add Windows Policy**.
- In the **Command Line Interface Access** section, enable the **Command Line Interface**.
- Click **Save**.
Optionally, you can require a password when disabling a service using the CLI.
To require a password when disabling the ZPA, ZIA, or ZDX service:
- If you’re adding a new policy, you must first save your policy before generating a password.
- If you’re editing an existing policy, you must first save your changes before generating a password.
- In the **Disable Services** section, do one of the following:
-
Enable **Disable ZPA Password** to require a password when disabling the ZPA service using the CLI.
The **Generate ZPA Disable Password** option appears.
-
Enable **Disable ZIA Password** to require a password when disabling the ZIA service using the CLI.
The **Generate ZIA Disable Password** option appears.
-
Enable **Disable ZDX Password** to require a password when disabling the ZDX service using the CLI.
The **Generate ZDX Disable Password** option appears.
- Click **Generate Password** to generate a password. The generated password displays in the associated **Generate <Service> Disable Password **field.
- Click **Copy** to copy the password to your clipboard. The password expires after two hours.
![CLI Access section for Windows](/downloads/zscaler-client-connector/monitoring-usage/interacting-zscaler-client-connector-remotely/zclient-connector-win-disable-services.png)
[]To enable the CLI for macOS devices:
- In the Zscaler Client Connector Portal, go to **App Profiles**. To learn more, see [Configuring Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-profiles).
- Click macOS, and then click **Add macOS Policy**.
- In the **Command Line Interface Access** section, enable **Command Line Interface**.
- Click **Save**.
Optionally, you can require a password when disabling ZPA using the CLI. The ZPA service is the only service that can require a password. The Zscaler Internet Access (ZIA) and ZDX services cannot require a password.
To require a password when disabling the ZPA service:
- If you’re adding a new policy, you must first save your policy before generating a password.
- If you’re editing an existing policy, you must first save your changes before generating a password.
- In the **Disable Services** section, enable **Disable ZPA Password** to require a password when disabling the ZPA service using the CLI.
The **Generate ZPA Disable Password** option appears.
- Click **Generate Password** to generate a ZPA password. The generated password displays in the **Generate ZPA Disable Password **field.
- Click **Copy** to copy the password to your clipboard. The password expires after two hours.
![CLI Access section for macOS](/downloads/tech-pubs-drafts/client-connector-draft-articles/interacting-zscaler-client-connector-remotely-doc-57652/macOS_CLI_Disable_Services.png)
Using the CLI
You can use the CLI for the following OSs:
- [Windows](#win-using-CLI)
- [macOS](#macOS-using-CLI)
[]To use CLI for Windows devices:
- Start a command prompt as an administrator.
- Use one of the following file paths, depending on your Windows system version:
- For 64-bit: `C:\Program Files\Zscaler\ZSACli\ZSACli.exe ``<command>`
- For 32-bit: `C:\Program Files (x86)\Zscaler\ZSACli\ZSACli.exe ``<command>`
-
Replace `<command>` with one of the following commands and press `Enter`.
-
-
-
-
-
-
-
-
-
-
-
-
[](/zscaler-client-connector/enabling-zdx-module-upgrades-cli)[](/zscaler-client-connector/viewing-and-configuring-zdx-module-upgrades)[](/zscaler-client-connector/enabling-zdx-module-upgrades-cli)[](/zscaler-client-connector/viewing-and-configuring-zdx-module-upgrades)
| Command | Result | Notes |
| ------- | ------ | ----- |
| `enable -s ``<service>` | Turn on the entered service. | Possible values for `<service>`:`zia `(indicates Zscaler Internet Access)`zpa `(indicates Zscaler Private Access)`zdx `(indicates Zscaler Digital Experience)If you are enabling ZPA for a partner tenant, add `-u ``<partner username>` after `zpa`.Can be run 5 or fewer times per minute. |
| `disable -s ``<service>` | Turn off the entered service. | Possible values for `<service>`:`zia `(indicates Zscaler Internet Access)`zpa `(indicates Zscaler Private Access)`zdx `(indicates Zscaler Digital Experience)If you enabled **Disable <Service> Password** and generated a password in app profiles, add `-p` `<disable password>` after `<service>`.Example: `ZSAcli.exe disable -s zpa -p ``<disable password>`Can be run three or fewer times per minute. |
| `status -s ``<service>` | Display the status in a JSON format of the entered service, or for all services if you enter `all`. | Possible values for `<service>`:`zia `(indicates Zscaler Internet Access)`zpa `(indicates Zscaler Private Access)`zdx `(indicates Zscaler Digital Experience)`deception `(indicates Zscaler Deception)zep (indicates Anti-Tampering)`all `(indicates all services) |
| `help` | Displays help information about the CLI arguments. | N/A |
| `update -s zdx -f ``<path to ZDX package>`` -c ``<checksum>` | Upgrades the ZDX Module with the update package in the path you enter. | You must first enable ZDX Module upgrades from the CLI. You can download the package and copy the checksum on the Client Connector App Store page. |
| `update -s zdx -u ``<url>`` -c ``<checksum>` | Upgrades the ZDX Module with the update package located at the URL you enter. | You must first enable ZDX Module upgrades from the CLI. You can download the package and copy the checksum on the Client Connector App Store page. |
If a message displays indicating that the CLI is disabled from the policy, enable the **Command Line Interface** option in the app profile.
[]To use CLI for macOS devices:
- Start a command prompt as an administrator.
-
Use the following file path:
`/Applications/Zscaler/Zscaler.app/Contents/PlugIns/zscli ``<command>`
-
Replace `<command>` with one of the following commands and press `Enter`.
-
-
-
-
-
-
-
-
-
| Command | Result | Notes |
| ------- | ------ | ----- |
| `enable -s zpa` | Turn on ZPA. | If you are enabling ZPA for a partner tenant, add `-u ``<partner username>` after `zpa`.Can be run five or fewer times per minute. |
| `disable -s zpa` | Turn off ZPA. | If you enabled **Disable ZPA Password** and generated a password in app profiles, add `-p` `<disable password>` after `zpa`.Example: `zscli disable -s zpa -p ``<disable password>`Can be run three or fewer times per minute. |
| `status -s ``<service>` | Display the status in a JSON format of the entered service, or for all services if you enter `all`. | Possible values for `<service>`:`zia `(indicates Zscaler Internet Access)`zpa `(indicates Zscaler Private Access)`zdx `(indicates Zscaler Digital Experience)`zdp` (indicates Endpoint Data Loss Prevention)`all` (indicates all services) |
| `help` | Displays help information about the CLI arguments. | Possible examples for `help`:`zscli -h``zscli enable -h``zscli disable -h``zscli status -h` |
| `diagnose -r` | Runs diagnostics for Zscaler Client Connector and outputs a file location for the diagnostics. |  |
If a message displays indicating that the CLI is disabled from the policy, enable the **Command Line Interface** option in the app profile.