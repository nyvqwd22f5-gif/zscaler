# About Zscaler Private Access Gateway
Source: https://help.zscaler.com/zia/about-zpa-gateway
PDF: https://help.zscaler.com/pdf/com/en/1401521.pdf

Zscaler provides a predefined Auto ZPA Gateway to direct ZPA application segment traffic marked for inspection from ZIA to ZPA, which is enabled by default. You cannot edit this gateway. You can also configure separate custom ZPA gateways to forward [Source IP Anchored](/zia/about-source-ip-anchoring) traffic to ZPA.
This page provides the following benefits and enables you to:
- Create ZPA gateway objects that can be used in forwarding policies to redirect Source IP Anchored application traffic to the destination servers via the ZPA App Connectors.
- Map ZPA gateways to the Source IP Anchored ZPA server groups and the associated application segments.
About the Zscaler Private Access Page
On the Zscaler Private Access page, you can do the following:
- [Configure a ZPA Gateway](/zia/configuring-zpa-gateway).
- Search for a ZPA gateway.
- View a list of all ZPA gateways. For each ZPA gateway, you can view the following information:
- **Gateway**: The name of the gateway. You can sort this column.
- **Server Groups**: The server group configured for this ZPA gateway.
- **Application Segment**: The application segments that are associated with the configured server group.
- **Description**: Additional notes or information about the gateway.
- [Edit a ZPA gateway](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- View the predefined Auto ZPA gateway.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
![Screenshot of Zscaler Private Access Gateway page showing buttons and list used to manage ZPA gateways](/downloads/zia/policies/forwarding-control/source-ip-anchoring/about-zpa-gateway/zia_about_zscaler_private_access_gateway.png)