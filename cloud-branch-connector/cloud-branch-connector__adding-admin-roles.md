# Adding Admin Roles
Source: https://help.zscaler.com/cloud-branch-connector/adding-admin-roles
PDF: https://help.zscaler.com/pdf/com/en/1420576.pdf

Configuring admin roles is one of the tasks you must complete when configuring role-based permissions for [admins](/cloud-branch-connector/adding-cloud-connector-admins) in the Zscaler Cloud & Branch Connector Admin Portal.
Prerequisites
When configuring roles:
- You must have the proper permissions to do so, [as detailed below](#permissions).
- You must have organizational scope.
Adding Admin Roles
To configure admin roles:
- Go to **Administration **>** Role Management**.
- Select **Add Admin Role**.
The **Add Admin Role** window appears.
[See image.](#Image1)
- In the **Add Admin Role** window:
- **Name**: Enter a name** **for the role.
- []**Permissions**: Permissions allow you to control an admin's access to the major features of the portal. For each admin, you must select permissions in the following categories:
- [Dashboard](#dashboard-access)
- [Template (Location & Provisioning)](#template-loc-prov)
- [Location Management](#location-management)
- [API Key Management](#api-key)
- [NSS Logging](#nss-logging)
- [Cloud Connector Provisioning](#cloud-provisioning)
- [Administrator Management](#administrator-management)
- [Forwarding (Traffic, DNS & Logs)](#traffic-dns)
- [Remote Assistance Management](#remote-assist)
- [Public Cloud Config Management](#PublicCloudConfigManagement)
- Click **Save **and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
You can [edit or delete](/cloud-branch-connector/editing-deleting-or-duplicating-items) admin roles at any time.
For ZIdentity-enabled tenants, you must assign admin roles in the ZIdentity Admin Portal. To learn more, see [About Administrative Entitlements](/zslogin/about-administrative-entitlements).
[]In **Dashboards**, admins can view predefined dashboards that enable real-time visibility into your organization's internet traffic in a range of areas, including Logs and Insights.
Choose one of the following permissions:
- **View** **Only**: Allows admins only to view all dashboards.
- **None**: Doesn't allow admins access to dashboards.
[]In** Location Management**, admins can view and edit locations.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Location Management**.
- **View Only**: Allows admins to view, but not edit, items in** Location Management**.
- **None**: Doesn't allow admins access to locations.
[]In **API Key Management**, admins can view, remove, edit, or regenerate the base URL and key.
Choose one of the following permissions:
- **Full**: Allows admins full access to remove, edit, or regenerate the API Key.
- **View Only**: Allows admins to view the API key but not edit, remove, or regenerate it.
- **None**: Doesn't allow admins access to **API Key Management**.
[]In **Nanolog Streaming Service (NSS) Logging**, admins can add NSS Servers, Deploy NSS Virtual Appliances, Download MIB Files, and view NSS Feeds.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **NSS Logging**.
- **None**: Doesn’t allow admins access to **NSS Logging**.
[]In **Cloud Connector Provisioning**, admins can add Cloud Connector Groups, access deployment templates, and access Branch Connector Images.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Cloud Connector Provisioning**.
- **View Only**: Allows admins to view, but not edit, items in **Cloud Connector Provisioning**.
- **None**: Doesn't allow admins access to **Cloud Connector Provisioning**.
[]In **Template (Location & Provisioning)**, admins can create and delete location templates and provisioning templates.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Template (Location & Provisioning)**.
- **View Only**: Allows admins to view, but not edit, items in **Template (Location & Provisioning)**.
- **None**: Doesn't allow admins access to **Template (Location & Provisioning)**.
[]In** Administrator Management**, admins can add other admins, search for configured admins, and view a list of all admins configured for your organization.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Administrator Management**.
- **View** **Only**: Allows admins to view, but not edit, items in **Administrator Management**.
- **None**: Doesn't allow admins access to** Administrator Management**.
[]In** Forwarding (Traffic, DNS & Logs)**, admins have access to **DNS Policies**, **Traffic Forwarding**, **Gateways**, and **Log & Control Forwarding**. Admins can also define rules for firewall filtering in** Network Services** and** IP & FQDN Groups**.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in** Forwarding (Traffic, DNS & Logs)**.
- **View** **Only**: Allows admins to view, but not edit, items in **Forwarding (Traffic, DNS & Logs)**.
- **None**: Doesn't allow admins access to** Forwarding (Traffic, DNS & Logs)**.
[]In **Remote Assistance Management**, admins can allow Zscaler Support to securely and remotely log in to your Cloud & Branch Connector Admin Portal.
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Remote Assistance Management**.
- **View** **Only**: Allows admins to view, but not edit, items in **Remote Assistance Management**.
[]![The Add Admin Role window accessed from the Zscaler Cloud & Branch Connector Admin Portal. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/adding-admin-roles-draft-doc-47676/CB%20Adding%20Admin%20Roles.png)
[]
In **Public Cloud Config Management**, admins can create, edit, delete, and view [Partner Integrations](/cloud-branch-connector/about-partner-integrations).
Choose one of the following permissions:
- **Full**: Allows admins full access to features in **Public Cloud Config Management**.
- **View Only**: Allows admins to view, but not edit, items in **Public Cloud Config Management**.
- **None**: Doesn't allow admins access to **Public Cloud Config Management**.
To enable this feature, contact Zscaler Support.