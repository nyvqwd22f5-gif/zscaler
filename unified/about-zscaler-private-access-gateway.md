# About Zscaler Private Applications Gateway
Source: https://help.zscaler.com/unified/about-zscaler-private-access-gateway
PDF: https://help.zscaler.com/pdf/com/en/1497701.pdf

Zscaler provides a predefined Auto ZPA Gateway to direct Private Applications' application segment traffic marked for inspection from Internet & SaaS to Private Applications, which is enabled by default. You cannot edit this gateway. You can also configure separate custom ZPA gateways to forward [Source IP Anchored](/unified/understanding-source-ip-anchoring) traffic to Private Applications.
This page provides the following benefits and enables you to:
- Create ZPA gateway objects that can be used in forwarding policies to redirect Source IP Anchored application traffic to the destination servers via the Private Applications App Connectors.
- Map ZPA gateways to the Source IP Anchored Private Applications server groups and the associated application segments.
About the Zscaler Private Access Page
On the Zscaler Private Access page (Infrastructure > Internet & SaaS > Network Policies > Zscaler Private Access), you can do the following:
- [Configure a ZPA Gateway](/unified/configuring-zpa-gateway).
- Search for a ZPA gateway.
- View a list of all ZPA gateways. For each ZPA gateway, you can view the following information:
- **Gateway**: The name of the gateway. You can sort this column.
- **Server Groups**: The server group configured for this ZPA gateway.
- **Application Segment**: The application segments that are associated with the configured server group.
- **Description**: Additional notes or information about the gateway.
- Edit a ZPA gateway.
- View the predefined Auto ZPA gateway.
- [Modify the table and its columns](/unified/using-tables).
![Screenshot of Zscaler Private Access Gateway page showing buttons and list used to manage ZPA gateways](/downloads/zia/policies/forwarding-control/source-ip-anchoring/about-zpa-gateway/zia_about_zscaler_private_access_gateway.png)