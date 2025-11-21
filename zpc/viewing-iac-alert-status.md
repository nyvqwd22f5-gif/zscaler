# Viewing IaC Alert Status
Source: https://help.zscaler.com/zpc/viewing-iac-alert-status
PDF: https://help.zscaler.com/pdf/com/en/1415046.pdf

By default, whenever an IaC alert is triggered for IaC policy violations, the status of the alert is displayed as *Open* in the ZPC Admin Portal. When you address the issue, ZPC updates the alert status as *Resolved*.
However, ZPC automatically changes the IaC alert status to *Closed* in the following scenarios on each platform:
- [GitHub](#github)
- [GitLab](#gitlab)
- [Jenkins](#jenkins)
- [GitHub Actions](#githubactions)
- [Azure Repos](#azurerepos)
- [Terraform Cloud](#terraform)
When you view the alert details, you can see the reason why the alert was closed, as shown in the following image.
![View the alert details and alert status description](/downloads/zpc/iac-integrations/about-iac-alert-status/zpc-alert-status-description.png)
- []IaC integration is deleted
- When a repository is deleted
- When a repository is deselected in the ZPC Admin Portal
- Branch is deleted
- Resource is deleted
- IaC subscription is expired or removed
- []IaC integration is deleted
- When a repository is deleted
- When a repository is deselected in the ZPC Admin Portal
- Branch is deleted
- Resource is deleted
- IaC subscription is expired or removed
- []IaC integration is deleted
- Resource is deleted
- IaC subscription is expired or removed
- []IaC integration is deleted
- Resource is deleted
- IaC subscription is expired or removed
- []IaC integration is deleted
- Azure repo is deleted
- IaC subscription is expired or removed
- []IaC integration is deleted
- Terraform workspace is deleted
- IaC subscription is expired or removed