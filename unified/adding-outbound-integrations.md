# Adding Outbound Integrations
Source: https://help.zscaler.com/zia/adding-outbound-integrations
PDF: https://help.zscaler.com/pdf/com/en/1450366.pdf

While your inbound integrations provide you with visibility and governance for the apps installed in your environment, outbound integrations allow you to receive messages and notifications from outside of the Zscaler 3rd-Party App Governance product.
Adding Slack Outbound Integration
To add Slack outbound integration:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect-Button)
The **Integrations** window appears.
- In the **Integrations** window, choose the **Outbound** tab.
- To configure Slack, click **Connect**.
[See image.](#Outbound-Tab)
A consent window appears.
- Click **Allow** in the consent window.
A list of your public Slack channels is populated.
- Select the channel you want for the alerts.
Integrating with a Private Channel
If the channel you wish to select is a private channel, you must add 3rd-Party App Governance to the channel.
To add 3rd-Party App Governance to your private channel:
- In Slack, click the name of the channel to open up the menu.
[See image.](#Slack-Channel)
- On the menu, go to the **Integrations** tab.
[See image.](#Integrations-Tab)
- Click **Add an App**.
[See image.](#Add-App)
- Look up 3rd-Party App Governance, and click **Add**.
Your channel is now visible for outbound integrations.
Adding Email Outbound Integration
To add email outbound integration:
- Click the **Connect** icon in the left-side navigation.
The **Integrations** window appears.
- In the **Integrations** window, choose the **Outbound** tab.
- Under **Policy Email**,** **enter one or more email addresses to be used to notify the users when a policy is triggered.
- Under** Revocation Email**, enter an email address to be used to notify the users when a previously accessible app is revoked or banned. To learn more, see[ Revoking and Banning Apps](/zia/revoking-banning-apps).
- Enter the access token, and click **Connect**. To create an access token, refer to the [SendGrid documentation](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/api-keys).
[See image.](#Revocation-Email)
![Connect Icon allows you to add new intgerations](/downloads/zia/apptotal/getting-started/connecting-your-platforms/outbound-integrations/Connect_Button.png?1688498609)
[]
![Screenshot of Outbound Tab](/downloads/zia/apptotal/getting-started/connecting-your-platforms/outbound-integrations/To%20configure%20Slack%2C%20click%20on%20%E2%80%9CConnect%E2%80%9D.png)
[]
![Screenshot of Slack Channel](/downloads/zia/apptotal/getting-started/connecting-your-platforms/outbound-integrations/To%20add%20Canonic%20App%20to%20your%20private%20channel%20click%20on%20the%20name%20of%20the%20channel%20to%20open%20up%20the%20menu..png)
[]
![Screenshot of Integrations Tab](/downloads/zia/apptotal/getting-started/connecting-your-platforms/outbound-integrations/Integrations_tab.png)
[]
![Screenshot of Add App Option](/downloads/zia/apptotal/getting-started/connecting-your-platforms/outbound-integrations/Add_App.png?1688499998)
[]
[]![Outbound Integration Tab showing Revocation and Policy Emails](/downloads/tech-pubs-drafts/zia-draft-articles/Outbound_RevokeEmail.png)