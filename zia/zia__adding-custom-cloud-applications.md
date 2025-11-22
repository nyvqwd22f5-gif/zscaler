# Adding a Custom Cloud Application
Source: https://help.zscaler.com/zia/adding-custom-cloud-applications
PDF: https://help.zscaler.com/pdf/com/en/1442796.pdf

Adding custom cloud applications provides greater flexibility when creating rules to control access to custom applications. This feature consists of two parts:
- Adding an application if it's not already present in Zscaler for discovery and usage metrics (e.g., number of users, bytes uploaded or downloaded, etc.).
- Associating the application with the [Custom Applications for Cloud App Control](/zia/adding-custom-applications-rule-cloud-app-control) rule.
- Risk attributes for custom cloud applications are not captured.
- The SSL inspection must be enabled for the custom cloud application lookup.
- If Zscaler creates a predefined cloud application with the URL used in a custom cloud application, then the predefined cloud application takes precedence over the custom application. Hence, the rules created with the custom cloud application are ineffective. Zscaler regularly notifies customers about this categorization change via trust posts and potential impact.
To add a custom cloud application:
- Go to **Administration** > **Cloud Applications**.
-
Click **Add Custom Cloud Application**.
The **Add Custom Cloud Application **window appears.
- In the **Add Custom Cloud Application **window:
- **Cloud Application Name**: Enter the name of the custom cloud application. This is displayed when configuring the Custom Applications for Cloud App Control rules.
- **Application Category**: The field displays **Custom**. This field is not editable.
- **Application Status**: Select the application status. You can select either **Sanctioned** or **Unsanctioned**. To learn more, see [About Cloud Application Status](/zia/about-cloud-application-status).
- **Risk Index**: Select the risk index number (1–5, 1 being the lowest risk and 5 being the highest) for the application.
- **Tags**: Select the tags associated with the application. To learn more, see [About Cloud Application Tags](/zia/about-cloud-application-tags).
- **URLs**: Enter the URLs or IP addresses you want to add to this custom cloud application and click **Add Items**.
- **Description**: (Optional) Enter any additional comments or information. The description cannot exceed 10,240 characters.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).