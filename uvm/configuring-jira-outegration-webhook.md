# Configuring the Jira Outegration Webhook
Source: https://help.zscaler.com/uvm/configuring-jira-outegration-webhook
PDF: https://help.zscaler.com/pdf/com/en/1527986.pdf

The Jira outegration webhook enables automatic syncing of Jira issue updates such as Status or SLA changes to their corresponding tickets, reducing the need for manual changes. This step is required when configuring the Jira to ticket mapping to keep issues and tickets in sync. To learn more, see [Configuring the Jira Outegration](/uvm/configuring-jira-outegration).
[See image.](#jira-ticket-step)
This article provides instructions for setting the Jira webhook and applies to both Jira Cloud and Jira Data Center. To learn more, refer to the [Atlassian documentation](https://developer.atlassian.com/server/jira/platform/webhooks/#registering-a-webhook).
To set up your Jira webhook:
- Log in to your Jira console as a user with the **Administer Jira **global permission. To learn more, refer to the [Atlassian documentation](https://support.atlassian.com/jira-cloud-administration/docs/manage-global-permissions/).
-
Go to **Settings** > **System**.
[See image.](#settings-system)
- Select the **Webhooks** tab.
-
Click **Create a WebHook**.
[See image.](#create-webhook)
- In the dialog window:
- **Name**: Enter a name for the webhook.
- **Status**: Select **Enabled**.
-
**URL**: Paste the following URL into the field: `https://webhook.avalor.io/integration/``<Account ID>``/jira`. Replace `<Account ID>` with your account ID.
[See image.](#name-status-url)
- In the **Issue related event**s section:
- **Filter**: Configure a filter to send updates from the relevant project only. The filter format is `project = ``<Your Project Key>`.
-
**Issue**: Select the **updated** and **deleted** checkboxes.
[See image.](#issue-related-events)
- Click **Create**.
After your webhook is set up, configured triggers for field updates in your Jira outegration mapping automatically sync changes made to Jira issues with their corresponding tickets.
[]**![6c544582-bba2-4a1e-9f9e-fe893e3a7c46.png](/downloads/uvm/configure/outegrations/jira-outegration-webhook/6c544582-bba2-4a1e-9f9e-fe893e3a7c46.png)
**
[]**![78bca9c5-8b74-4ee0-be18-730ab18f76c4.png](/downloads/uvm/configure/outegrations/jira-outegration-webhook/78bca9c5-8b74-4ee0-be18-730ab18f76c4.png)
**
[]![d035c3e7-b540-4673-9d7f-820a0686d512.png](/downloads/uvm/configure/outegrations/jira-outegration-webhook/d035c3e7-b540-4673-9d7f-820a0686d512.png)
[]![6a9e7f5d-4473-4081-9f42-498f2fdb7c27.png](/downloads/uvm/configure/outegrations/jira-outegration-webhook/6a9e7f5d-4473-4081-9f42-498f2fdb7c27.png)