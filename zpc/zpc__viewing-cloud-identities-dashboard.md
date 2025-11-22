# Viewing the Cloud Identities Dashboard
Source: https://help.zscaler.com/zpc/viewing-cloud-identities-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1394186.pdf

The Cloud Identities dashboard is an identity inventory that offers visibility into:
- Users and services that have permissions to assets and accounts.
- Identities that pose potential high risk.
- Powerful identities with multiple roles and permission sets.
- Identity count trend over time.
Most dashboard widgets and icons are interactive. You can drill down to view the Cloud Identities Dashboard in more detail.
About Power Identities
Power identities have multiple admin-level roles and permissions. Power identities are categorized into power categories such as Data Admin, an identity with a permission set enabling it to perform high-level data operations.
About Identity Types
ZPC categorizes identities into the following types:
- **Human**: Identities created for your organization employees and third-party vendors to access your cloud deployment resources.
- **Non-Human**: Identities created to accommodate service-level needs, such as service accounts, virtual machines, or lambda functions.
About Identity Sources
ZPC categorizes identities into the following sources:
- **Local**: Identities manually created in a cloud service provider. To remove a local identity from your organization, you need to manually revoke permissions across all services the identity was authorized to use.
- **External**: Identities which you have authorized to use your cloud service provider but are not local identities (e.g., contractors).
- **Federated**: Users that are defined on your user directory such as Okta, and are authorized to use cloud service providers. When you remove a federated user from your organization, they lose all roles and permissions.
On the Cloud Identities Dashboard page (Dashboard > Cloud Identities), you can do the following:
- Filter identities by the following parameters:
- **Business Units**: Select one or multiple business units. Business units are logical groups of multiple cloud accounts.
- **Cloud Type**: Select one or multiple cloud service providers for which you want to view assets.
- **Account**: Select one or multiple cloud accounts for which you want to view cloud assets.
- **Regions**: Select one or multiple regions for which you want to view cloud assets.
- View the following Cloud Identities trend for identities on your cloud deployment:
- **All Identities**: View all local, federated, external identities and their alerts for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, or last 90 days).
- **Non-Human**: View all non-human (for example, virtual machines) local, federated, external identities and their alerts for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, or last 90 days).
- **Human**: View all human local, federated, external identities and their alerts for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, or last 90 days).
The Cloud Identities trend is a cumulative chart: the sum of local, federated, and external identities is the total number of identities.
- View **Non-Human Identities**: View identity count for local, external, and federated non-human identity categories. For each category, view powerful and inactive non-human identities.
- View **Human Identities**: View identity count for local, external, and federated human identity categories. For each category, view powerful and inactive human identities.
- View **Top Power Categories**: View identity count for each powerful administrative category.
- View **Roles by Number of Identities**: View top 10 roles by identity count.
- View **Accounts by Number of Identities**: View top 10 accounts by identity count.
- View **Identities by Number of Resources**: View top 10 identities by resource count.
![View the Cloud Identity dashboard on ZPC.](/downloads/zpc/dashboards/about-cloud-identities-dashboard/zpc-cloud-identity-dahboard.png?1675934440)