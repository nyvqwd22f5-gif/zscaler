# Managing SD-WAN Partner Keys
Source: https://help.zscaler.com/zia/configuring-sdwan-integration
PDF: https://help.zscaler.com/pdf/com/en/1400586.pdf

On the Partner Integrations page (Administration > Partner Integrations), you can view information regarding your organization's SD-WAN partner keys. For the partner key, you can see:
- **Partner Name**: The name of the partner.
- **Key**: The partner key string.
- **Last Modified By**: The date and time the partner key was last modified.
- **Last Modified On**: The last admin to modify the partner key.
![SD-WAN Tab Within the Admin Portal](/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/SD-WAN%20page.png)
You can also perform the following tasks for your SD-WAN partner keys:
- [Add a New Partner Key](#AddNewKey)
- [Edit the Partner Key](#EditNewKey)
- [Regenerate the Partner Key](#RegenerateKey)
- [Delete the Partner Key](#DeleteKey)
After you have added a [new partner key](/zia/configuring-sdwan-integration#AddNewKey), make sure that you provide the following information to your SD-WAN partner:
- Their SD-WAN partner API client credentials
- The partner key
If you have [edited](/zia/configuring-sdwan-integration#EditNewKey), [regenerated](/zia/configuring-sdwan-integration#RegenerateKey), or [deleted](/zia/configuring-sdwan-integration#DeleteKey) the partner key, make sure that you have informed your partner of the change.
To learn more, see [About Partner Integrations](/zia/about-partner-integrations).
[]Before adding a new partner key, make sure that you have completed the following prerequisites:
- Configure a [SD-WAN partner API role](/zia/adding-sd-wan-partner-api-roles) with SD-WAN partner access enabled.
- Configure a [SD-WAN partner API client](/zia/adding-sd-wan-partner-api-clients) for the SD-WAN partner, and make sure to apply the proper partner role.
- Review your configured [locations](/zia/about-locations) and [VPN credentials](/zia/about-vpn-credentials) and assign the proper partner to manage them. The partner's name should be displayed in the **Managed By** column for the location or VPN credential.
Your organization can only have one partner key per SD-WAN partner. You must delete the existing key before you can add a new key.
To add a new partner key:
- Go to **Administration** > **Partner Integrations**.
- Select the **SD-WAN **tab.
- Click **Add Partner Key**.
The **Add Partner Key** window appears.
- In the **Add Partner Key** window, select one of the following partners from the **Name **drop-down menu. You can also search for the partner name.
- Cisco Viptela
- VMware SD-WAN
- Citrix SD-WAN
- CloudGenix
- HPE Aruba
- ngena
- Riverbed SteelConnect
- Silver Peak
- VMware VeloCloud
- Nile Secure
For VMware SD-WAN, you must also enter an SSO URL. After adding a URL, you can click the VMware SD-WAN link to go the VMware SD-WAN portal via the Location Management page.
[See image.](#AddPartnerKey)
- Click **Generate**.
The new partner key is immediately valid and displayed in the **Partner Integrations** page. Send the new partner key and the SD-WAN partner API client credentials to your SD-WAN partner.
[]To edit the partner key:
- Go to **Administration** > **Partner Integrations**.
- Select the **SD-WAN** tab.
- Locate the partner name in the table and click the **Edit** icon.
The **Edit Partner Key** window appears.
-
In the **Edit Partner Key** window, enter the **New Partner Key**. The new key must meet the following requirements:
- The new key must be alphanumeric (A-Z, a-z, 0-9) and exactly 12 characters in length.
- The new key cannot be the same as the **Current Partner Key**.
[See image.](#EditPartnerKey)
- Click **Confirm**.
After confirmation, the old partner key is immediately invalidated. Send the new partner key to your SD-WAN partner.
[]To regenerate the partner key:
- Go to **Administration** > **Partner Integrations**.
- Select the **SD-WAN **tab.
- Locate the partner name in the table and click the **Regenerate **icon.
- In the confirmation window that appears, click **Ok**.
After confirmation, a random partner key string is immediately generated and the old string is invalidated. Send the new partner key to your SD-WAN partner.
[]To delete the partner key:
- Go to **Administration** > **Partner Integrations**.
- Select the **SD-WAN **tab.
- Locate the partner name in the table and click the **Delete** icon.
- In the confirmation window that appears, click **Ok**.
After confirmation, the partner key is immediately removed and invalidated. Inform your SD-WAN partner, if necessary.
[]![Add Partner Key Window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/Add%20Partner%20Key.png)
[]![Edit Partner Key page](/downloads/zscaler-tech-pubs-style-guide/draft-articles/managing-sd-wan-partner-keys-draft/Edit%20Partner%20Key_0.png)