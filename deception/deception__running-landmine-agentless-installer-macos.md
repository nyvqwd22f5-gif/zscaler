# Running Landmine Agentless on macOS
Source: https://help.zscaler.com/deception/running-landmine-agentless-installer-macos
PDF: https://help.zscaler.com/pdf/com/en/1531348.pdf

This article provides instructions for running landmine agentless on the macOS platform.
Prerequisites
Before running landmine agentless, make sure that the following prerequisites are met:
- A Mac computer with macOS Ventura (version 13) or later.
- You must have network connectivity from the system where the agentless service is installed to the Zscaler Deception Admin Portal on port 443. This connection is proxy aware and uses the proxy set in the `HTTP_PROXY` and `HTTPS_PROXY` environment variables. Some policies may not run unless the agentless binary is run on a GUI terminal session.
Running Landmine Agentless on macOS
To run a landmine agentless installer on macOS:
-
[Download the macOS agentless executable via cURL](/deception/downloading-landmine-agentless).
Notarization issues might occur if the executable is not downloaded using cURL due to Gatekeeper quarantine attributes.
-
In the terminal, run the following command to configure the executable permissions of the file:
$ chmod +x <full path to landmine.agentless.macos.x64>
-
Run the following command to register the agentless executable with the Deception Admin Portal:
$ sudo -i <full path to landmine.agentless.macos.x64> -c <Deception Admin Portal instance> -k <Agent Registration Token>
-
Run the following command to apply the policy. Make sure that you do not prefix `sudo` in the command:
$ <full path to landmine.agentless.macos.x64> -c <Deception Admin Portal instance>
The following table describes the command parameters:
| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `-c` | The hostname of the Deception Admin Portal | Yes |
| `-k` | The Agent Registration Token | Yes |
| `-l <level>` | Enables logging to console with the specified log level. Allowed values are `Debug`, `verbose`, and `Information`. | No |
| `-r` | Removes the applied policy | No |
After you run the command, the landmine agentless policy is registered with the current user. After the registration, the policy is applied and landmine agentless for macOS appears in the **Agents** table (**Settings **> **Endpoint Settings **> **Agents**) in the Deception Admin Portal.
Landmine agentless runs as the current user. If multiple users use the same system, you must run the agentless installer separately for each user.