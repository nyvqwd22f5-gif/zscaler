# Configuring the Acceptable Use Policy
Source: https://help.zscaler.com/unified/configuring-acceptable-use-policy
PDF: https://help.zscaler.com/pdf/com/en/1493826.pdf

You can create an Acceptable Use Policy (AUP) notification and require users to accept it before the Zscaler service allows them to browse the internet. If the AUP notification is configured, the service displays the AUP notification before users can browse the internet. [See image.](#aup)
To display the AUP notification, users should be authenticated. However, for locations or sub-locations that do not have authentication enforced, you can still enable AUP and configure the notification frequency (in days) using the corresponding settings on the Location or the Sub-Location page. To learn more, see [Configuring Locations](/unified/configuring-locations#EnableAUP) and [Configuring Sub-Locations](/unified/configuring-sub-locations#EnableAUP).
When a user accepts the AUP, the service automatically logs the acceptance with the user’s login name and location. AUP acceptance logging cannot be turned off.
[See image.](#AcceptableUsePolicyLogs)
To configure the AUP notification:
- Go to **Policies **>** Common Configuration **>** Resources **>** End User Notifications **>** Browser **>** Global Configuration**.
- Under the **Acceptable Use Policy (AUP) **section:
- **Show AUP**: Choose how often the service displays the AUP page and configure accordingly. You can choose one of the predefined intervals or customize your own using the following options:
- [Never](#never)
- [Once Per Session](#oncepersession)
- [Daily](#daily)
- [Weekly](#weekly)
- [Once Per Login](#onceperlogin)
- [Custom](#custom2)
- [Day of the Month](#dayofthemonth)
- [Day of the Week](#dayoftheweek)
The service tracks the AUP acceptance time and expiration for each user. The Zscaler service sets an [AUP cookie](/unified/about-zscaler-cookies) when a user accepts the AUP. For example, if you select **Weekly**, the service displays the AUP page one week from when the AUP cookie was set. If the AUP cookie is not present, the service displays the AUP page the next time the user logs in.
- **AUP Message (HTML)**: Enter the *Acceptable Use* statement. You can use HTML and [CSS styles](/unified/customizing-euns-css-styles) to customize the AUP notification message and its appearance. You can also add image files that are hosted on the internet.
This field appears only when the AUP notification is configured to be displayed at specific intervals using the **Show AUP** field (i.e., a value other than **Never **must be chosen).
[See image.](#configure-aup)
- Under the **IT Support** section, enter one or more of the following contact information so users can seek additional information about why access to pages, files, or web applications is restricted:
- **Email**: You can provide an email address for a contact who can explain your company's use of the Zscaler service to protect your network.
- **Phone**: You can provide a phone number for a contact who can explain your company's use of the Zscaler service to protect your network. The following examples show valid formats: 123-456-7890, +91-1234567890, 1234567890, and +911234567890.
- **Policy Link**: You can provide a URL pointing to a page you created on your company intranet that describes your current policy about using corporate network and internet resource.
[See image.](#it-support)
This information also appears on the [block](/unified/configuring-block-notifications), [caution](/unified/configuring-caution-notification), and [quarantine](/unified/configuring-quarantine-notification) notifications.
- Click **Preview Template(s) **to see what the AUP notification looks like after making changes. You can preview the notification as many times as you want. CSS style and JavaScript don't render when previewing EUN templates.
[See image.](#preview)
- Click **Save** and activate the change.
[]![Acceptable Use Policy](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-acceptable-use-policy/aup.png?1652362272)
[]The service never displays the AUP statement.
[]The service displays the AUP statement when a browser opens.
[]The service displays the AUP statement every day.
[]The service displays the AUP statement every week.
[]The service displays the AUP statement when the user logs in.
[]The service displays the AUP statement at your custom time interval.
- **Custom AUP Frequency (days)**: Enter the number of days, between 1 and 180 inclusive, that the service displays the AUP statement. For example, if you enter 30, the service displays the AUP statement every 30 days.
[]The service displays the AUP statement on a specific day of the month.
- **Select Calendar Date**: Choose the calendar date on which you want the service to display the AUP to users. For example, if you select **1**, the service displays the AUP when users log in on the 1st of every month. If a user does not log in on the specified date, the service displays the AUP the next day the user logs in.
If you choose a date that is not available for a given month (e.g., the 31st), the service does not display the AUP that month.
[]The service displays the AUP statement on a specific day of the week.
- **Select Day of the Week**: Select the day of the week on which you want the service to display the AUP to users. For example, if you select Monday, the service displays the AUP when users log in on Monday every week.
If a user does not log in on the specified day, the service displays the AUP the next day the user logs in.
[]![Acceptable Use Policy configuration](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-acceptable-use-policy/aup-configuration.png)
[]![Acceptable Use Policy preview](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-acceptable-use-policy/aup-preview.png?1652362337)
[]![IT Support fields in the Acceptable Use Policy](/downloads/zia/documentation-knowledgebase/authenticating-and-managing-users/user-aup-and-notifications/configuring-acceptable-use-policy/it-support-fields.png)
[]![A screenshot of the logs generated for Acceptable Use Policy (AUP) action taken by users](/downloads/zia/authentication-administration/end-user-notifications/configuring-acceptable-use-policy/aup-logs.png)