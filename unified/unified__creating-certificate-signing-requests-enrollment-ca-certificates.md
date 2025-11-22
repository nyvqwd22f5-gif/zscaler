# Creating Certificate Signing Requests for Enrollment (CA) Certificates
Source: https://help.zscaler.com/unified/creating-certificate-signing-requests-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1496926.pdf

A CA certificate is required for enrollingZscaler Client Connector [configuring an App Connector](/zpa/about-connectorprovisioningwizard#sc) for enrollment, and [configuring an AppProtection-enabled application segment](/zpa/configuring-application-segments) for enrollment.
Zscaler recommends creating a CA certificate for Zscaler Client Connector and another certificate for App Connectors. If you have AppProtection enabled, you need to create an additional CA certificate.
To create a CSR for an enrollment (CA) certificate:
- Go to the **Enrollment Certificates** page (Infrastructure > Private Access > Component > Enrollment Certificates).
- Click **Create CSR**.
The **Create CSR** window appears.
- In the **Create CSR** window:
- **Name**: Enter a name for the CSR. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
![Enrollment Certificates page with Create CSR window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/certificates/about-creatingEnrollmentCsr/zpa-createenrollmentcertcsr.png)
- Click **Create** to generate content for the CSR.
- Sign the CSR using your organization’s signing CA, which can be a root or intermediate CA. This will result in the CSR becoming a signed certificate.
The **Enrollment Certificates** page automatically updates to display your pending CSR in the table, where you must [upload the signed certificate and the certificate chain](/unified/uploading-enrollment-ca-certificates).