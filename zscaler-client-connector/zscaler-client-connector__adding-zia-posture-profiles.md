# Adding ZIA Posture Profiles
Source: https://help.zscaler.com/zscaler-client-connector/adding-zia-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1385061.pdf

The posture profile is a set of criteria evaluated on a user’s device that can be used in Zscaler Internet Access (ZIA) policy. You can create a ZIA posture profile for a specific trust level and add it to an app profile. To learn more about posture profiles, see [About ZIA Posture Profiles](/zscaler-client-connector/about-zia-posture-profiles).
Creating a ZIA Posture Profile
To add a ZIA posture profile for Zscaler Client Connector:
- In the Zscaler Client Connector Portal, go to **Administration **> **ZIA Posture Profile**.
- Click **Add ZIA Posture**. The **Add ZIA Posture **window appears.
![Add ZIA Posture window for adding ZIA Posture Profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-zia-posture-profiles-48330/Add-ZIA_Posture-Type2.png)
- In the **Add ZIA Posture **window:
- For **Posture Definition**, enter a **Posture Name**.
- For** High Trust**, **Medium Trust**, **Low Trust: **Choose a trust level.** **Posture checks for all trust levels are evaluated by Zscaler Client Connector on the device and the highest matching level is used in ZIA posture.
To define the expression:
- Click the **Select Device Posture** drop-down menu to view a list of [available postures](/zscaler-client-connector/configuring-device-posture-profiles).
- Select a device posture for the trust level. You can search for a specific device posture and click **Clear All **to remove all items.
- Click **Add** to include another device posture and repeat the first two steps. You can select up to 5 device postures.
- Review your expression in the **Expression Preview **field. Within a group, the logic is AND. Between groups, the logic is OR.
- Click **Save**.
Assign a ZIA Posture Profile to an App Profile
Posture profiles are evaluated on devices assigned to [app profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles). To add a ZIA posture profile to an existing or new app profile:
- In the Zscaler Client Connector Portal,** **go to **App Profiles**.
- Select the OS platform you want to add the policy to and then select one of the following:
- Select an existing policy and click **Edit**.
- Click **Add Policy **to create a new policy.
- In the **ZIA Posture Profile **drop-down menu, select the ZIA posture profile you created.
- When finished, do one of the following:
- Click **Save** if you're editing an existing policy.
- Click **Add **if you're creating a new policy.
![Add ZIA Posture Profile option in App Profiles](/downloads/tech-pubs-drafts/client-connector-draft-articles/adding-zia-posture-profiles-48330/Add-ZIA_Posture-Type_App-Profiles.png)