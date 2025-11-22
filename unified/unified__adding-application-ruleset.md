# Adding an Application for a Ruleset
Source: https://help.zscaler.com/unified/adding-application-ruleset
PDF: https://help.zscaler.com/pdf/com/en/1533781.pdf

You can add an application to use when adding a ruleset to manage endpoint firewall rules to use with location-based policies. To learn more, see [About Location-Based Policies](/unified/about-location-based-policies).
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
To add an application:
- Go to **Infrastructure **>** Connectors **>** Client** > **Location-Based Policies**.
-
Select the **Applications** tab and click **Add Application**.
[See image.](#applications-tab)
The **Add Application** window appears.
[See image.](#add-application-window)
- In the **Add Application** window:
- **Name**: Enter a unique alphanumeric name for your list.
-
**Path**: Enter a path for the application in one of the following formats:
- The absolute path to the application.
- The path to the application using built-in OS environment variables (e.g., `%programfiles%` or `%system32%`).
You cannot enter wildcards or directory names in the path. Paths with periods or commas must be enclosed within double quotes. You can enter a maximum of 5 paths per application, separated by commas. Each path can be a maximum of 256 characters.
- **List Description**: Enter any notes regarding the list.
- Click **Save**.
You can enter a maximum of 300 applications to use in rulesets. After you create an application, you can select it in [inbound](/unified/adding-ruleset#inbound-rule) and [outbound](/unified/adding-ruleset#outbound-rule) firewall rules when adding a ruleset. You must use the application in a ruleset, and you cannot use it for application-based bypasses directly in the app profile.
[]![Applications tab](/downloads/zscaler-client-connector/location-based-policies/adding-firewall-ip-list/zclient-connector-applications-tab.png)
[]
![Add Application window](/downloads/zscaler-client-connector/location-based-policies/adding-firewall-ip-list/zclient-connector-add-application-window.png)