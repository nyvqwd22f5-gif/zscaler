# About the Application Information
Source: https://help.zscaler.com/unified/about-application-information
PDF: https://help.zscaler.com/pdf/com/en/1497516.pdf

The Application Information page shows you information on the specific application you selected to view on the [Shadow IT Report](/unified/about-shadow-it-report) page.
For the Hosting Information and Security Information sections, you can see whether the application has (Yes) or does not have (No) the characteristic. A green thumbs up next to that answer means that this is the desirable answer. A red thumbs down means that this is not the desirable answer.
Application Information provides the following benefits and enables you to:
- Gain in-depth visibility into individual Shadow IT applications after analyzing them for multiple risk attributes.
- View comprehensive details on authenticated users, unauthenticated traffic, and suggestions for similar applications.
- Analyze and secure your organization's traffic from potential threats and vulnerabilities posed by the usage of an application.
- Inspect third-party applications that are integrated with your corporate data and their permission levels.
- Identify risks and take appropriate actions like revoking application access.
- Analyze data ingested from third-party vendor devices that are connected to your organization's traffic.
About the Application Information Page
On the Application Information page (Analytics > Internet & SaaS > Analytics > SaaS Security Report > Applications > any application on the Shadow IT Report page), you can do the following:
- View the application name, the time duration for which the report is filtered, and the application's last seen date within the specified duration.
- Print a PDF version of this page or view the logs for the application; you are redirected to the [Web Insights](/unified/about-insights) page.
- View or edit the following information about the application:
- **Total Bytes**: The total bytes consumed by the application, both upload and download. However, in some cases, the total bytes might not be equivalent to the sum of upload and download bytes because the uploaded and downloaded bytes distribution data might not be available for the Web Search application. In such cases, only the total bytes metrics are considered for that application.
- **Upload Bytes**: The total upload data bytes for the application.
- **Download Bytes**: The total download data bytes for the application.
- **Total Users**: The total number of users using the application.
- **Application Status**: The application status, whether it's sanctioned or unsanctioned. You can edit the status of the application by clicking the **Edit **icon.
- **Zscaler Services Supported**: The Zscaler services that are supported for the application.
-
**Risk Index**: The risk index for the applications. You can alter and override the Zscaler-computed risk index for the application by clicking the **Edit** icon (1–5, 1 being the lowest risk and 5 being the highest). To reset to the Zscaler-computed risk index, click **Reset**. The Zscaler-computed risk index is unavailable for [custom cloud applications](/unified/adding-custom-cloud-application). However, you can edit or reset their risk index as needed.
[See image.](#override-risk-index)
- **Notes**: The notes added for the application. You can add or edit a note for the application by clicking the **Edit** icon.
- **Policies Applied**: All the policies that are configured specifically for the application in the Admin Portal. The field stays blank if you haven't configured any policies for the application.
- **Tags**: The [tags assigned to the application](/unified/adding-cloud-application-tag). You can add or remove tags for the application by clicking the **Edit** icon.
- View basic, hosting, and security information about the application.
- [Risk Attributes](#risk-attributes)
-
View third-party integration information about the application.
- [3rd-Party Integrations](#3rd-party-integration)
The Risk Attributes and 3rd-Party Integrations information is unavailable for [custom cloud applications](/unified/adding-custom-cloud-application).
- View user and location information about the application.
- [Usage](#usage)
- View** **a list of applications that fall under the same application category. The applications are shown in descending order of usage. Each application widget shows the number of users, upload and download bytes, risk index, and the status of the application. Click **View** to open the Application Information page for that application.
[]On the Risk Attributes tab, you can view:
- **Basic Information**: You can see the following basic information about the application:
- **Headquarters**: The application company's headquarters.
- **Employees**: The number of employees in the application company.
- **Year Incorporated**: The year when the application company was incorporated.
- **Activities Supported**: The activities supported by the application.
- **Application Category**: The application category that the application is categorized under.
- **Integrations**: The number of integrations associated with the application across your corporate SaaS platforms. For example, if your organization uses Amazon and the application shows at least one integration in this field, then Amazon has potential access to your corporate SaaS platforms, such as Google Workspace. Data in this field is populated by [Zscaler 3rd-Party App Governance](/unified/what-3rd-party-app-governance).
- **Description**: The description of the application company.
- **Hosting Information**: You can see whether the application has (**Yes**) or does not have (**No**) the following characteristics. A green thumbs up next to that answer means that this is the desirable answer. A red thumbs down means that this is not the desirable answer:
- [Hosting Characteristics](#hosting-char)
- **Security Information**: You can see whether the application has (**Yes**) or does not have (**No**) the following characteristics. A green thumbs up next to that answer means that this is the desirable answer. A red thumbs down means that this is not the desirable answer:
- [Security Characteristics](#security-char)
[See image.](#img-risk-attributes-tab)
[]On the 3rd-Party Integrations tab, you can view the following data populated by [3rd-Party App Governance](/unified/what-3rd-party-app-governance). The application must have at least one integration (Risk Attributes > Basic Information) for data to be populated.
- **Integration Platform**: The platform (e.g., Google Workspace) associated with the integrations.
- **Integration Name**: The name of the integration (e.g., Amazon Alexa) associated with the application. Multiple integrations can have the same name even though their configuration and security posture are unique.
- **Risks & Findings**: The number of risks and findings associated with the integration.
- **Permission Level**: The permission level (Low, Medium, High) associated with the integration.
- **Integration Risk Level**: The risk level (Low, Medium, High) associated with the integration.
Click the integration to view the following additional **Security Information**:
- **Marketplace**: Indicates if the application is from a marketplace (e.g., Chrome Web Store).
- **Yes** = thumbs up
- **No **= thumbs down
- **Risks & Findings**: The risks and findings (e.g., Unique Permission, Non-Marketplace App, etc.) associated with the integration.
- **Permission Level**: The permission level (Low, Medium, High) associated with the integration.
- **Access Types**: The types of access (e.g., Sign in) associated with the integration.
- **Integration Risk Level**: The risk level (Low, Medium, High) associated with the integration.
- **Platform Verified**:** **Indicates if the application is verified by the platform (e.g., Google).
- **Yes** = thumbs up
- **No **= thumbs down
- **Permissions**: The permissions (e.g., access to your contacts) associated with the integration.
- **View More**: To view more information in the 3rd-Party App Governance Admin Portal, you must be an Internet & SaaS super admin and your organization must be subscribed to 3rd-Party App Governance. If your organization is not subscribed, you instead see links to upgrade your license.
[See image.](#img-3rd-party-integrations-tab)
[]On the **Usage** tab, you can view:
- **Users Table**: You can view user-specific data for the application in this table. In this table, you can:
- View a list of all the users. For each user, you can view:
- **User Name**: The name of the user who accessed the application.
- **Download Bytes**: The total bytes downloaded by the user.
- **Upload Bytes**: The total bytes uploaded by the user.
- **Total Bytes**: The sum of upload and download bytes.
- **Department**: The department that the user belongs to.
- **No. of Transactions**: The total number of transactions made by the user for the selected duration.
- **Last Accessed**: The date when the user accessed the application last time.
- Download the table data as a CSV file.
- Use the filter option to update the table with your selections:
- Download Bytes
- Upload Bytes
- Total Bytes
- Users
- Department
- Click on a user name to view the logs specific to that user; you are redirected to the Web Insights Logs page.
- Modify the table and its columns.
The table shows data for up to 1,000 entries. You can click **Download CSV** file to view the data for all the entries.
- **Location Table**: View the unauthenticated location-specific data for the application in this table. In this table, you can:
- View a list of all the unauthenticated locations. For each location, you can view:
- **Name**: The name of the user who accessed the application.
- **Download Bytes**: The total bytes downloaded by the user.
- **Upload Bytes**: The total bytes uploaded by the user.
- **Total Bytes**: The sum of upload and download bytes.
- **Department**: The name of the department. For multiple departments in a location, additional entries are shown in the table with similar locations but different departments.
- **No. of Transactions**: The total number of transactions made by the user for the selected duration.
- **Last Accessed**: The date when the user accessed the application last time.
- Download the table data as a CSV file.
- Use the filter option to update the table with your selections:
- Download Bytes
- Upload Bytes
- Total Bytes
- Location
- Department
- Click on a location to view the logs specific to that location; you are redirected to the Web Insights Logs page.
- Modify the table and its columns.
The table shows data for up to 1,000 entries. You can click **Download CSV** file to view the data for all the entries.
The Location Table is only visible for reports generated by the Zscaler service.
[See image.](#img-usage-tab)
- []SSL Pinned
- **Yes** = thumbs down
- **No **= thumbs up
- Data Encryption in Transit
- **Yes** = thumbs up
- **No **= thumbs down
- Evasive
- **Yes** = thumbs down
- **No **= thumbs up
- HTTP Security Header Support
- **Yes** = thumbs up
- **No **= thumbs down
- DNS CAA Policy
- **Yes** = thumbs up
- **No **= thumbs down
- Weak Cipher Support
- **Yes** = thumbs down
- **No **= thumbs up
- Valid SSL Certificate
- **Yes** = thumbs up
- **No **= thumbs down
- Public CVE Vulnerability
- **Yes** = thumbs down
- **No **= thumbs up
- SSL Cert Key Size
- Below** 2048 Bits** = thumbs down
- **2048 Bits **& above = thumbs up
- Vulnerable to Heartbleed
- **Yes** = thumbs down
- **No **= thumbs up
- Vulnerable to Poodle
- **Yes** = thumbs down
- **No **= thumbs up
- Vulnerable to Logjam
- **Yes** = thumbs down
- **No **= thumbs up
- Support for WAF
- **Yes** = thumbs up
- **No **= thumbs down
- Remote Access Screen Sharing
- **Yes** = thumbs down
- **No **= thumbs up
- Vulnerability Disclosure Policy
- **Yes** = thumbs up
- **No **= thumbs down
- Sender Policy Framework
- **Yes** = thumbs up
- **No **= thumbs down
- DomainKeys Identified Mail
- **Yes** = thumbs up
- **No **= thumbs down
- Domain-Based Message Authentication
- **Yes** = thumbs up
- **No **= thumbs down
- Malware Scanning Content
- **Yes** = thumbs up
- **No **= thumbs down
- []**Certifications**: If applicable, this field shows the application's certifications (e.g., HIPAA).
- **Data Residency Vendors**: If applicable, this field shows the vendors (e.g., AWS) that host the application's data. Data in this field is populated by [3rd-Party App Governance](/unified/what-3rd-party-app-governance).
- **Data Residency Countries**: If applicable, this field shows the countries (e.g., USA) in which the application's data resides. Data in this field is populated by 3rd-Party App Governance.
- **Data Retention Description**: If applicable, this field describes the application's data retention policy. Data in this field is populated by 3rd-Party App Governance.
- **Data Retention Type**: If applicable, this field shows the application's data retention type (e.g., as long as the account is active). Data in this field is populated by 3rd-Party App Governance.
- **Deletion Upon Request**: If applicable, this field indicates if the application deletes a user's data upon the user's request. Data in this field is populated by 3rd-Party App Governance.
- **Yes** = thumbs up
- **No **= thumbs down
- Poor Terms of Service
- **Yes** = thumbs down
- **No **= thumbs up
- Data Breaches in the Last 3 Years
- **Yes** = thumbs down
- **No **= thumbs up
- Source IP Restrictions
- **Yes** = thumbs up
- **No **= thumbs down
- MFA Support
- **Yes** = thumbs up
- **No **= thumbs down
- Admin Audit Logs
- **Yes** = thumbs up
- **No **= thumbs down
- Password Strength
- **Yes** = thumbs up
- **No **= thumbs down
- File Sharing
- **Yes** = thumbs down
- **No **= thumbs up
[]![Override Risk Index window in the Application Information page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/shadow-it-report/ZIA-6.2-edit-risk-index-shadow-it-report.png)
![The Application Information page that shows more information about a specific app selected in the Shadow IT Report](/downloads/zia/dashboard-analytics/reports/about-application-information/ZIA-6.2r-Application-information-page%20(1).png)
[![Screenshot of the Risk Attributes tab in the Application Information Report](/downloads/zia/dashboard-analytics/reports/about-application-information/ZIA-6.2r_risk_attributes.jpg)
][]
[![Screenshot of 3rd Party Integrations tab in the Application Information Report](/downloads/zia/dashboard-analytics/reports/about-application-information/zia-application-information-3rd-party-integrations.png)
][]
[![Screenshot of the Usage tab in the Application Information Report](/downloads/zia/dashboard-analytics/reports/about-application-information/usage_tab.png)
][]