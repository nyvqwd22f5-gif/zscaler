# Running Landmine Agentless on Linux
Source: https://help.zscaler.com/deception/running-landmine-agentless-installer-linux
PDF: https://help.zscaler.com/pdf/com/en/1531349.pdf

This article provides instructions for running landmine agentless on the Linux platform.
Prerequisites
Before running landmine agentless, make sure that the following prerequisites are met:
- Supported Linux distributions:
- Debian 10 or later
- Ubuntu 20.04 or later LTS releases
- Red Hat Enterprise Linux version 8 or later
- Fedora 35 or later
- openSUSE Leap 15.3 or later
- You need network connectivity from the system where the agentless service is installed to the Zscaler Deception Admin Portal instance on port 443. This connection is proxy aware and uses the proxy set in the `HTTP_PROXY` and `HTTPS_PROXY` environmental variables.
Running Landmine Agentless on Linux
To run landmine agentless on Linux:
- [Download the Linux agentless executable file](/deception/downloading-landmine-agentless) from the Deception Admin Portal.
-
In the terminal, run the following command to configure the executable permission of the file:
$ chmod +x <full path to landmine.agentless.linux.x64>
-
Run the following command to register the agentless executable with the Deception Admin Portal:
$ sudo -i <full path to landmine.agentless.linux.x64> -c <Deception Admin Portal instance> -k <Agent Registration Token>
-
Run the following command to apply the policy. Make sure that you do not prefix `sudo` in the command:
$ <full path to landmine.agentless.linux.x64> -c <Deception Admin Portal instance> -k <Agent Registration Token>
The following table describes the installation parameters:
| Parameter | Description | Required |
| --------- | ----------- | -------- |
| `-c` | The hostname of the Deception Admin Portal | Yes |
| `-k` | The Agent Registration Token | Yes |
| `-l <level>` | Enables logging to console with the specified log level. Allowed values are `info`, `debug`, and `verbose`. | No |
| `-r` | Removes the applied policy | No |
After you run the command, the landmine agentless policy is registered with the current user. After the registration, the policy is applied and landmine agentless for Linux appears in the **Agents** table (**Settings **> **Endpoint Settings **> **Agents**) in the Deception Admin Portal.
Landmine agentless runs as the current user. If multiple users use the same system, you must run the agentless installer separately for each user.