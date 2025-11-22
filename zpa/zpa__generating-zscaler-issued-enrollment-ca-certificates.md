# Generating Zscaler-Issued Enrollment (CA) Certificates
Source: https://help.zscaler.com/zpa/generating-zscaler-issued-enrollment-ca-certificates
PDF: https://help.zscaler.com/pdf/com/en/1483486.pdf

A CA certificate is required for enrolling Zscaler Client Connector, enrolling [AppProtection-enabled application segments](/zpa/configuring-application-segments), and when [configuring an App Connector](/zpa/about-connectorprovisioningwizard#sc), [configuring a ZPA Private Service Edge](/zpa/configuring-service-edges), and [configuring a Private Cloud Controller](/zpa/configuring-private-cloud-controllers) for enrollment. Enrollment certificates differ from web server certificates. Web server certificates provide access to web applications. To learn more, see [About Enrollment (CA) Certificates](/zpa/about-enrollment-ca-certificates).
Zscaler recommends creating a CA certificate for Zscaler Client Connector, another certificate for App Connectors, a third for ZPA Private Service Edges, and a fourth for Private Cloud Controllers. If you have AppProtection enabled, you need to create an additional CA certificate.
To generate a Zscaler-issued enrollment (CA) certificate:
- Go to **Configuration & Control **>** Certificate Management** > **Enrollment Certificates**.
- Click **Generate Certificate**.
The **Generate Enrollment Certificate** window appears.
- In the **Generate Enrollment Certificate** window:
- **Name**: Enter a name for the certificate. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Type**: Select one of the following options:
- **Root CA**: Select this option if you want to use a root certificate authority.
- **Intermediate CA**: Select this option if you want to use an intermediate certificate authority.
For Intermediate CA, select a **Parent Certificate**, which can be a [preloaded ZPA certificate](/zpa/about-usingDefaultZPACertificates) or another Zscaler-issued certificate.
- **Client Certificate Type**: Select one of the following options:
- **None**: Select this option if you are using this enrollment (CA) certificate to enroll App Connectors, Private Service Edges, or Private Cloud Controllers.
- **Client Connector**: Select this option to use this enrollment (CA) certificate to enroll Zscaler Client Connector.
- **Isolation Client**: Select this option to use this enrollment (CA) certificate for to enroll Isolation clients.
- **AppProtection CA**: Select this option to use this enrollment (CA) certificate to enroll AppProtection-enabled application segments. If there is an existing CA certificate and you create a new AppProtection CA certificate, it replaces the previous AppProtection CA certificate.
![Enrollment Certificates page with Generate Certificate page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/certificates/enrollment-certificates/generating-zscaler-issued-enrollment-ca-certificates/Generate%20Certificate%20window.png)
- Click **Generate**.