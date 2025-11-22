# Adding SD-WAN Partner API Roles
Source: https://help.zscaler.com/unified/adding-sd-wan-partner-api-roles
PDF: https://help.zscaler.com/pdf/com/en/1491296.pdf

A Software-Defined Wide Area Network (SD-WAN) partner API role is a specific role for API access to the Internet & SaaS APIs. SD-WAN partner APIs cannot be users; only admins can be assigned to an SD-WAN partner API role. SD-WAN partner APIs can:
- Make API calls to endpoints that involve building tunnels and mapping tunnels to locations.
- Only access API endpoints (no Admin Portal interactive login allowed).
- Only perform API calls as they relate to SD-WAN partners, depending on the use case.
- Have API access using programmatic API calls.
- Be assigned full or view-only permissions to the API endpoints group given in the following procedure.
SD-WAN partner APIs do not have permission to perform the following tasks:
- Update policy configurations.
- Create or delete users or grant users access to the Admin Portal.
- Change properties or settings within the Admin Portal.
An SD-WAN partner API is not the same as a System Integration partner.
To add an SD-WAN partner API role:
- Go to **Administration **>** Admin Management **>** Role Based Access Control **>** Internet & SaaS**.
- On the **Role Management** page, click **Add SD-WAN partner API Role**.
- In the **Add SD-WAN Partner API Role** window:
- **Name**: Enter a name for the SD-WAN partner API role.
-
**Traffic Forwarding **(scope): Assign appropriate permissions for the SD-WAN partner APIs to access the Traffic Forwarding API endpoints that the partner is managing via the Internet & SaaS API. For each SD-WAN partner API role, you can configure the following permissions:
- **Full**: This permission allows SD-WAN partner APIs to view and edit the traffic-forwarding API resources.
- **View Only**: This permission allows SD-WAN partner APIs to only view the traffic-forwarding API resources.
-
**Custom**: This permission allows you to assign field-wise permissions (**Full** or **View Only**) to the API endpoints, providing further granular access to those API resources.
Selecting **Full** or **View Only **permissions applies to all the traffic-forwarding resources. To assign custom permissions, select **Custom **and assign appropriate permissions to the following API endpoints:
- Locations
- VPN Credentials
- Static IPs
- GRE Tunnels
If an SD-WAN partner API role does not have access to an API endpoint, the option to get or update resources via the API is not available.
[See image.](#sdwan-partner-api-role-image)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]![The Add SD-WAN Partner API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-sd-wan-partner-api-roles/zia-adding-sdwan-partner-api-role-add-sdwan-partner-window.png)