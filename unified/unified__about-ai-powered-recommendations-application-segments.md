# About AI-Powered Recommendations for Application Segments
Source: https://help.zscaler.com/unified/about-ai-powered-recommendations-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1520246.pdf

The service analyzes user logs and suggests AI-powered recommendations for application segments. AI-powered recommendations are application segments that have been pulled based on the filters you have configured in the [AI-Powered Recommendations Settings](/unified/configuring-ai-powered-recommendations-settings). These AI-powered recommendations for application segments can be [merged with existing defined application segments](/unified/merging-recommended-application-segments), [added as newly defined application segments](/unified/configuring-ai-powered-recommendations-settings), or ignored if they do not apply.
AI-powered recommendations for application segments provide the following benefits and enable you to:
- Discover and create new application segments based on application similarity or user behavior.
- Find missing applications for existing application segments and easily merge them.
- Accelerate your journey toward achieving Zero Trust for private access.
To learn more about the configuration options available for your applications before configuring an application segment, see [About Applications](/unified/about-applications) and [Configuring AI-Powered Recommendations](/unified/configuring-ai-powered-recommendations).
Prerequisites
The following prerequisites are required to activate the AI-Powered Recommendations page:
- Have a minimum of 100 [discovered applications](/unified/about-application-discovery).
- Have at least 20 [enrolled users](/unified/viewing-users-dashboard).
To activate this feature, click **Activate Recommendations** on the AI-Powered Recommendations page.
[See image](#activate-recommendations)
The AI-Powered Recommendations page is only populated with data for users who have activated it. If you want to enable this feature and the AI-Powered Recommendations page is not displayed, contact Zscaler Support.
About the AI-Powered Recommendations Page
[]On the AI-Powered Recommendations page (Policies > Access Control > Private Applications > App Segments > AI-Powered Recommendations), you can do the following:
- Open the [Settings](/unified/configuring-ai-powered-recommendations-settings) drawer to add parameters to AI-powered recommended application segment findings.
- Click **Generate Recommendations** to generate AI-powered recommendations. Hover over the button to view the **Last Generated** and **Next Availability** dates. The **Next Availability** date and the ability to generate AI-powered recommendations are determined by your subscription.
- Download a CSV file of the AI-Powered Recommendations list.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all AI-powered recommendations that were configured for your organization.
- [View elements of each application segment.](#listApplicationSegments)
- [Click any application in the Applications column to view its details.](#moreappsegmentdetails)
- [Add an AI-powered recommended application segment](/unified/configuring-ai-powered-recommendations-settings).
- [Merge with a defined application segment](/unified/merging-recommended-application-segments).
- Access the table menu to:
- [Ignore an AI-powered recommended application segment.](#Ignore)
- [View the Diagnostics page, filtered with the applications related to that specific AI-powered recommended application segment.](#Diagnostics)
- Download the configuration information for the recommended [application group](/unified/about-segment-groups) to a CSV file.
- Navigate between the pages of AI-powered recommendations.
- [Validate a client hostname.](/unified/validating-client-hostname)
- [View and add DNS search domains.](/unified/adding-dns-search-domains)
- Access pages or tabs (depending on what features you have enabled).
- [View a list of accessible pages or tabs.](#listPages)
![Using the Recommended Application Segments page ](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-ai-powered-recommendations-application-segments/zpa-ai-powered-recommendations-w-steps.png)
[]
- **Name**:** **The name of the application segment for the application.
- **Download**:** **Click **Download **to export a CSV file containing information for this specific application segment. The file lists the application segments based on the selected table filters. Larger files can take several minutes to download.
- **Attack Surface Reduction**: The percentage reduction in the attack surface (i.e., percentage difference between potential users and recommended users).
- **Current Configuration**: The number of Applications, Defined Application Segments, and Current Users.
- **Recommended Configuration**: The number of Applications, Recommended Users, and Observed Users for the AI-Powered recommendation.
-
**Recommended Users**: If [SCIM Sync](/unified/enabling-scim-identity-management) is enabled, the number of suggested users for this recommended application segment is displayed. Click the number of users to list the recommended users. You can search by email.
If SCIM Sync or SCIM Attributes for Policy are not enabled, the user recommendations appear as N/A in the recommendations.
- **Recommended Basis**: Lists the recommendation's basic information to configure.
- **Number of Transactions**:** **The total number of transactions.
- **TCP Port Ranges**:** **The TCP port ranges used to access applications.
- **UDP Port Ranges**:** **The UDP port ranges used to access applications.
- **Grouping Reasons**:** **The 5 categories that a recommended application segment can be grouped by (**IP Similarity**, **User Access Similarity**, **Domain Name Similarity**, **Co-occurring Applications Similarity**, and **Ports and Protocols Similarity**).
- **Description**: Information about the recommendation.
- **Applications**: The list of applications assigned to the selected application segment. Click **Next** or **Previous** at the bottom of the table to view additional applications. You can filter the information that appears in the table. By default, no filters are applied.
- **Application**: The name of the application.
- **Defined Application Segment**: The defined application segment merged with this application, if applicable.
- **Port and Protocol**: The web server port and protocol used by the application.
- **Server IP**: The web server IP address (e.g., 192.0.2.0).
[See image.](#img_applicationsdetails)
[]
![AI-Powered Recommendation Details](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-recommended-application-segments/ZPA-AI-Powered-Recommendations-Details.png)
[]
![Activate Recommendations button](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-ai-powered-recommendations-defined-application-segments/ZPA-Activate-AI-Powered-Recommendations.png)
[]
Each AI-powered recommended application segment contains the following elements:
- **Name**: The name of the application segment.
- **Applications**: A list of up to three recommended applications within the AI-powered recommendations for application segments.
- **Grouping Reasons**: The 5 categories that an AI-powered recommended application segment can be grouped by (**IP Similarity**, **User Access Similarity**, **Domain Name Similarity**, **Co-occurring Applications Similarity**, and **Ports and Protocols Similarity**).
- **Confidence**: The measurement of accuracy of an AI-powered recommended application segment that matches the set requirements. The range is from 0 to 100, with higher numbers meaning a more accurate match, given the configured filters configured in the AI-Powered Recommendations Settings.
- **Attack Surface Reduction**: The percentage reduction in the attack surface (i.e., percentage difference between potential users and recommended users).
By default, the list is sorted in ascending order by Attack Surface Reduction.
[]
- Go to the [Browser Access](/unified/about-browser-access) page to manage applications where Browser Access is enabled.
- Go to the [AppProtection](/unified/about-appprotection-applications) page to manage applications where AppProtection is enabled.
- Go to the [Privileged Remote Access](/unified/about-privileged-remote-access-applications) page to manage applications where Privileged Remote Access is enabled.
- Go to the [Segment Groups](/unified/about-segment-groups) page to add a new segment group or manage existing groups.
- Go to the [Defined Application Segments](/unified/about-applications) tab to view and manage defined application segments.
[]If you click the **Ignore **icon, you need to select a reason in the **Send Feedback **window. Add additional comments if needed and click **Save**. The ignored recommended application segment will no longer appear in the table. Click **Cancel** to cancel the ignore action. To view the list of ignored AI-powered recommended application segments, select the **Ignored Recommendations** filter.
[]The** Diagnostics** page shows up to 200 applications per recommended application segment. Any additional applications are not shown.