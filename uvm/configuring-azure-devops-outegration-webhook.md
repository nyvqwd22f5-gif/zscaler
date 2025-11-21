# Configuring the Azure DevOps Outegration Webhook
Source: https://help.zscaler.com/uvm/configuring-azure-devops-outegration-webhook
PDF: https://help.zscaler.com/pdf/com/en/1532593.pdf

The Azure DevOps outegration webhook enables automatic syncing of Azure DevOps ticket updates such as Status or SLA changes to their corresponding Zscaler SecOps tickets, reducing the need for manual changes. This step is required when configuring the Azure DevOps to SecOps ticket mapping to keep the tickets in the two systems in sync. To learn more, see [Configuring the Azure DevOps Outegration.](/uvm/configuring-azure-devops-outegration)
[See image.](#uvm-outegration-config)
Configuring the Azure DevOps Webhook
To set up your Azure DevOps webhook:
- Log in to the [Azure Portal.](https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize?redirect_uri=https%3A%2F%2Fportal.azure.com%2Fsignin%2Findex%2F&response_type=code%20id_token&scope=https%3A%2F%2Fmanagement.core.windows.net%2F%2Fuser_impersonation%20openid%20email%20profile&state=OpenIdConnect.AuthenticationProperties%3DZVjiwziwkqMm09ulCtjcFHak_lElmz1-GR3JLeWLxQsF7QjBNKvv9QvLEFH2HcEndSvxqwH8TYIz05Rs-KLkXn5DBfmJfiZ9aE2z3zu7Op006IlpU9ju4tkaKXkLjVtymohcjPOPwTCbV0AO-wSe_IcmX-SWqpR8VrT9TqiH-dKSpSt3Ors_jAkH4T7FhpT-_mDwOdyu6j1x8jas38xjKGG__EjqIp_1RCpWSEvyj4W2WsNVmo4WJHF201lUOCruzvvvkLQWVlJgCNeSPAED_sNLW0UgWO6h18vBbJAT1zaiGvOs98n5J279Fr2jEe3ubIBwpaPdljHfGmjY_3bAHUNZ1-9_Yj1mho1-kuG6Db6arWKhCzvWGeYfiM5_8dBI6io5UiU12LzaXKm8BnkFsfZ5TkLknok2_a0CCDsjB5Io_KV9PkOoCWUwmjg0Glsk-pQc9kTdIdhT_xZE4O4c4NLUlpHVyFfIDBjFOWENYUs&response_mode=form_post&nonce=638943031944613686.MDNjY2Q4MDUtMDU1OC00ZTdkLWI2NjAtMzRkNGEyOTgwMTRjNzU1ZGVkOGEtNzljYy00YWFiLWEwNWYtZWE2ZDQzMDA4MTNm&client_id=c44b4083-3bb0-49c1-b47d-974e53cbdf3c&site_id=501430&instance_aware=true&client-request-id=4632ec44-3590-4f2c-97ca-ccbf3b65c19a&x-client-SKU=ID_NET472&x-client-ver=8.3.0.0)
- Go to **Organization **>** Projects** and select a project.
The project page appears.
[See image.](#uvm-organization-project)
-
Click **Project Settings** in the bottom-left corner.
The **Project details **page appears.
[See image.](#ds-project-settings-image)
- In the left-side navigation, go to **General **> **Service Hooks**.
- Click **Create subscription**.
The **Service **page appears.
- On the **Service **page, select **Web Hooks**.
- Click **Next**.
The **Trigger **page appears.
- Select an event to trigger and configure filters. Select the options based on the work item that you are configuring the outegration for.
[See image.](#uvm-trigger)
- Click **Next**.
The **Action **page appears.
- For **URL, **enter `https://webhook.avalor.io/integration/{avalor-account-id}/azure_DevOps`.
[See image.](#uvm-url)
- Click **Test**.
- Click **Finish **if the test is successful.
After your webhook is set up, configured triggers for field updates in your Azure DevOps outegration mapping automatically sync changes made to Azure DevOps tickets with their corresponding SecOps tickets.
[]
![Shows the details on sync changes made from Azure DevOps to Zscaler SecOps ticket](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops-outegration-webhook/uvm-webhoook.png)
[]
![Shows the projects in the Azure DevOps portal](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops-outegration-webhook/ds-projectpage.png)
[]
![Select the event to trigger and configure the filters](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops-outegration-webhook/uvm-trigger-workitemupdated.png)
[]
![Select and configure the action to perform on the Action page](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops-outegration-webhook/uvm-url.png)
[]
![Shows the project settings page in the Azure DevOps portal](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-58700-configuring-azure-devops-outegration-webhook/ds-project-settings.png)