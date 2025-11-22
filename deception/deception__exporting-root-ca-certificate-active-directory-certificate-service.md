# Exporting a Root CA Certificate from an Active Directory Certificate Service
Source: https://help.zscaler.com/deception/exporting-root-ca-certificate-active-directory-certificate-service
PDF: https://help.zscaler.com/pdf/com/en/1531334.pdf

When you create an AD domain with credentials in the Zscaler Deception Admin Portal, you must upload a domain CA certificate (.crt) to enable a secure LDAP connection. This certificate must be in the PEM format. This article provides instructions for exporting a CA certificate from an Active Directory Certificate Service (AD CS) server.
As a prerequisite, install the AD CS server on your system.
Creating a Certificate Snap-in
To extract a root CA certificate, you must first create a certificate snap-in in the Microsoft Management Console (MMC).
To create a certificate snap-in:
- Press the `Windows key+R` in your system.
- In the **Run** window, enter `mmc.exe` to open MMC.
[See image.](#mmc-console)
- Go to **File** > **Add/Remove Snap-in**.
- In the **Add or Remove Snap-ins** window, select **Certificates**, and then click **Add**.
[See image.](#add-certificates)
- In the **Certificates snap-in** window, select **Computer account**, and then click **Next**.
[See image.](#computer-account)
- In the **Select Computer** window, select **Local computer**, and then click **Finish**.
[See image.](#local-computer)
- Click **OK** to save the snap-in settings.
[See image.](#save-snap-in-settings)
Exporting a CA Certificate
To export a CA certificate:
- In MMC, go to **Console Root** > **Certificates (Local Computer)** > **Trusted Root Certification Authorities** > **Certificates**.
[See image.](#navigate-certificate-export)
- Select a root certificate created for your AD domain. The certificate has the same name as your domain.
- Right-click the certificate, and then select **All Tasks** > **Export** from the drop-down menu.
[See image.](#export-certificate-option)
- In the **Certificate Export Wizard**, click **Next**.
- In **Export File Format**, select **Base-64 encoded X.509 (.CER)**,** **and then click **Next**.
[See image.](#select-format)
- In **File to Export**, browse to the location where you want to export the certificate and provide the name of the certificate file,** **and then click **Next**.
[See image.](#location-name-certificate)
- Click **Finish.**
[See image.](#complete-certificate-export)
The CA certificate is exported successfully to the specified location in your local system.
After exporting the CA certificate, change the file extension of the certificate from .cer to .crt. You can upload the .crt file to the Zscaler Deception Admin Portal when [adding an AD domain](/deception/adding-active-directory-domain).
[]![Microsoft Management Console](/downloads/deception/deceive/active-directory-decoys/extracting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-mmc-console.png)
[] ![Add certificates](/downloads/deception/deceive/active-directory-decoys/extracting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-add-certificate.png)
[] ![Manage certificates for a computer account](/downloads/deception/deceive/active-directory-decoys/extracting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-computer-account.png?1655201301)
[]![Select local computer](/downloads/deception/deceive/active-directory-decoys/extracting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-local-computer.png)
[]![Save snap-in settings](/downloads/deception/deceive/active-directory-decoys/exporting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-save-snap-in-settings.png?1655465538)
[] ![Navigate to certificate export option](/downloads/deception/deceive/active-directory-decoys/extracting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-export-navigation.png)
[]![Export certificate](/downloads/deception/deceive/active-directory-decoys/exporting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-export-certificate.png?1655466547)
[]![Select certificate export format](/downloads/deception/deceive/active-directory-decoys/exporting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-base-64-format.png)
[]![Specify location and name of the certificate](/downloads/deception/deceive/active-directory-decoys/exporting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-export-certificate-location.png?1655467046)
[]![Completed exporting CA certificate](/downloads/deception/deceive/active-directory-decoys/exporting-root-ca-certificate-active-directory-certificate-service/zscaler-deception-certificate-export-completed.png)