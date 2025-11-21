# Configuring Privileged Approvals
Source: https://help.zscaler.com/zpa/configuring-privileged-approvals
PDF: https://help.zscaler.com/pdf/com/en/1485231.pdf

After you have created a [privileged portal ](/zpa/about-privileged-portals)and a [privileged console](/zpa/about-privileged-consoles), you can go to the [Privileged Approvals](/zpa/about-privileged-approvals) page to create a privileged approval. For a complete list of ranges and limits, see [Ranges & Limitations](/zpa/ranges-limitations).
Prior to creating a privileged approval, it is recommended that you go to the [Access Policy](/zpa/about-access-policy) page and create an access policy with the rule action **Conditional Access **selected and the **Allow for Privileged Approval **checkbox selected.** ** If you create a privileged approval before setting an access policy, the privileged approval and its related application segments cannot take effect until the access policy is created with the related application segments.
To add a privileged approval:
- Go to **Resource Management **> **Privileged Remote Access **> **Privileged Approvals**.
- Click** Add Approval**.
The **Add Approval** window appears.
- In the** Add Approval** window, configure the following privileged console information as needed:
- [General Information](#GeneralInfo)
- [Time Bound Access](#TimeBound)
[See image.](#AppWind)
- Click **Save**.
If you are a third-party user or contractor using a [Microtenant](/zpa/about-microtenants) with Privileged Approvals disabled, you cannot add a privileged approval.
User Validations
When Emergency Access isn't configured, ZPA doesn't validate that users exist before a privileged approval is created. You need to manage those users within your IdP.
When [Emergency Access](/zpa/configuring-emergency-access) is configured, ZPA only validates users that are from arbitrary authentication domains. If the user does not exist in the IdP enabled for emergency access, ZPA offers to create the user when creating the privileged approval, and you can manage the user on the [Emergency Access Users](/zpa/about-emergency-access-users) page.
If Emergency Access is enabled, a window appears to designate the new user as an emergency access user.
[See image.](#EAprompt)
The **Add Emergency Access User** window only appears if:
- The email address entered doesn't match the authentication domain of the primary or secondary domain.
- Emergency access is already configured.
- The specified email domain is added to the **Emergency Authentication Domains** field.
- The user doesn't exist in the IdP enabled for emergency access.
To add an Emergency Access user:
- In the **Add Emergency Access User** window, click **OK** and fill out the following fields:
- **Email Address**: The email address of the privileged approval user.
- **First Name**: The first name of the privileged approval user.
- **Last Name**: The last name of the privileged approval user.
- Click **OK**, and the user is added to the [Emergency Access Users](/zpa/about-emergency-access-users) page.
[See image.](#EAwindow)
- []**User Email**: Enter the user's email address that you are assigning the privileged approval to.
The user email should match the tenant's identity provider (IdP), specifically the NameID attribute in the SAML Assertion.
[See image.](#GenInf)
- **Application Segments**: Select the application segments you want to include in the privileged approval. You can search for a specific application segment, click **Select All** to apply the application segments visibly listed, or click **Clear Selection** to remove all selections. There is no limit to the number you can select. Click **Done** after you have made your selections. Click the **Delete** icon in a selected application segment to remove it from your list.
[See image.](#AddAS)
- []**Time Window**:
- Select the start date by clicking a day on the calendar under **Start Date**. You can use the arrows next to the month and year of the calendar to select a different month.
- Enter a start time above the calendar under **Start Date**.
- Select the end date by clicking a day on the calendar under **End Date**. You can use the arrows next to the month and year of the calendar to select a different month.
- Enter an end time above the calendar under** End Date**.
[See image.](#TBaccess)
- (Optional) Select **Enable Working Hours** to specify what hours and days of the week the time window is going to be active. The default is 9:00 start time and 17:00 end time for a 24-hour window.
[See image.](#EnabWH)
[]![General Information section in the Add Approval window within the ZPA Admin Portal](/downloads/zpa/privileged-remote-access-management/configuring-privileged-approvals-draft/GenInfo.png)
[]![Select application segments in the Add Approval window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/ranges-limitations-draft/selectappseg.png)
[]![Setting the date and time parameters for a privileged approval in the Time Bound Access window](/downloads/zpa/privileged-remote-access-management/configuring-privileged-approvals/Updated%20Time%20Bound%20Access.png)
[]![Set the working day and time parameters when you select Enable Working Hours](/downloads/zpa/privileged-remote-access-management/configuring-privileged-approvals/Updated%20Working%20Hours.png)
[]![Configuring a privileged approval in the Add Approval window](/downloads/zpa/privileged-remote-access-management/configuring-privileged-approvals/Updated%20Add%20Approval%20window.png)
[]![Add Emergency Access User prompt window](/downloads/tech-pubs-drafts/zpa-draft-articles/doc-46676-configuring-privileged-approvals-draft/EA%20pop%20up%20window.png)
[]![Adding user information in the Add Emergency Access User window](/downloads/zpa/privileged-remote-access-management/configuring-privileged-approvals/UPDATED%20Add%20EA%20user.png)