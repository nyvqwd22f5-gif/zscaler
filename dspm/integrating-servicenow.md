# Integrating with ServiceNow
Source: https://help.zscaler.com/zpc/integrating-servicenow
PDF: https://help.zscaler.com/pdf/com/en/1402931.pdf

ZPC leverages ServiceNow APIs to automatically create tickets when a misconfiguration is detected. You can integrate ZPC with ServiceNow to create incidents on ServiceNow whenever a security policy violation occurs on the selected cloud accounts.
Ensure that your ServiceNow instance is online.
Integrating with ServiceNow
To integrate ZPC with ServiceNow:
- Go to** Administration** > **Integrations**.
-
Under **ITSM Integrations**, click **Add**.
[See image.](#zpc-addbutton)
-
Under **Integration Information**:
- For **Integration Name**, enter a unique name for the integration.
- For **IT Service**, select **ServiceNow**.
[See image.](#zpc-select)
- Click **Next**.
-
Under **ITSM Details**:
- For **ServiceNow Hostname**, enter the ServiceNow hostname.
- For **ServiceNow Username**, enter the username for ServiceNow.
- For **ServiceNow Password**, enter the password for ServiceNow.
[See image.](#zpc-details)
- Click **Test Connection** to validate the ServiceNow connection. A confirmation message appears if the connection is successful. If not, then check the previous steps and try again. To learn more, see the [ServiceNow Guide](https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0516495).
- If you need to reset the validation, click **Reset Validation**, if not, click **Next**.
-
Review the integration details on the **Summary** page. Click the **Edit** icon if you want to make any changes.
[See image.](#zpc-summary)
- Click **Finish**.
The integration is added and the details are displayed on the **Integrations** page.
[]![Select ServiceNow](/downloads/zpc/third-party-integrations/itsm-tools/integrating-servicenow/zpc-add-itsm-integr.png)
[]![View the ITSM Integrations page](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-servicenow/zpc-itsm-page1.png)
[]![Add the ITSM details](/downloads/zpc/third-party-integrations/itsm-integrations/adding-itsm-integrations/zpc-add-itsm-details.png)
[]![View the summary of the ServiceNow integration](/downloads/zpc/third-party-integrations/itsm-integrations/integrating-servicenow/zpc-itsm-summary.png)