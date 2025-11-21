# Viewing the Blocked Identities
Source: https://help.zscaler.com/itdr/viewing-blocked-identities
PDF: https://help.zscaler.com/pdf/com/en/1531809.pdf

You can view the following details of contained attackers or endpoints depending on the containment integration:
- The details of blocked attackers or endpoints.
- The timestamp when the attacker's identity was added to the containment list.
- The expiration date of the containment.
With CrowdStrike integration, you can also view IOC hashes that are shared by Zscaler ITDR. To learn more about CrowdStrike integration, see [Containment Configuration Guide for CrowdStrike](/itdr/containment-configuration-guide-crowdstrike).
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
To view containment or shared intelligence details, click **IOC Hash **to view the list of file hashes that are shared with CrowdStrike as indicators of compromise.
[See image.](#deception-crowdstrike-details)
-
To lift containment and remove the entry from one of the lists, click the **Delete **icon in the **Actions **column, and confirm your action.
When the containment is lifted directly from the CrowdStrike Falcon console, the corresponding entry in the Zscaler ITDR Admin Portal is also removed automatically via a scheduled job that typically runs every hour.
[]![Attacker IP count on the containment page](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/itdr-containment-page.png)
[]![Viewing attacker IP details](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/itdr-zia-containment.png)
[]![Deleting an attacker IP](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/itdr-zia-containment-delete.png)
[]![View CrowdStrike Containment Details ](/downloads/deception/orchestrate/containment-integrations/viewing-blocked-identities/itdr-crowdstrike-hash.png)