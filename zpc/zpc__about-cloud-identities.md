# About Cloud Identities
Source: https://help.zscaler.com/zpc/about-cloud-identities
PDF: https://help.zscaler.com/pdf/com/en/1404606.pdf

ZPC scans your cloud deployment for identity metadata and creates a cloud infrastructure entitlement mapping across all the permissions and access granted in the public cloud. The public cloud has both human and non-human identities. Human identities are users created on your cloud deployment and are assigned roles and permissions to perform actions. Non-human identities also use roles and permission to perform actions to circumvent bad security practices. For example, consider a virtual machine which needs to connect to an AWS account periodically and write information into an S3 bucket. You can store AWS admin credentials on the virtual machine which are then used to access the AWS account. Storing sensitive credentials on cloud assets is not a good security practice. To circumvent this, cloud service providers offer users to assign roles and permissions to non-human identities, such as virtual machines. To learn more, see [Understanding Identity Types](/zpc/understanding-identity-types).
About Power Identities
Power identities have multiple admin-level roles and permissions. Power identities with power score highter than 80 are categorized into power categories such as Data Admin, an identity with a permission set enabling it to perform high-level data operations.
About Identity Source
ZPC categorizes human identities into the following two sources:
- **Local**: Users manually created in a cloud service provider. To remove a local user from your organization, you need to manually revoke permissions across all services the user was authorized to use.
- **External**: Users which you have authorized to use your cloud service provider but are not local users (e.g., contractors, federated identities).
The Identities page provides the following benefits and enables you to:
- Gain a panoramic view of identity management and security in your multi-cloud environment.
- View the power score and power categories to quickly understand which identities pose greater risk if they are compromised.
- View all human and non-human identities and entitlements in your cloud infrastructure.
About the Cloud Identities Page
On the Cloud Identities page (Cloud Posture > Identities), you can do the following:
- Filter identities using available parameters. To learn more, see [Using Filters](/zpc/using-filters#identity-filters).
- Export cloud identities as a .xlsx file.
- Search for an identity.
- View the following cloud identity details for each identity:
- **Type**: View whether the identity is human or non-human.
- **Name**: View the identity name as defined in your cloud type. Click the identity name to see identity details. To learn more, see [Viewing Cloud Identity Details](/zpc/viewing-cloud-identity-details).
- **Power Score**: View the identity power score, which is a number between 0–100. The score determines the potential power the identity owns.
- **Power Category**: View the power category the identity belongs to, such as Data Admin.
- **Source**: View whether the identity is local or external.
- **Alerts**: View the alert count related to the identity. Select the alert count to view all open alerts for the identity. To learn more, see [Viewing the Identity Alerts](/zpc/viewing-cloud-identity-details#viewing-identity-alerts).
- **Entitlements**: View the entitlement count which the identity can access.
- **Assets**: View the number of assets the identity can access.
- **Asset Types**: View the number of asset types the identity can access.
- **Cloud Accounts**: View the number of cloud accounts the identity can access.
- **Cloud**: View the cloud service provider the identity belongs to.
![View the Identities page on ZPC.](/downloads/zpc/cloud-posture/cloud-identities/about-cloud-identities/zpc-identities.png)