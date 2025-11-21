# Adding Internet & SaaS Posture Profiles
Source: https://help.zscaler.com/unified/adding-internet-saas-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493041.pdf

The posture profile is a set of criteria evaluated on a user’s device that can be used in an Internet & SaaS policy. You can create an Internet & SaaS posture profile for a specific trust level and add it to an app profile. To learn more about posture profiles, see [About Internet & SaaS Posture Profiles](/unified/about-internet-saas-posture-profiles).
Creating an Internet & SaaS Posture Profile
To add an Internet & SaaS posture profile for Zscaler Client Connector:
- In the Admin Portal, go to **Policies > Common Configuration > Resources > Internet & SaaS Posture Profiles**.
- Select a platform.
-
Click **Add ZIA Posture**. The **Add ZIA Posture** window appears.
![Add ZIA Posture window for adding ZIA Posture Profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-zia-posture-profiles-48330/Add-ZIA_Posture-Type2.png)
- In the **Add ZIA Posture **window:
- For** Posture Definition**, enter **Posture Name**.
-
For** High Trust**, **Medium Trust**, **Low Trust: **Choose a trust level**. **Posture checks for all trust levels are evaluated by Zscaler Client Connector on the device and the highest matching level is used in Internet & SaaS posture.
To define the expression:
- Click the **Select Device Posture** drop-down menu to view a list of [available postures](/unified/configuring-device-posture-profiles).
- Select a device posture for the trust level. You can search for a specific device posture and click **Clear All **to remove all items.
- Click **Add** to include another device posture and repeat the first two steps. You can select up to 5 device postures.
- Review your expression in the **Expression Preview **field. Within a group, the logic is AND. Between groups, the logic is OR.
- Click **Save**.
Assign an Internet & SaaS Posture Profile to an App Profile
Posture profiles are evaluated on devices assigned to [app profiles](/unified/configuring-zscaler-client-connector-app-profiles). To add an Internet & SaaS posture profile to an existing or new app profile:
- In the Admin Portal,** **go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select the operating system and and then select one of the following:
- Select an existing policy and click **Edit**.
- Click **Add Policy **to create a new policy.
- In the **ZIA Posture Profile** drop-down menu, select the Internet & SaaS posture profile you created.
- When finished, do one of the following:
- Click **Save** if you're editing an existing policy.
- Click **Add **if you're creating a new policy.
![Add ZIA Posture Profile option in App Profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-zia-posture-profiles-48330/Add-ZIA_Posture-Type_App-Profiles.png)