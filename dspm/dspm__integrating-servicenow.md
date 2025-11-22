# Integrating with ServiceNow
Source: https://help.zscaler.com/dspm/integrating-servicenow
PDF: https://help.zscaler.com/pdf/com/en/1487556.pdf

DSPM leverages ServiceNow APIs to automatically create tickets when senstivie data or a misconfiguration is detected in the cloud resources. You can integrate DSPM with ServiceNow to create incidents on ServiceNow whenever a security policy violation occurs on the selected cloud resources.
Ensure that your ServiceNow instance is online.
Integrating with ServiceNow
To integrate DSPM with ServiceNow:
- Go to** Administration** > **Integrations**.
-
Under **ITSM Integrations**, click **Add**.
[See image.](#ds-sn-addbutton)
-
Under **Integration Information**:
- For **Integration Name**, enter a unique name for the integration.
- For **IT Service**, select **ServiceNow**.
[See image.](#ds-sn-select)
- Click **Next**.
-
Under **ITSM Details**:
- For **ServiceNow Hostname**, enter the ServiceNow hostname.
- For **ServiceNow Username**, enter the username for ServiceNow.
- For **ServiceNow Password**, enter the password for ServiceNow.
[See image.](#ds-sn-details)
- Click **Test Connection** to validate the ServiceNow connection. A confirmation message appears if the connection is successful. If not, then check the previous steps and try again. To learn more, refer to the [ServiceNow Guide](https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0516495).
- If you need to reset the validation, click **Reset Validation**, if not, click **Next**.
-
Review the integration details on the **Summary** page. Click the **Edit** icon if you want to make any changes.
[See image.](#ds-sn-review)
- Click **Finish**.
The integration details are displayed on the **Integrations** page.
[]![Add a ServiceNow integration](/downloads/zpc/third-party-integrations/itsm-tools/integrating-servicenow/ds-itsm-addbutton.png)
[]![Select ServiceNow](/downloads/zpc/third-party-integrations/itsm-tools/integrating-servicenow/ds-servicenow-select.png)
[]![Add the ServiceNow details](/downloads/zpc/third-party-integrations/itsm-tools/integrating-servicenow/ds-servicenow-details.png)
[]![ds-servicenow-summary.png](/downloads/dspm/third-party-integrations/itsm-tools/integrating-servicenow/ds-servicenow-summary.png)