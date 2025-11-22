# Editing Enrollment (CA) Certificates
Source: https://help.zscaler.com/unified/editing-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1496936.pdf

[]To edit an enrollment (CA) certificate:
- Go to the **Enrollment Certificates **page (Infrastructure > Private Access > Component > Enrollment Certificates)
-
In the table, locate the certificate you want to modify and click the **Edit icon**.
Enrollment certificates that are managed by Zscaler are read only and cannot be edited.
The **Edit Certificate** window appears.
- In the **Edit Certificate** window, modify fields as necessary. You can see more details about the certificate, including the certificate’s expiration date and whether it is being used as the signing certificate for App Connectors, AppProtection, or Zscaler Client Connector.
To replace an expired certificate, you must upload a new one. To learn more, see [About Enrollment (CA) Certificates](/unified/about-Enrollment-ca-Certificates).
If you select the Client Certificate Type **AppProtection CA** and there is an existing AppProtection CA certificate, when you click **Save** this CA certificate replaces the previous AppProtection CA certificate.
[See image.](#img-editcert)
- Click **Save**.
[]![Edit Certificate window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/editing-enrollment-ca-certificates/Edit%20Certificate%20window.png)