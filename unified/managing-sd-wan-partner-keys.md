# Managing SD-WAN Partner Keys
Source: https://help.zscaler.com/unified/managing-sd-wan-partner-keys
PDF: https://help.zscaler.com/pdf/com/en/1494621.pdf

From the [Partner Integrations page](/unified/about-partner-integrations), you can view information regarding your organization's SD-WAN partner keys. For the partner key, you can see the following:
- **Partner Name**: The name of the partner
- **Key**: The partner key string
- **Last Modified By**: The date and time the partner key was last modified
- **Last Modified On**: The last admin to modify the partner key
You can also perform the following tasks for your SD-WAN partner keys:
- [Add a new partner key](#AddNewKey)
- [Edit the partner key](#EditNewKey)
- [Regenerate the partner key](#RegenerateKey)
- [Delete the partner key](#DeleteKey)
After you have added a [new partner key](/unified/managing-sd-wan-partner-keys#AddNewKey), make sure that you provide the following information to your SD-WAN partner:
- Their partner admin credentials
- The partner key
If you have [edited](/unified/managing-sd-wan-partner-keys#EditNewKey), [regenerated](/unified/managing-sd-wan-partner-keys#RegenerateKey), or [deleted](/unified/managing-sd-wan-partner-keys#DeleteKey) the partner key, make sure that you have informed your partner of the change.
[]Before adding a new partner key, make sure that you have completed the following prerequisites:
- Configured a [partner admin role](/unified/adding-partner-admin-roles) with SD-WAN partner access enabled
- Configured a [partner admin](/unified/adding-partner-admins) for the SD-WAN partner, and make sure the proper partner admin role is applied
- Reviewed your configured [locations](/unified/about-locations) and [VPN credentials](/unified/about-vpn-credentials) and assigned the proper partner to manage them. The partner's name should be displayed in the **Managed By** column for the location or VPN credential.
Your organization can only have one partner key per SD-WAN partner. You must delete the existing key before you can add a new key.
To add a new partner key:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations: SDWAN**.
-
Click **Add Partner Key**.
The **Add Partner Key** window appears.
-
In the **Add Partner Key** window, select one of the following partners from the **Name **drop-down menu:
- Cisco Viptela
- VMware SD-WAN
- Citrix SD-WAN
- CloudGenix
- HPE Aruba
- ngena
- Riverbed SteelConnect
- Silver Peak
- VMware VeloCloud
You can also search for the partner name.
For VMware SD-WAN, you must also enter an SSO URL. After adding a URL, you can click to VMware SD-WAN link to go the VMware SD-WAN portal via the Location Management page.
[See image.](#AddPartnerKey)
-
Click **Generate**.
The new partner key is immediately valid and displayed in the **Partner Integrations** page. Send the new partner key and the partner admin credentials to your SD-WAN partner.
[]To edit the partner key:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations: SDWAN**.
-
Locate the partner name in the table and click the **Edit** icon.
The **Edit Partner Key** window appears.
-
In the **Edit Partner Key** window, enter the **New Partner Key**. The new key must meet the following requirements:
- The new key must be alphanumeric (A-Z, a-z, 0-9) and exactly 12 characters in length.
- The new key cannot be the same as the **Current Partner Key**.
[See image.](#EditPartnerKey)
-
Click **Confirm**.
After confirmation, the old partner key is immediately invalidated. Send the new partner key to your SD-WAN partner.
[]To regenerate the partner key:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations: SDWAN**.
- Locate the partner name in the table and click the **Regenerate **icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, a random partner key string is immediately generated and the old string is invalidated. Send the new partner key to your SD-WAN partner.
[]To delete the partner key:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations: SDWAN**.
- Locate the partner name in the table and click the **Delete** icon.
-
In the confirmation window that appears, click **Ok**.
After confirmation, the partner key is immediately removed and invalidated. Inform your SD-WAN partner, if necessary.
[]![Add Partner Key Window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/Add%20Partner%20Key.png)
[]![Edit Partner Key page](/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/Edit%20Partner%20Key_0.png)