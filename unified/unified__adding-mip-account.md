# Adding an MIP Account
Source: https://help.zscaler.com/unified/adding-mip-account
PDF: https://help.zscaler.com/pdf/com/en/1493321.pdf

Add an MIP (Microsoft Information Protection) account in the Admin Portal to enable the scan and retrieval of the MIP labels from Microsoft to the Admin Portal. After the MIP account has been successfully validated, the service can scan and retrieve the MIP labels from Microsoft for the MIP account in the Admin Portal. For the service to scan and retrieve the MIP labels from Microsoft, you need to change the status on the MIP account from *Validation Successful* to *Active* using the Edit MIP Account window. To stop the scan and retrieval of these MIP labels from Microsoft, change the status of the MIP account to *Tenant Inactive*. To learn more, see [Retrieving MIP Labels from Microsoft to the MIP Account](/unified/retrieving-mip-labels-microsoft-mip-account).
To add an MIP account:
- Go to **Policies **>** Data Protection **>** Common Resources **>** MIP Labels**.
- Click **Add MIP Account**.
The **Add MIP Account **window appears.
[See image.](#Authorize)
- In the **Add MIP Account** window, select a **SaaS Connector** option. A Zscaler-defined connector grants the Zscaler service full administrator privileges to the application; whereas, a custom connector grants only necessary permissions.
- [Zscaler Defined](#Zscaler-Defined)
- [Custom](#Custom)
The **Add MIP Account** window reappears, displaying the next window for account details.
[See image.](#AccountDetails)
- In the **Add MIP Account** window, under **Account Name**, enter a name you want to associate with the Microsoft account. It must be unique.
- Click **Save** and activate the change.
The MIP account is added to the Admin Portal. The MIP Account displays a status of **Validation Successful **if the account is authorized. It displays a status of **Validation Failed** if the account is not authorized. If the status on the MIP account is **Validation Failed**, you can try the authorization process again by clicking **Reauthorize** on the **Edit MIP Account** window.
[]
- Click **Authorize**.
The Microsoft Portal appears.
- Choose an account and log in to the Microsoft Portal.
A Microsoft window appears listing the permissions requested by the Zscaler service.
[See image.](#MicrosoftPermissionsWindow)
- Review the required permissions for the Zscaler service to access the Microsoft account and click **Accept**.
[]
To create a custom MIP connector, you must first configure permissions in Azure so that you can provide the **Client ID**, **Client Secret**, and **Tenant ID** for the MIP account in the Admin Portal. To learn more, see [Authorizing a Custom Zscaler Connector for Microsoft Applications](/unified/authorizing-custom-zscaler-connector-microsoft-applications).
[]![Authorizing the MIP account](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/ZIA-Add-MIP-Account-Window-Authorize-with-Custom.png)
[]![Required Microsoft Permissions Window](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/microsoft-permissions-window.png)
[]![Entering MIP Account details](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/ZIA-Add-MIP-Account-Window-Account-Details.png)