# Configuring the Data at Rest Scanning Exceptions
Source: https://help.zscaler.com/unified/configuring-data-rest-scanning-exceptions
PDF: https://help.zscaler.com/pdf/com/en/1493606.pdf

Optionally, you can create Data at Rest Scanning exceptions for file sharing applications.
Configuring a scanning exception allows you to exempt specific folders or users from the [Data at Rest Scanning policy](/unified/understanding-data-rest-scanning-policy), which consists of the [Data Loss Prevention (DLP)](/unified/about-data-rest-scanning-dlp) and [Malware Detection](/unified/about-data-rest-scanning-malware-detection) policies. When you configure a scanning exception for a folder, the Zscaler service completely ignores the files within the folder, i.e., its files aren’t evaluated with the Data at Rest Scanning policy. Likewise, the Zscaler service ignores an exempted user and the user isn’t evaluated with the policy.
To configure a scanning exception:
- Go to **Policies **>** Common Configuration **>** Out-of-Band CASB **>** Scanning Exceptions**.
- Under **Do Not Inspect Content From Any of the Following Locations**:
- To add an exception for a folder:
- Click **Add Exception**. A row with the **Tenant**, **Owner**, and **Folder** fields appears.
- In the row:
- **Tenant**: From the drop-down menu, choose the [SaaS application tenant](/unified/about-saas-application-tenants) that the folder belongs to.
- **Owner**: From the drop-down menu, choose the [user](/unified/about-users) who owns the folder.
- **Folder**: Enter the full path for the folder you want to exempt from inspection.
- To add an exception for a user:
- Click **Add Exception**. A row with the **Tenant**, **Owner**, and **Folder** fields appears.
- From the **Owner** drop-down menu, choose the [user](/unified/about-users) you want to exempt from inspection.
-
Click **Add Exceptions** to exempt more folders or users from inspection. You can add up to 64 exceptions for folders and users. To remove an exception, click the **Remove** icon for the row.
[See image.](#scanning-exceptions-image)
- Click **Save** and activate the change.
[]![The Data at Rest Scanning Exceptions page allows you to remove exceptions while scanning a rule.](/downloads/unified/policies/internet-saas/saas-security-posture-management/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scanning-exceptions/SaaS-Security-API-Scanning-Exceptions.png)