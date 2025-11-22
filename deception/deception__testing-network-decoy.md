# Testing a Network Decoy
Source: https://help.zscaler.com/deception/testing-network-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531281.pdf

You can test a deployed network decoy to simulate an attack.
To test a network decoy:
- Open a web browser.
- In the browser address bar, enter the IP address of the network decoy for which the web services are enabled.
After the decoy web page appears, verify that it matches the personality you selected while creating the decoy.
![Decoy web page](/downloads/deception/deceive/network-decoys/testing-network-decoy/zscaler-deception-decoy-web-page.png)
- (Optional) If the decoy web page provides a login field, enter the test credentials. For example, enter `Admin` in both the username and password fields.
- Log in to the Zscaler Deception Admin Portal.
- In the left navigation menu, click **Investigate**.
- Select a time frame from the drop-down menu. For example, select **Last 10 Minutes** to see the most recent decoy logs.
![View decoy logs in the Investigate page](/downloads/deception/deceive/network-decoys/testing-network-decoy/zscaler-deception-decoy-log.png)
- Click the threat icon to open the attacker details pane, and then click **View Extended Details**.
The threat icon is unique for each attacker. In the example above, the threat icon is depicted as (![Threat icon](/downloads/deception/deceive/network-decoys/testing-network-decoy/zscaler-deception-threat-icon.png)
).
![Attacker details pane](/downloads/deception/deceive/network-decoys/testing-network-decoy/zscaler-deception-attacker-details-pane.png)
- Verify if all the activities performed on the decoys were captured on the **ThreatParse** and **Event Logs** tabs.
![Verify attacker activity details](/downloads/deception/deceive/network-decoys/testing-network-decoy/zscaler-deception-attacker-activity.png?1650605307)
You can test decoys configured with other services. However, you must access these services using their respective applications.