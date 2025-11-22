# Testing Gen AI Decoys
Source: https://help.zscaler.com/deception/testing-generative-ai-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531595.pdf

This article provides information on how to test if configured generative AI (Gen AI) decoys are properly deployed and working. Gen AI decoys can be deployed on internal networks, Zero Trust networks, endpoints, and public cloud platforms. When users interact with these decoys, the interaction is considered an attack and an event is generated on the Zscaler Deception dashboard. The deployment of decoys and the subsequent event-generating interaction depend on the type of Gen AI decoy, so the steps required to test a decoy vary.
Prerequisites
Before testing a Gen AI decoy, ensure that you have:
- Endpoints with a landmine agent, a landmine agentless, or Zscaler Client Connector installed, depending on your preferred method for deploying endpoint deception.
-
A landmine policy configured with the necessary modules. The landmine policy must have a selection criterion that matches at least one endpoint. For the purposes of testing, you can select **Catch All** as the selection criterion for the landmine policy.
Selecting **Catch All** as the selection criterion applies policies to all endpoints. Exercise caution when using this option.
Testing an Interactive Gen AI Decoy
To test an interactive Gen AI decoy:
- Open your web browser.
- In the browser address bar, enter the IP address or FQDN for the internal or Zero Trust network decoy that has the Gen AI service enabled.
- Verify that the web page matches with your selected static or dynamic application.
- Interact with the application. For example, if you have deployed a chatbot, enter a prompt.
- Go to the [Investigate dashboard](/deception/understanding-zscaler-deception-dashboard), locate the event corresponding to the interaction with the interactive Gen AI decoy, and verify the details.
Testing a File-Based Gen AI Decoy
To test a file-based Gen AI decoy:
- In the Zscaler Deception Admin Portal, go to **Settings **> **Endpoint Settings **> **Agents**.
- Locate an active agent with at least one matched policy in the **Matched Policy **column, and click the **View **icon under the **Actions **column.
- On the **Details **pane that appears, ensure that the **File Decoys **module with **Pre-Configured Datasets** is configured in the landmine policy.
- To test the decoy, make a note of the file path displayed in the **Details **pane.
-
Open Windows PowerShell on the endpoint in which you want to test the decoy.
The landmine policy must have been deployed to the endpoint based on the selection criterion.
-
Go to the path where the file decoy is deployed using the following command:
``cd `<file_path>`
-
Open the file using the following command:
``Get-Content .\``<file_name>``
The file is opened, and an event is generated in the Deception Admin Portal.
- Verify the event on the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).