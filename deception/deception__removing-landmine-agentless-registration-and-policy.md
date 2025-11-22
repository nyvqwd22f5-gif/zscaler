# Removing Landmine Agentless Policy and Registration
Source: https://help.zscaler.com/deception/removing-landmine-agentless-registration-and-policy
PDF: https://help.zscaler.com/pdf/com/en/1531350.pdf

This article provides instructions for removing the landmine agentless policy and registration on the Windows, macOS, and Linux platforms.
Removing the Landmine Agentless Policy and Registration on Windows
To remove the landmine agentless policy and registration on Windows:
-
Run the following command to remove the agentless policy:
Landmine.Agentless.Win.x64.exe -c <Zscaler Deception Admin Portal instance> -k <Agent Registration Token> -r
You must run this command separately for each user.
-
Delete the `C:\ProgramData\lma` folder to remove the agentless registration.
This folder path is hidden. To view the folder, enable the **Show hidden files and folders** option in Windows.
- After the folder is deleted, log in to the Zscaler Deception Admin Portal.
- Go to **Settings **> **Endpoint Settings **> **Agents.**
-
Select the Windows agentless installer you want to delete, and then choose **Delete Selected** from the **Actions **drop-down menu.
[See image.](#delete-agentless-windows)
Removing the Landmine Agentless Policy and Registration on macOS
To remove the landmine agentless policy and registration on macOS:
-
Run the following command to remove the agentless policy:
$ <full path to landmine.agentless.macos.x64> <Deception Admin Portal instance> -k <Agent Registration Token> -r
You must run this command separately for each user.
-
Delete the `/etc/lma` folder to remove the agentless registration.
You must have root privileges to delete the folder.
- After the folder is deleted, log in to the Deception Admin Portal.
- Go to **Settings **> **Endpoint Settings **> **Agents.**
-
Select the macOS agentless installer you want to delete, and then choose **Delete Selected** from the **Actions **drop-down menu.
[See image.](#delete-landmine-agentless-macos)
Removing the Landmine Agentless Policy and Registration on Linux
To remove the landmine agentless policy and registration on Linux:
-
Run the following command to remove the agentless policy:
$ <full path to /landmine.agentless.linux.x64.exe> <Deception Admin Portal instance> -k <Agent Registration Token> -r
You must run this command separately for each user.
-
Delete the `/etc/lma` folder to remove the agentless registration.
You must have root privileges to delete the folder.
- After the folder is deleted, log in to the Deception Admin Portal.
- Go to **Settings **> **Endpoint Settings **> **Agents.**
-
Select the Linux agentless installer you want to delete, and then choose **Delete Selected** from the **Actions **drop-down menu.
[See image.](#delete-landmine-agentless-linux)
[]![Delete landmine agentless on Windows](/downloads/deception/deceive/landmine-decoys/agents/landmine-agentless/removing-landmine-agentless-registration-and-policy/zscaler-deception-delete-action-windows-new.jpg)
[]![Delete landmine agentless on macOS](/downloads/deception/deceive/landmine-decoys/agents/landmine-agentless/removing-landmine-agentless-registration-and-policy/zscaler-deception-delete-action-new.jpg)
[]![Delete landmine agentless on Linux](/downloads/deception/deceive/landmine-decoys/agents/landmine-agentless/removing-landmine-agentless-registration-and-policy/zscaler-deception-delete-action-linux-new.jpg)