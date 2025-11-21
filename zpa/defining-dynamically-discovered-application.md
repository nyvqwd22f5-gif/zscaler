# Defining a Dynamically Discovered Application
Source: https://help.zscaler.com/zpa/defining-dynamically-discovered-application
PDF: https://help.zscaler.com/pdf/com/en/1483536.pdf

When you configure ZPA to [discover applications](/zpa/about-application-discovery), the Discovered Applications widget in the** **[Applications dashboard](/zpa/about-dashboard/appsDashboard) displays the applications that ZPA discovered for your organization. You will see all of the discovered applications listed in row order, with the most recently discovered applications listed in the first row.
If you want to define a user access policy for a specific application listed in the Discovered Applications** **widget, or want to be able to change other settings for it (e.g., enable health reporting or configure bypass settings), you can explicitly define the application within an application segment. Also, when you hover over a discovered application, you can see the date and time when the application was discovered.
![Discovered Applications widget with App Discovered On timestamp displayed within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/applications/how-do-i-define-application-after-it-dynamically-discovered/zpa-defineapp3.png)
If an application was discovered over 14 days in the past, then the [User Activity Diagnostics](/zpa/about-diagnostics/txnUsersDiagnostics) corresponding to application discovery will not be available.
When defining a new application segment, Zscaler recommends taking note of the following interaction between a wildcard domain and specific host domain, where wildcard no longer means wildcard:
- You have an app segment defined by a wildcard (*.exapp.company.com).
- You add the app segment to an access policy.
- You create a new app segment (file.exapp.company.com).
The app segment in the third bullet is not covered by the access policy. By defining the app segment (file.exapp.company.com) separately, you need to add a new access policy because the application is matched to the specific app segment. ZPA will always match an application to the most specific app segment, even if that application could potentially match a wildcard app segment. For policy, ZPA will evaluate the policy with the most specific app segment.
ZPA does not apply the ports specified in the app segments that contain IP subnets or wildcards towards app segments that contain more specific IPs or FQDNs. You will need to explicitly specify the ports in the app segment that contain the IPs or FQDNs.
To define a discovered application in the Applications dashboard:
- Go to the **Dashboard** > **Applications**.
- In the **Discovered Applications** widget, click **Add Application Segment**.
![Discovered Applications widget with Define Application Segment option within the ZPA admin portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/how-do-i-define-application-after-it-dynamically-discovered/zpa-defineapp.png)
- Select the applications you want to define, then click **Define Selected Applications**.
![Discovered Applications widget with applications selected within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/how-do-i-define-application-after-it-dynamically-discovered/zpa-defineapp2.png)
The **Add Application Segment **window appears.
- In the **Add Application Segment **window, [add an application segment](/zpa/about-application/onboard).