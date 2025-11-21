# Running Landmine Agentless on Windows
Source: https://help.zscaler.com/deception/running-landmine-agentless-installer-windows
PDF: https://help.zscaler.com/pdf/com/en/1531347.pdf

This article provides instructions for running landmine agentless on the Windows platform using the command line interface (CLI).
Prerequisites
Before running landmine agentless, make sure that the following prerequisites are met:
-
Windows installer and .NET framework: .NET version 4.6.1 or later
For Windows 10 version 1607 and earlier (Zscaler recommends using the latest version of the .NET framework for Landmine agentless to work).
Microsoft Windows 7, Windows 8, and Windows 8.1 are not supported.
- You must have network connectivity from the system where the agentless service is installed to the Zscaler Deception Admin Portal on port 443. This connection is proxy aware and uses the current user’s configured proxy.
Running Landmine Agentless on Windows
To run landmine agentless on Windows:
- [Download the agentless Windows EXE file](/deception/downloading-landmine-agentless) from the Deception Admin Portal:
-
In the command prompt, enter the following command:
Landmine.Agentless.Win.x64.exe -c <Deception Admin Portal instance> -k <Agent Registration Token>
The following table describes the command parameters:
| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `-c` | The hostname of the Deception Admin Portal | Yes |
| `-k` | The Agent Registration Token | Yes |
| `-l <level>` | Enables logging to console with the specified log level. Allowed values are `info`, `debug`, and `verbose`. | No |
| `-r` | Removes the applied policy | No |
After you run the command, the landmine agentless policy is registered with the current user. After the registration, the policy is applied and the landmine agentless appears in the **Agents** table (**Settings **> **Endpoint Settings **> **Agents**) in the Deception Admin Portal.
Landmine agentless runs as the current user. If multiple users use the same system, you must run landmine agentless separately for each user.