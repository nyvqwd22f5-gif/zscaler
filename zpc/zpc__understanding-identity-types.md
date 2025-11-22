# Understanding Identity Types
Source: https://help.zscaler.com/zpc/understanding-identity-types
PDF: https://help.zscaler.com/pdf/com/en/1446971.pdf

ZPC classifies identities into the following types:
- **Human**: Identities created for your organization employees and third-party vendors to access your cloud deployment resources.
- **Non-Human**: Identities created to accommodate service-level needs, such as service accounts, virtual machines, or lambda functions.
ZPC uses the following rules for each cloud service provider to determine whether a local or external identity is human or not:
| Cloud Service Provider | Classification | Identity Name |
| ---------------------- | -------------- | ------------- |
| AWS | Non-Human | Instance Profile |
| AWS | Non-Human | Auto Scaling Group |
| AWS | Non-Human | Lambda Function |
| AWS | Human | Public Account |
| AWS | Human | Canonical User |
| AWS | Human | Federated |
| AWS | Human | Root Account |
| AWS | Human | IAM User |
| AWS | Human | User |
| Azure | Non-Human | Service Principal |
| Azure | Non-Human | Microsoft Apps |
| Azure | Non-Human | Virtual Machine |
| Azure | Non-Human | Managed Identities |
| Azure | Human | Other Microsoft Entra (formerly Azure AD) users |
| Azure | Human | Public Account |
| GCP | Non-Human | Service Account |
| GCP | Non-Human | Compute Instance |
| GCP | Non-Human | Cloud Function |
| GCP | Non-Human | Group |
| GCP | Non-Human | Domain |
| GCP | Human | Public Account |
| GCP | Human | G Suite User |