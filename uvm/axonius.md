# Axonius
Source: https://help.zscaler.com/uvm/axonius
PDF: https://help.zscaler.com/pdf/com/en/1528216.pdf

![The Axonius tile](/downloads/uvm/configure/sources/axonius/mceclip0.png)
Axonius provides visibility and control for all assets in an organization's IT estate, as well as any SaaS applications used by employees, contractors, and authorized third parties.
Required Parameters
- API Key
- API Secret
- Machine URL
- Number of days to Fetch: The number of days you want to retrieve in each run.
- Custom Fields: To learn more, refer to the [Axonius documentation](https://docs.axonius.com/docs/managing-custom-fields).
Retrieving the API Credentials
You can retrieve API credentials using a user account or a service account. A service account is used only for API purposes. To learn more, refer to the [Axonius documentation](https://docs.axonius.com/docs/manage-service-accounts).
Enable API Access
- Log in to the Axonius platform.
- On the **All Pages** page, click the cogwheel icon in the top right corner.
- On the **System Settings** page, click the **Manage Roles** tab.
- Select the relevant role. To learn more, refer to the [Axonius documentation](https://docs.axonius.com/docs/manage-roles). Ensure that it has the following permissions checked:
![mceclip1.png](/downloads/uvm/configure/sources/axonius/mceclip1.png)
Retrieving the API Key
To be able to retrieve an API key a user should have API Access enabled.
- Log in to the Axonius platform.
- Go to your account avatar > **User Settings**.
- Go to the **API Key** tab and copy your **API key** and **API secret**.
![mceclip2.png](/downloads/uvm/configure/sources/axonius/mceclip2.png)
Retrieving the Machine URL
The machine URL is part of the API request. In the SecOps platform, enter the following machine URL:
`https://``<machine URL>``/api/`
For example, in `https://10.20.0.111/api/`, `10.20.0.111` is the machine URL.