# Adding a Custom Application
Source: https://help.zscaler.com/unified/adding-custom-application
PDF: https://help.zscaler.com/pdf/com/en/1492821.pdf

To add a custom application:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration **> **Applications**.
- At the bottom of the page, click **Add Custom Application**.
[See image.](#AddNewCustomApp)
The **Add Custom Application** window appears.
The **Add Custom Application** link is disabled when you’ve reached the maximum number of allowed applications or probes for your subscription level.
- In the **Add Custom Application** window:
- **Name**: Enter a name for the custom application. The maximum length is 64 characters. Accepted characters are alphanumerics and a limited range of symbols: underscore (_), hyphen (-), space ( ), forward slash (/), backward slash (\), period (.), at symbol (@), pipe symbol (|), and parentheses ().
- **Status**: The application status is **Disable** by default. You can enable most custom applications by adding at least one Web probe.
- **Type**: Select either **Custom **or **Network**. Network applications do not require a Web probe, and require only one Cloud Path probe. To learn more, see [Monitoring Applications](/unified/monitoring-applications-overview).
[See image.](#AddAppWindow)
- Click **Save** and activate your changes.
After you save the application, you can [configure probes](/unified/configuring-probe) for it, then [edit the status](/unified/editing-application).
[]![Link to Add Custom Application](/downloads/unified/policies/digital-experience-monitoring/configuration/applications/adding-custom-application/zdx-cp-scoring-add-custom-app.png)
[]![Dialog window to add a custom application](/downloads/zdx/configuration/applications/adding-custom-application/zdx-cp-scoring-add-custom-app-modal.png)