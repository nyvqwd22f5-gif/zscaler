# Integrating CrowdStrike with Adaptive Access Engine
Source: https://help.zscaler.com/unified/integrating-crowdstrike-adaptive-access-engine
PDF: https://help.zscaler.com/pdf/com/en/1508496.pdf

The Adaptive Access Engine receives user and device context signals from CrowdStrike, which are required to control user and device access to applications via Zscaler. You can integrate CrowdStrike with Adaptive Access Engine to establish a connection and automate the event response workflows using webhooks and API client configurations. CrowdStrike shares the following context signals with the Adaptive Access Engine: CrowdStrike Operating System (OS) Score, Zero Trust Assessment (ZTA) Score, ZTA Sensor Score, and Overall Score.
This feature is in limited availability. Contact Zscaler Support for assistance.
Prerequisites
Ensure that you have:
- A CrowdStrike account with admin privileges.
- An admin role in Experience Center that allows you to integrate CrowdStrike with Adaptive Access Engine.
To integrate CrowdStrike with Adaptive Access Engine:
- [1. Create an API client.](#aae-configureapiclient)
- [2. Configure the webhook.](#aae-configurewebhook)
- [3. Integrate CrowdStrike in Experience Center.](#aae-integrate-exp-center)
- [4. Configure the workflow.](#aae-addworkflows)
After completing the integration, you can proceed to [add the Adaptive Access profiles](/unified/adding-adaptive-access-profile).
[]The CrowdStrike API client acts as a unique identifier and authentication mechanism, allowing the Adaptive Access Engine to securely access and interact with the CrowdStrike Falcon platform.
- Log in to the [CrowdStrike Falcon console](https://falcon.crowdstrike.com/login/).
-
Go to **Support and resources** > **API Clients and Keys **> **Create** **API client**.
[See image.](#aae-cs-createapiclientbutton)
- In the **Create API Client** window, enter the** Client Name** and **Description**.
-
Select the following **API scopes** with Read permissions: Detection, Device control policies, Incidents, Vulnerabilities, IOCs, Prevention policies, Response policies, Workflows, API integration scope, and Zero Trust Assessment (ZTA). API scope defines the level of access granted to Adaptive Access Engine to access specific data when interacting with the CrowdStrike API.
[See image.](#aae-cs-addapi-clientdetails)
-
Click **Create**.
The API client is created.
[See image.](#aae-cs-copy-idsecret)
-
Copy and save the **Client ID**, **Client Secret**, and **Base URL**.
Make sure to copy the values because this information is not shown again. In case you don't copy the values, you need to create another API client.
- []Go to **Policies** > **Common Configuration** > **Adaptive Access** > **Integrations**.
-
Click the **Edit **icon for CrowdStrike.
[See image.](#aae-crwd-edit)
- On the **Integrations** page, enter the following details:
- **Base URL**: Enter the URL that was generated when the API client was created on the CrowdStrike Falcon console. This URL is required for Adaptive Access Engine to connect to the CrowdStrike account.
- **Webhook URL**: The Webhook URL is generated after you enter the Base URL. Copy the Webhook URL, as you need to add this value while configuring the webhook on the CrowdStrike Falcon console. The webhook URL is the designated address where CrowdStrike can automatically send real-time context signals.
- **Customer ID**: The customer ID is available on the **Profile** page on the CrowdStrike Falcon console:
- On the CrowdStrike home page, click the **Profile** icon in the top-right corner.
-
Copy the **Customer ID** that is displayed on the **User profile** page.
[See image.](#aae-cs-custid)
- **Client ID**: Enter the client ID you copied after the API client was created on the CrowdStrike Falcon console.
- **Client Secret**: Enter the client secret you copied after the API client was created on the CrowdStrike Falcon console.
- **Shared Secret**: [Enter the secret key you added while configuring the webhook](#aae-cs-sharedsecret).
- **Status**: By default, the connection status is disabled. Click the toggle to enable the status.
-
Click **Test Integration** to verify if the connection is successful.
A message appears indicating the connection between CrowdStrike and Adaptive Access Engine is successful.
[See image.](#aae-crwd-configuration)
- Click **Save**.
[]A webhook is required to send context signals from the CrowdStrike Falcon platform to Adaptive Access Engine.
- Log in to the [CrowdStrike Falcon console](https://falcon.crowdstrike.com/login/).
- Go to **CrowdStrike store** > **All apps** > **CrowdStrike Webhook**.
-
Click **Configure**.
[See image.](#aae-cs-configurebutton)
- In the next window that appears, click **Add Configuration**.
-
On the **Configure CrowdStrike Webhook** page:
- **Name**: Enter a name for the webhook.
- **Webhook URL**: Add the webhook URL you copied while integrating CrowdStrike in the Experience Center.
-
[]**HMAC Secret key**: Use any Hash-based Message Authentication Code (HMAC) generator tool to obtain a key and enter that value. The secret key is used to verify the authenticity and integrity of data exchanged between CrowdStrike and Adaptive Access Engine using the HMAC algorithm.
Enter the same value in the Experience Center while integrating CrowdStrike.
[See image.](#aae-cs-addwhookdetails)
- Click **Save Configuration**.
[]A workflow is an automated action that is initiated by a predefined trigger (security event or incident). The events or incidents can be defined in the workflow and these signals are sent to Adaptive Access Engine via the webhook plugin.
You need to create three workflows: Score Changed, New Incident, and Incident Update.
- Log in to the [CrowdStrike Falcon console](https://falcon.crowdstrike.com/login/).
- Search for **Workflows | Fusin SOAR** and select it.
- Click **Create workflow** > **Create workflow from scratch**, then click** Next**.
- On the **Add trigger** page:
- **Pick a Trigger**: Search for and select the required event (e.g., Zero Trust Assessment > Host assessment change) that must initiate the workflow.
- **Type**: Select **Overall assessment** from the drop-down menu.
- Under **Event triggers**, choose the relevant event category based on your organization's requirement.
-
To define the workflow, click the arrow on the trigger.
[See image.](#aae-cs-arrowontrigger)
-
Next, click the **Action **icon.
[See image.](#aae-cs-actionicon)
-
On the **Add action** page:
- Search for and select **Call webhook**.
- **Webhook name**: Select the webhook you created earlier. This webhook is used to send the context signals to Adaptive Access Engine.
- **Data format**: Select **Default **from the drop-down menu.
- **Data to include**: Select the required data that must be included in the action based on your organization's requirement.
- Click **Next**.
[See image.](#aae-cs-actiondetails)
The webhook is added as an action and displayed on the page.
-
Click **Finish**.
[See image.](#aae-cs-finishaction)
- In the **Add workflow name and description** window, enter the **Name** and **Description**.
-
Select **On** for the **Workflow status**.
[See image.](#aae-cs-saveworkflow)
-
Click** Save workflow**.
Whenever there is a change in the trigger, the workflow calls the webhook and signals are sent to the Adaptive Access Engine.
[]![The Integrations page displaying a table and an annotation around the Edit icon under the Actions column.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-crowdstrike-editicon.png)
[]![The Integrations page displaying the different fields, and a list of signals and their value type.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-crowdstrikeintegration.png)
[]![Click the Create API client button to add a new API client](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-addapiclient.png)
[]![The Create API client window with fields, listed scopes, and Read and Write checkboxes.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-createclient.png)
[]![CrowdStrike Webhook description and a Configure button at the end.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-configurewhook.png)
[]![The API client's ID and secret are displayed](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-apiclientcreated.png)
[]![View the user profile details](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-userprofile.png)
[]![The Configure CrowdStrike Webhook page displaying different fields and buttons to Cancel or Save configuration.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-webhookdetails.png)
[]![Trigger and three sequential options under it with annotation around Action icon.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-clickactionicon.png)
[]![Trigger and a down arrow under it displaying three sequential options.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-arrowaction.png)
[]![The Add action page with fields Webhook name and Data format and buttons Cancel and Next.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-addactionpage.png)
[]![Trigger with the Call webhook action listed under it and annotation around Finish button.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-action-finishbutton.png)
[]![Add workflow name and description page with Name, Display, and Workflow status fields and options to cancel or save workflow.](/downloads/unified/policies/adaptive-access-engine/integrating-crowdstrike-adaptive-access-engine/aae-cs-saveworkflow.png)