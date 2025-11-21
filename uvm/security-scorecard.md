# Security Scorecard
Source: https://help.zscaler.com/uvm/security-scorecard
PDF: https://help.zscaler.com/pdf/com/en/1528281.pdf

![The Security Scorecard tile](/downloads/uvm/configure/sources/security-scorecard/mceclip0.png)
SecurityScorecard is an information security company that rates cybersecurity postures of companies via scored analysis of cyber threat intelligence signals for the purposes of third party management and IT risk management.
The SecurityScorecard connector retrieves information about security issues or vulnerabilities detected within an organization's systems, networks, or applications.
Required Parameters
The source Authentication configuration requires the API key parameter. To learn more, refer to the [SecurityScorecard documentation](https://support.securityscorecard.com/hc/en-us/articles/9738347291931-Create-API-tokens-for-the-SecurityScorecard-platform).
There are two options for API keys in SecurityScorecard:
- [Create a token for your user account](#user-account)
- [Create a bot (service account) user with an API token](#service-account)
In the source setup Retrieval** **section, set the following:
- Identifier: Enter your domain(s) (e.g., <yourcompanyname>.com). To add multiple domains, press Enter after each entry.
- Category (optional): Choose one of 10 categories of cyber-risk and protection that SecurityScorecard uses to assess and score an organization’s security resilience. To learn more, refer to the [SecurityScorecard documentation](https://support.securityscorecard.com/hc/en-us/articles/4410784989083-SecurityScorecard-glossary#h_01FMXBVDB8X47C9PWPK3XXY27K).
[]
To create an API key from a user account:
- In your SecurityScorecard profile menu, click **My Settings**.
- From the left-side navigation, select the **API **tab and click **Generate New API Token**.
**![mceclip1.png](/downloads/uvm/configure/sources/security-scorecard/mceclip1.png)
**
- Click **Confirm**.
- Copy the API key and save it in a secure location. You are not able to see your token once you leave the page.
[]
To create an API key from a service account:
- In an administrator SecurityScorecard account’s profile menu, click **My Settings**.
![mceclip2.png](/downloads/uvm/configure/sources/security-scorecard/mceclip2.png)
- From the left-side navigation, in the **Admin Settings** section, select **People Management**.
- Click **Invite People**.
- Make the new user a bot so that it does not expire.
- Select the **Uncheck to create a human user** checkbox.
- Enter a name for** **the bot you created.
- In the **Base Role** section, select **Read Only**.
- Click **Add User**.
- In the user list, in the **API Access** section, click** Create API token**.
**![mceclip3.png](/downloads/uvm/configure/sources/security-scorecard/mceclip3.png)
**
- Click **Confirm**.
- Copy the API key and save it in a secure location.