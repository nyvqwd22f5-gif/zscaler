# Testing a Threat Intelligence Decoy
Source: https://help.zscaler.com/deception/testing-threat-intelligence-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531294.pdf

You can test a deployed Threat Intelligence (TI) decoy to simulate an attack.
To test a TI decoy:
- Open a web browser.
- In the browser address bar, enter the URL of the decoy.
After the decoy web page appears, verify that it matches the application you selected while creating the decoy.
![Threat intelligence decoy test web page](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-ti-decoy-web-page.png?1651224734)
- (Optional) If the decoy web page provides a login field, enter the test credentials in both the username and password fields, and sign in.
- Log in to the Zscaler Deception Admin Portal.
- In the left navigation menu, click **Investigate**.
- Select a time frame from the drop-down menu. For example, select **Last 30 Minutes**.
![View threat intelligence decoy logs in the Investigate page](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-ti-decoy-investigate.png)
- Click the threat icon to open the attacker details pane, and then click **View Extended Details**.
If the IPinfo integration is enabled, the Deception Admin Portal attempts to geolocate the adversary and uses the country's flag (![Threat icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-ti-decoy-icon.png)
) as the threat actor's icon. If the IPinfo integration is not enabled, then the Deception Admin Portal uses a unique threat icon ( ![Threat icon](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-threat-icon.png)
).
![Attacker details pane](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-ti-decoy-view-details.png)
- Verify if all the activities performed on the decoys were captured on the **ThreatParse** and **Event Logs** tabs.
![Verify attacker activity details](/downloads/deception/product-documentation/deceive/threat-intelligence-decoys/testing-threat-intelligence-decoy/zscaler-deception-ti-decoy-threatparse-event-logs.png)