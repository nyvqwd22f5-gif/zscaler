# Editing a Subcloud
Source: https://help.zscaler.com/zia/editing-subcloud
PDF: https://help.zscaler.com/pdf/com/en/1402616.pdf

A subcloud is a subset of ZIA Private Service Edges or Public Service Edges, which are full-featured secure internet gateways that inspect all web traffic bi-directionally for malware, and enforce security, compliance, and next-generation firewall (NGFW) policies. ZIA Public Service Edges are deployed in Zscaler data centers (DCs) around the globe, so when your users move to a different location, they can access the internet from any device and the ZIA Public Service Edges will protect their traffic and apply your corporate policies.
You can edit a subcloud from the Subclouds page in the ZIA Admin Portal to temporarily disable the DCs under scheduled maintenance or DCs with capacity issues, trust incidents, site or region service issues, excessive latency, congestion, peering issues, etc.
To edit a subcloud:
- Go to **Administration **> **Resources **> **Subclouds**.
- Click the **Edit** icon next to the subcloud that you want to edit.
The **Edit Subcloud** window appears.
- In the **Edit Subcloud** window:
- Under **General Information**, you can view the name of the subcloud.
- Under **Data Center Schedule**, you can view a list of the DCs configured for the subcloud, and select a DC from the list.
- Under **Data Center Disabled Until (UTC Time)**, you can view and edit the date and time until which the selected DC is disabled. The time is displayed in Coordinated Universal Time (UTC). You can disable a DC for a maximum of two weeks.
[See image.](#Editing-a-Subcloud)
- Click **Save** and activate the change.
- If you disable all the DCs in a country, a confirmation window appears. Click **Confirm** to continue.
[See image.](#Confirmation-Window)
After you edit the DC list for a subcloud, the Zscaler Client Connector traffic and PAC file users are redirected 15 minutes after the app policy push. To failover immediately, you can trigger DNS requests with app policy updates on Zscaler Client Connector. To learn more, see [Understanding Subclouds](/zia/understanding-subclouds).
[]![Screenshot of Edit Subcloud](/downloads/tech-pubs-drafts/zia-draft-articles/editing-subcloud-draft-doc-48727/DC_UTCTime.png)
[![Screenshot of Edit Subcloud Confirmation Window](/downloads/tech-pubs-drafts/zia-draft-articles/editing-subcloud-draft/EditSubcloud_Confirm.png)
]