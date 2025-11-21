# Halo Assets
Source: https://help.zscaler.com/uvm/halo-assets
PDF: https://help.zscaler.com/pdf/com/en/1528031.pdf

![The Halo Assets tile](/downloads/uvm/configure/sources/halo-assets/c3b254ea-1a73-4647-85a1-5e0141e74561.png)
Halo ITSM helps organizations track and manage IT assets throughout their lifecycle, integrating with other IT service management processes.
Required Parameters
- [Client ID and Client Secret](#param1)
- [Tenant](#param2)
Roles and Permissions
To obtain the required parameters, you first need to create a Halo Application and assign it the appropriate permissions, as outlined in the Client ID and Client Secret section. This process requires HaloITSM administrator** **privileges.
When setting up the application, you must associate it with an agent, or user. The selected user, whether it is yours or a dedicated user created for this purpose, must have access to all Asset fields within their permissions.
You can verify this in the agent’s profile on the **Permissions** tab. Go to** Configuration** > **Teams & Agents** > **Agents**.
![Allow use of all Asset fields in the Halo console](/downloads/uvm/configure/sources/halo-assets/02d79f72-12da-480f-98f3-44ea7618ca0d.png)
[]
Ensure that you sign in to the Halo ITSM console as a HaloITSM administrator.
To generate the client ID and client Secret:
- From the left-hand navigation, go to **Configuration** > **Integrations**.
- Click **HaloITSM API**.
**![Selecting HaloITSM API in the Halo console](/downloads/uvm/configure/sources/halo-assets/730173f6-d820-4201-8e67-1c20e7fac984.png)
**
- In the **Applications** section, click **View Applications**.**![Viewing applications in the Halo console](/downloads/uvm/configure/sources/halo-assets/3be07f4b-e657-4083-9847-58eee23c8457.png)
**
- From the top right, click **New**.
![Creating a new application in the Halo console](/downloads/uvm/configure/sources/halo-assets/ed7d8184-0b33-40d2-b171-34e63f0dbc98.png)
- On the **Details** tab, configure the following:
- **Application Name**: Enter a name for the application.
- **Active**: Ensure that the checkbox is selected.
- **Authentication Method**: Select **Client ID and Secret (Services)**. This automatically generates your client ID and client Secret.
- **Login Type**: From the drop-down menu, select **Agent**.
- **Agent to log in as**: Select your admin user as the agent to which the application is associated. If you select a different user, ensure that the user you select has the relevant access, as this could affect access control.
![Entering information into the Details tab of the Halo console](/downloads/uvm/configure/sources/halo-assets/12caaa09-a206-4202-907e-55e81077ec38.png)
- Click **Save**.
- Copy the **Client ID** and **Client Secret** and store them securely.
- On the **Permissions **tab, select the **read:assets** checkbox.![Selecting the read:assets permission checkbox in the Halo console](/downloads/uvm/configure/sources/halo-assets/89f9e015-9c20-4bce-a1e1-240827bd96bc.png)
- Click **Save**.
If you save the Application before copying the client ID and client secret, you must regenerate the Client Secret and copy it. The client ID remains unchanged.
[]
Your tenant is the unique subdomain which can be found in your Halo ITSM Console URL (e.g., `https://<tenant>.haloitsm.com/home`)
For example, if your URL is `https://acme.haloitsm.com/home`, your tenant is acme.
![Your tentant in the URL of the Halo console](/downloads/uvm/configure/sources/halo-assets/486b47db-6a66-4384-87fb-283286323fe9.png)
Your tenant also be found in your HaloITSM console in **Configuration** > **Integrations** > **HaloITSM API**.
![Your tenant in the Halo console](/downloads/uvm/configure/sources/halo-assets/69d8076a-fde1-414c-a23a-e3dd3574ab67.png)