# Configuring Sandbox Integrations
Source: https://help.zscaler.com/unified/configuring-sandbox-integrations
PDF: https://help.zscaler.com/pdf/com/en/1494861.pdf

Files can be transferred securely through the Private Applications cloud via a designated privileged console from a Privileged Remote Access (PRA) portal. These files can then be downloaded or uploaded with the option to inspect the files using Internet & SaaS Sandbox File Transfer.
Configuring the integrations for the Internet & SaaS Sandbox File Transfer provides the following benefits and enables you to:
- Inspect files you are uploading in a privileged console for malware or malicious content.
- Safeguard the privileged console by inspecting larger files.
To enable the Inspect option for the File Transfer feature for privileged consoles, you first need to set up the parameters for the Internet & SaaS Sandbox integration. If you do not set up the integration configurations, then the Inspect option is automatically disabled.
After you have configured the Internet & SaaS Sandbox integration, set up the privileged capabilities policy for the privileged consoles.
The Integrations page is read-only for Private App [Microtenant](/unified/about-microtenants) admins.
Configuring Integration Settings
To configure Integration settings:
- Complete the following fields:
- **ZIA Cloud**: Enter the name of the Internet & SaaS Cloud with the Sandbox you are accessing.
- **Cloud Service API Key**: Enter the API key for the Internet & SaaS Cloud.
- **ZIA Admin Username**: Enter the username for that specific Internet & SaaS Admin account.
- **ZIA Admin Password**: Enter the password for that specific Internet & SaaS Admin account.
- **ZIA Sandbox API Token**: Enter the API key for the Internet & SaaS Sandbox.
If you don’t include the username, password, or token, you cannot continue. All fields must be completed before you can move forward.
- Click **Save**.
![Using the Integrations page within the Admin Portal](/downloads/unified/policies/private-applications/access-control/clientless/about-integrations/integrations-ui.png)