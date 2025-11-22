# Adding an HTTP Header Profile
Source: https://help.zscaler.com/zia/adding-http-header-profile
PDF: https://help.zscaler.com/pdf/com/en/1517126.pdf

The [HTTP header profile](/zia/about-http-header-profile) allows you to create criteria for various HTTP request headers and create policies based on the HTTP headers.
The HTTP header profiles consist of the following logical operations between the criteria:
Origin (`AND`) Referer (`AND`) User Agent
If multiple HTTP header criteria are added to a profile, then the logical operator `OR` is added between the same header types and the logical operator `AND` is added between different header types.
For example, if 5 HTTP header criteria (i.e., two Origins, a Referer, and two User Agents) are added to an HTTP header profile, then the logical operations between the criteria are as follows:
[Origin 1 (`OR`) Origin 2] (`AND`) Referer (`AND`) [User Agent 1 (`OR`) User Agent 2]
To add an HTTP Header profile:
- Go to **Administration** > **HTTP Header Control**.
-
On the **HTTP Header Profile** tab, click **Add HTTP Header Profile**.
The **Add HTTP Header Profile **window appears.
-
In the **Add HTTP Header Profile **window:
- **Name**: Enter the name of the HTTP header profile. This is displayed when configuring the URL Filtering policy rules.
-
**HTTP Header**: Select one of the following HTTP headers:
- [Origin](#origin)
- [Referer](#referer)
- [User Agent](#user-agent)
You can add up to 16 HTTP header criteria by clicking the **Add Header Criterion** button.
- **Description**: (Optional) Enter any additional comments or information. The description cannot exceed 10,240 characters.
[See image.](#add-http-header-profile)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]Select this header to add the cloud applications or URL categories from which the request originates. The following fields appear when you select this header:
- **Cloud Applications**: Select the cloud applications or cloud application categories that apply to the HTTP header profile.
- **URL Categories**: Select the URL categories that apply to the HTTP header profile.
[]Select this header to add the cloud applications or URL categories that refer to other applications (e.g., if the referer is Google Classroom (learning management system (LMS)), then allow www.youtube.com). The following fields appear when you select this header:
- **Cloud Applications**: Select the cloud applications or cloud application categories that apply to the HTTP header profile.
- **URL Categories**: Select the URL categories that apply to the HTTP header profile.
[]Select this header to control access to user agents. The following fields appear when you select this header:
-
**User Agent**: Choose a user agent for which you want to control access.
You can enter a custom user agent by selecting the **Other** option.
-
**Operator**: Choose an operator (i.e., **>**, **<**, **=**, or **≠**) or **Any** to create an expression between the user agents and its versions.
**Any** implies all the versions for the user agent.
- **Version**: Choose a version for the selected user agent.
[]![The Add HTTP Profile window with the header criteria in the ZIA Admin Portal](/downloads/zia/policies/http-header-control/adding-http-header-profile/ZIA-Add-HTTP-Header-Profile-Page.png)