# Viewing the Blocked Identities
Source: https://help.zscaler.com/deception/viewing-blocked-identities
PDF: https://help.zscaler.com/pdf/com/en/1531410.pdf

You can view the following details of contained attackers or endpoints depending on the containment integration:
- The details of blocked attackers or endpoints, such as IP address, hostname, or username.
- The timestamp when the attacker's identity was added to the containment list.
- The expiration date of the containment.
- Additional details such as the device ID and machine ID, depending on the containment integration.
With CrowdStrike integration, you can also view IOC hashes, IOC IP addresses, and IOA process trees that are shared by Zscaler Deception. To learn more about CrowdStrike integration, see [Containment Configuration Guide for CrowdStrike](/deception/zscaler-deception-and-crowdstrike-deployment-guide).
To view and delete the details of the containment:
-
Go to **Orchestrate** > **Containment**.
[See image.](#containment-ip-count)
- Locate the containment integration and follow these steps based on the third-party application:
- For third-party integrations other than CrowdStrike:
-
To view containment details, click the number under the **Blocked Identities** column. A window appears listing the contained attacker's IP details.
[See image.](#deception-containment--view-attacker-ip-details)
-
To remove an entry from the list, click the **Delete **icon in the **Actions **column, and confirm your action.
[See image.](#contained-attacker-ip-details)
- For CrowdStrike integration:
-
To view containment or shared intelligence details, click one of the following options:
- **Contained IP**:** **Shows the list of contained IP addresses.
- **IOC Hash**: Shows the list of file hashes that are shared with CrowdStrike as indicators of compromise.
- **IOC IP**: Shows the list of IP addresses that are shared with CrowdStrike as indicators of compromise.
- **IOA Process Tree**: Shows the list of process trees that are shared with CrowdStrike as indicators of attack.
[See image.](#deception-crowdstrike-details)
-
To lift containment and remove the entry from one of the lists, click the **Delete **icon in the **Actions **column, and confirm your action.
[See image.](#deception-crowdstrike-ioc-entry-delete)
When the containment is lifted directly from the CrowdStrike Falcon console, the corresponding entry in the Zscaler Deception Admin Portal is also removed automatically via a scheduled job that typically runs every hour.
[]![Attacker IP count on the Containment page](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/deception-containment-list.png)
[]![View attacker IP details](/downloads/deception/orchestrate/containment-integrations/viewing-contained-attacker-details/zscaler-deception-view-attacker-ip-details.png)
[]![Delete an attacker IP](/downloads/deception/orchestrate/containment-integrations/viewing-contained-attacker-details/zscaler-deception-delete-attacker-ip.png)
[]![View CrowdStrike Containment Details ](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/deception-containment-list-crowdstrike.png)
[]![Delete a CrowdStrike IOC IP Entry ](/downloads/deception/orchestrate/containment-integrations/viewing-contained-attacker-details/zscaler-deception-ioc-page-delete.jpg)