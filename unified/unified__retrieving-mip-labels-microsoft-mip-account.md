# Retrieving MIP Labels from Microsoft to the MIP Account
Source: https://help.zscaler.com/unified/retrieving-mip-labels-microsoft-mip-account
PDF: https://help.zscaler.com/pdf/com/en/1493326.pdf

After you create a MIP account in the Admin Portal and it is validated successfully, you need to change the Label Retrieval field for the MIP account in the Admin Portal to *Activate* for the service to scan and retrieve the published MIP labels from Microsoft. The MIP labels need to be published in Microsoft before the service can retrieve them. The first scan and retrieval of the MIP labels takes a few minutes. After that, the scan and retrieval of the MIP labels occurs automatically every 12 hours. To learn more about creating and publishing MIP labels in Microsoft, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/microsoft-365/compliance/create-sensitivity-labels?view=o365-worldwide).
After the MIP labels are added to the Admin Portal, you can use them with the [inline web Data Loss Prevention (DLP) policies](/unified/about-data-loss-prevention).
To retrieve MIP labels from Microsoft to the MIP account:
- Go to **Policies** > **Data Protection** > **Common Resources** > **MIP Labels**.
- Locate the MIP account for which you want to retrieve the MIP labels from Microsoft.
- Click **Edit** next to the MIP account.
The **Edit MIP Account** window appears.
- In the **Edit MIP Account** window, click **Next**.
- Change **Label Retrieval** to **Activate*** *if this is the first time retrieving the MIP labels from Microsoft. If you have previously disabled the retrieval of the MIP tags, change the field from **Disable** to **Activate** if you want to resume the scanning and retrieval of the MIP labels.
- Click **Save** and activate the change.
The scan and retrieval of the MIP labels from Microsoft is initiated. The retrieved MIP labels are added to the MIP account.
The MIP labels that are associated with the different MIP accounts are displayed when configuring an inline web DLP policy.
Disabling the **Label Retrieval** field for the MIP account stops the scan and retrieval of the MIP labels from Microsoft.