# Viewing Cloud Identity Details
Source: https://help.zscaler.com/zpc/viewing-cloud-identity-details
PDF: https://help.zscaler.us/pdf/com/en/1404611.pdf

ZPC displays information for each cloud identity it finds through entitlement mapping in your cloud deployment. You can view the following details for each identity by selecting an identity from the [Cloud Identities page](/zpc/about-cloud-identities):
- Identity properties such as the type, source, number of entitlements, etc.
- Graphical representation of everything the identity can access.
- All open alerts associated with the identity.
The cloud identity details page (Cloud Posture > Cloud Identities > Identity Name) displays information about each cloud identity in the following tabs:
- [Properties](#viewing-identity-properties)
- [Graph View](#viewing-identity-graph)
- [Entitlements](#viewing-identity-entitlements)
- [Alerts](#viewing-identity-alerts)
- [Authentication](#viewing-identity-authentication)
![View identity details on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/cloud-identity-details/about-cloud-identity-details/zpc-identity-details-page.gif)
[]
The properties tab offers information on identity details, what the identity can access, its authentication methods, power score, and metadata.
On the Properties tab, you can do the following:
- ZPC supports multiple identity attributes over multiple cloud service providers. Some attributes might be available only for certain cloud service providers.
- [View all identity attributes.](#identity-properties-table)
Some attribute details are offered by cloud service providers only for local identities and not for external identities. For example, AWS and Microsoft Azure only offer the "Has MFA" attribute information for local identities.
- View the number of entitlements, assets, asset types, and cloud accounts the identity can access.
- View the different authentication methods available to the identity. Cloud service providers offer this information only for local identities.
- View the identity's power score and power categories.
- View the identity metadata collected by ZPC. You can choose to download or copy the metadata.
![View the identity properties tab on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/about-cloud-identity-details/zpc-identities-properties-tab.png)
[]
The graph view tab offers a topological co-relation with other identities, roles, accounts, asset types, and assets. You can interact with each graph node to view more information on the details panel.
![View the identity graph view tab on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/cloud-identity-details/viewing-identity-properties-tab/zpc-identity-graph-view.gif)
[]
The entitlements tab offers entitlement information for each cloud identity such as the number of assets the identity can access, the permission set the identity has, and the number of accounts the identity can access.
On the Entitlements tab, you can do the following:
- Export the entitlement details as an Excel file.
- Search for an entitlement.
- View the following details in the entitlement table:
- **Asset Type**: View the cloud service provider-defined services the identity is entitled to access.
- **Assets**: View the asset count for the asset type.
- **Accounts**: View the number of accounts the identity is entitled to perform actions on.
- **Actions**: View the list of actions the identity is entitled to access.
- **Permission Set**: View the list of permissions the identity has.
![View the identity entitlements tab on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/cloud-identity-details/viewing-identity-graph-view-tab/zpc-identities-entitlements-tab.png)
[]
The alerts tab offers insight into the alerts generated on your cloud deployment for a specific cloud identity.
On the Alerts** **tab, you can do the following:
- Filter for alerts based on **Alert Status**.
- Search for alerts using the searchable columns.
- View the following alert details:
- **Alert ID**: Unique ID of the alert. Click to view the alert details. To learn more, see [About Alerts](/zpc/about-alerts).
- **Risk Level**: The severity level (Critical, High, Medium, or Low) of the policy violation. The severity of the alert indicates the impact the issue can have on your assets. The higher the severity, the bigger the impact.
- **Policy Name**: The title of the security policy.
- **Alert Age**: The age of the alert (in days) from the last time the Alert Status was set to **Open**.
- **Last Updated**: The timestamp for when the alert was last modified.
- **Status**: The status (**Open**, **Closed**, or **Resolved**) of the alert.
- Modify the table and its columns. You can choose which columns appear on the alert table. To learn more, see [Using Tables](/zpc/using-tables).
![View the identity alerts tab on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/cloud-identity-details/viewing-identity-entitlements-tab/zpc-identities-alerts-tab.png)
[]
The authentication tab offers authentication information on passwords, access keys, and certificates for all AWS local identities.
AWS does not offer authentication information for external identities to be collected by ZPC. ZPC only displays authentication information for AWS local identities.
On the Authentication tab (Identity Name > Authentication), you can do the following:
- View the password authentication information for the identity:
- **Status**: View whether the password is active or inactive.
- **Last Used**: View timestamp for when the password was last used by the local identity.
- **Last Changed**: View timestamp for when the password was last changed.
- **Next Rotation**: View timestamp for when the password must be changed.
- **MFA State**: View whether multi-factor authentication is enabled or disabled for the identity.
- View the access keys and their information for the identity:
- **Status**: View whether the access key is active or inactive.
- **Last Rotated**: View timestamp for when the access key was last changed for the local identity.
- **Last Used**: View timestamp for when the access key was last used by the local identity.
- **Last Used Region**: View the region the access key was last used in.
- **Last Used Service**: View the service the access key was last used to authenticate.
- View the certificates and their information for the identity:
- **Status**: View whether the certificate is active or inactive.
- **Last Rotated**: View timestamp for when the certificate was last changed for the local identity.
![View the identity authentication tab on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/viewing-cloud-identity-details/zpc-identity-details-authentication.png)
[]
-
-
-
-
-
-
-
-
-
-
-
-
[](/zpc/viewing-cloud-identity-details#viewing-identity-alerts)
| Attribute Name | Cloud Service Provider | Description |
| -------------- | ---------------------- | ----------- |
| Type | All | Zscaler determines whether the identity is human or non-human. |
| Display Name | All | Identity's display name as defined on the cloud service provider. If a display name does not exist for the identity, ZPC displays the username or the email address. |
| Identity ID | All | Identity ID as defined on the cloud service provider. For example, ARN on AWS or User Principal Name on Azure. |
| Email | All | Email address for human identities. |
| Phone | All | Phone number for human identities. |
| Job Title | All | Job title for human identities. |
| Power Score | All | Power score which is a number between 0–100 determined by ZPC based on the entitlements the identity holds. The score determines the potential power the identity owns. |
| Power Category | All | Identities that possess more than 80 in power score are also assigned power categories. The following power categories are available on ZPC:
Data Admin
Storage Admin
Compute Admin
IAM Admin
Security Admin
Infrastructure Admin
CICD Admin
Secret Admin
AI Admin
Log Admin
Application Admin
Cost Admin |
| Source | All | Local or external identities as derived from the identity metadata. Local identities are usually IAM users and external identities are granted permission to access the Cloud Service Provider but are not locally available on any of the onboarded accounts. |
| Cloud Account Origin | All | Cloud Account Name and the ID where the local identity was created. Not available for external identities. |
| Alerts | All | Open alert count for a particular identity. Click the alert count to view all open alerts. To learn more, see Viewing the Identity Alerts Tab. |
| Entitlements | All | Entitlement count for a particular identity. Entitlements are used to provide identities access to resources in your cloud deployment. |
| Assets | All | The number of assets the identity is entitled to access. |
| Asset Types | All | The number of asset types the identity is entitled to access. |
| Cloud Accounts | All | The number of cloud accounts the identity is entitled to access. |
| Regions | All | The number of regions the identity is entitled to access. |
| Cloud | All | Indicates the cloud service provider the identity can access. |
| Created On | AWS, Azure, GCP | Time stamp of when the identity was created on the cloud service provider. This is available only for local identities. |
| Has MFA | AWS, Azure | Identities with multi-factor authentication enabled or not. Cloud service providers offer this information only for local identities. |
| Has Password | AWS | Identity with password-based authentication. |
| Has Access Keys | AWS | Identity with access key-based authentication. |
| Has Certificate | AWS | Identity with certificate-based authentication. |
| Account Status | All | Identity's enabled or disabled status on a cloud service provider. AWS offers this information only for local identities. |
| Object ID | Azure | Unique Azure identifier for an identity. |
| User Type | Azure | Identity type as defined by Azure as Guest or Member. |