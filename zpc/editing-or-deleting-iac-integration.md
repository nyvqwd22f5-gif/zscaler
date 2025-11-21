# Editing or Deleting an IaC Integration
Source: https://help.zscaler.com/zpc/editing-or-deleting-iac-integration
PDF: https://help.zscaler.com/pdf/com/en/1403381.pdf

You can edit or delete IaC integrations as required. You can choose to add more repositories for scanning, remove repositories from scanning, or delete an IaC integration account.
Whenever you delete an account from IaC integration, remove a repository from scanning in the ZPC Admin Portal, delete the resource or branch from the version control system or CI/CD pipeline, alert notifications will not be sent for that account and the alert status changes to *Closed** ***on the Alerts page. To learn more, see [About Alert Status](/zpc/about-alert-status).
Editing an IaC Integration
To edit an IaC integration:
- Go to **Administration** > **Version Control & CI/CD Systems**.
- On the **IaC Integrations** page, you can choose to edit any of the following integrations:
- Under **Version Control Systems**, select **GitHub**, **GitLab**, or **Azure Repos**.
- Under **CI/CD Tool**s, select **Jenkins**, **GitHub Actions**, **Azure Pipelines**, or **Others**.
- Click the **Edit** icon for the account that you want to edit.
[See image.](#edit)
- Add or remove repositories or change other values as required.
- Click **Finish**.
Deleting an IaC Integration
To delete an IaC integration:
- Go to **Administration** > **Version Control & CI/CD Systems**.
- On the **IaC Integrations** page, you can choose to delete any of the following integrations:
- Under **Version Control Systems**, select **GitHub**, **GitLab**, or **Azure Repos**.
- Under **CI/CD Tool**s, select **Jenkins**, **GitHub Actions**, **Azure Pipelines**, or **Others**.
- Click the **Delete** icon for the account that you want to delete.
[See image.](#delete)
- A confirmation message appears. Click **Delete** to proceed.
[See image.](#confirm)
Whenever you delete a GitHub integration, the Zscaler IaC app is also automatically removed from the Installed Apps and Authorized Apps section within GitHub.
[![Click the Edit icon to edit an IaC integration](/downloads/zpc/iac-integrations/editing-or-deleting-iac-integration/zpc-edit-iac.png)
]
[![Click the Delete icon to delete an IaC integration](/downloads/zpc/iac-integrations/editing-or-deleting-iac-integration/zpc-delete-iac.png)
]
[![Delete the IaC integration](/downloads/zpc/iac-integrations/editing-or-deleting-iac-integration/zpc-delete-iac-msg.png)
]