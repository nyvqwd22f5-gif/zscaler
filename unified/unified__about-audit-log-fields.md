# About Audit Log Fields
Source: https://help.zscaler.com/unified/about-audit-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1495991.pdf

The Log Streaming Service can send audit log information to any third-party log analytics tool. By default, the audit log type includes the fields listed in the table below for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View an example Audit Log](#examplelog)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/unified/understanding-log-stream-content-format).
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
[](/unified/about-audit-logs)
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
[](/unified/about-audit-logs)
-
-
-
-
-
-
-
-
[](/unified/configuring-company-profile)
-
-
-
-
-
-
-
-
| Field | Description | Supported Field Format Specifications |
| ----- | ----------- | ------------------------------------- |
| modifiedTime | Time when an object is created, deleted, or updated | %[OPT]s%[OPT]j%[OPT]J |
| creationTime | Time when the log was generated | %[OPT]s%[OPT]j%[OPT]J |
| modifiedBy | The user ID for the admin that made the change | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| requestID | The ID for the associated configuration change, as related to the action that was made | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| auditOldValue | The previous value that was changed if the action type is delete, sign out, or update.If the modified object is policy related, the value depends on the policy type. Then the expected values for this field are:Allow: the policy type is Access PolicyIntercept: the policy type is Bypass PolicyRe_Auth: the policy type is Timeout Policy | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| auditNewValue | The new value that was changed if the action type is create, sign in, or update.If the modified object is policy related, the value depends on the policy type. Then the expected values for this field are:Allow: the policy type is Access PolicyIntercept: the policy type is Bypass PolicyRe_Auth: the policy type is Timeout Policy | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| auditOperationType | The action performed.The expected values for this field:CreateClient Session RevokedDeleteDownloadSign InSign In FailureSign OutUpdate | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| objectType | The location within the Admin Portal where the Action was performed. This corresponds to the Resource Type in the Audit Log page. To learn more, see About Audit Logs.The expected values for this field are:AdministratorApp ConnectorApp Connector GroupApp Connector Group to App Connector AssociationApp Connector Provisioning KeyApplication SegmentApplication Segment to Server Group AssociationAuditAuthenticationAuthentication SettingBrowser AccessCertificateCertificate for Zscaler Client Connector EnrollmentClient SessionCompany LogoConstellation AssociationCORS/SameSiteCustomer Support URLDNS Search DomainEnrollment CertificateExecutive Insights DeviceExecutive Insights UserIdP CertificateIdP ConfigurationLog ReceiverLog Zone: (Indicates the log store location for a region. This is only specified during organization account creation and is never modified.)MachineMachine GroupMachine Group to Machine AssociationMachine Provisioning KeyPolicyPolicy to Connector Group AssociationPolicy to Server Group AssociationPortal LinkPosture ProfileRoleSAML AttributeSCIM AttributeSegment GroupSegment Group to Application Segment AssociationServerServer GroupServer Group to Connector Group AssociationServer Group to Server AssociationService EdgeService Edge GroupService Edge Group to Service Edge AssociationService Edge Group to Trusted Network AssociationService Edge Provisioning KeyTrusted NetworkUser PortalUser Portal to Portal Link Association | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| objectName | The name of the object. This corresponds to the Resource Name in the Audit Log page. To learn more, see About Audit Logs. | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| objectID | The ID associated with the object name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| customerID | The Private Applications tenant ID of the customer. To learn more, see Configuring the Company Profile. | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| modifiedByUser | The username of the admin associated with the audit action | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| clientAuditUpdate | Indicates whether the logs are associated with admin or client credentials. The expected values for this field are 0 and 1. | %[OPT]d |
[]{"modifiedTime": "2020-07-13T20:53:10.000Z","creationTime":"2020-07-13T20:53:10.000Z","modifiedBy":11223344556677889,"requestID":"a12aa12a-1234-aab1-123ab123456a","auditOldValue":"","auditNewValue":"{\"id\":\"98765432100123456\",\"name\":\"app1.test.com\",\"applicationId\":\"12312312312312300\",\applicationPort\":\"443\",\"applicationProtocol\":\"HTTPS\",\"certificateId\":"10203040506070809\",\"domain\":\"app1.test.com\",\"enabled\":\"true\",\"hidden\":\"false\",\"path\":\"\\/\",\"portal\":\"false\",\"trustUntrustedCert\":\"true\"}","auditOperationType":"Create","objectType":"Browser Access","objectName":app1.test.com,"objectID":98765432100123456,"customerID":12345678901234567,"modifiedByUser":"admin@test.com", "clientAuditUpdate":"0"}