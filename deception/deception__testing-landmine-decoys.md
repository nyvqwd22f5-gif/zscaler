# Testing Landmine Decoys
Source: https://help.zscaler.com/deception/testing-landmine-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531584.pdf

This article provides information on how to test if the configured landmine decoys are properly deployed and working. The landmine decoys are deployed on endpoints via different methods (agents, agentless, and Zscaler Client Connector). The landmine decoys deploy a number of different types of lures configured in the landmine policies that are applied to endpoints based on the configured criterion. When users interact with these decoys, the interaction is considered an attack and an event is generated on the Zscaler Deception dashboard. The deployment of decoys and the subsequent event-generating interaction depends on the type of lures configured. Hence, the steps required to test a landmine decoy depend on the specific type of lure configured.
Prerequisites
Before testing a landmine decoy, ensure that you have:
- Endpoints with a landmine agent, a landmine agentless, or Zscaler Client Connector installed, depending on your preferred method for deploying endpoint deception.
-
A landmine policy configured with the necessary modules. The landmine policy must have a selection criterion that matches at least one endpoint. For the purposes of testing, you can select **Catch All** as the selection criterion for the landmine policy.
Selecting **Catch All** as the selection criterion applies policies to all endpoints. Exercise caution when using this option.
Testing a Landmine Decoy
Follow the steps below to test a landmine decoy configured with the File Decoy module:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
-
Locate an active agent with at least one matched policy in the **Matched Policy **column, and click the **View **icon under the **Actions **column.
[See image.](#locate-agent)
- On the **Details **pane that appears, ensure that the policy module that you want to test is available. For example, if you want to test **File Decoys**, ensure that the details of **File Decoys **configured in the landmine policy appears.
-
To test a file decoy, make a note of the file path displayed in the **Details **pane.
[See image.](#details-pane)
-
Open Windows PowerShell on the endpoint in which you want to test the decoy.
The landmine policy must have been deployed to the endpoint based on the selection criterion.
-
Go to the path where the file decoy is deployed using the following command:
``cd `<file_path>`
-
Open the file using the following command:
``Get-Content .\``<file_name>``
[See image.](#command-shell)
The file is opened, and an event is generated in Zscaler Deception Admin Portal.
- Verify the event on the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
A file decoy can be configured as a custom file decoy (**PPT**, **EXCEL**, **WORD**, or **HTML**), credential file decoy, or preconfigured file dataset decoy. You can use the same command to test any of these different types of file decoys. To learn more about configuring file decoys, see [Configuring the File Decoys Module](/deception/configuring-file-decoys-module).
[]
![zscaler-deception-locate-agent.png](/downloads/deception/deceive/landmine-decoys/policies/testing-landmine-decoys/zscaler-deception-locate-agent.png)
[]
![zscaler-deception-path-name-details-pane.png](/downloads/deception/deceive/landmine-decoys/policies/testing-landmine-decoys/zscaler-deception-path-name-details-pane.png)
[]
![zscaler-deception-commands-test-file-decoy.png](/downloads/deception/deceive/landmine-decoys/policies/testing-landmine-decoys/zscaler-deception-commands-test-file-decoy.png)