# Signing a CSR Using the Active Directory Certificate Services
Source: https://help.zscaler.com/zia/signing-csr-using-active-directory-certificate-services
PDF: https://help.zscaler.com/pdf/com/en/1399266.pdf

When you configure a [custom intermediate root certificate](/zia/how-do-i-use-custom-certificate-ssl-inspection) for [SSL inspection](/zia/about-ssl-inspection), you must generate and download a certificate signing request (CSR) in the ZIA Admin Portal, then send the CSR to a certificate authority (CA) for signing. Ensure that the CSR is signed as a subordinate CA or intermediate CA.
Below is a configuration example showing how the CSR can be signed using the Active Directory Certificate Services using Certreq.exe. To learn more about Certreq, see the [Microsoft documentation](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn296456(v%3dws.11)).
- Generate a certificate signing request. For more information, see [Generating Certificate Signing Request (CSR) for SSL Inspection](/zia/how-do-i-generate-certificate-signing-request-csr-ssl-inspection). For this example, the downloaded file will be named `zscalerdemo.csr`.
- Open an elevated command prompt
- Enter cmd in the search bar.
- Press `CTRL + SHIFT + ENTER`.
- A dialog prompt will appear asking if you want to run the program as an administrator. Select **Yes** to open an elevated command prompt.
- Enter the following command: certreq -submit -attrib "CertificateTemplate:SubCA" zscalerdemo.req zscalerdemo.cer
- From the dialog box, choose the desired certificate authority.
- Click **OK**.
- The issued certificate will be saved as zscalerdemo.cer so long as you have domain administrator access permissions. Navigate to the certificate that you saved and change the certificate file name so it has a .pem extension. For example, zscalerdemo.pem. The Zscaler service only accepts certificates with the .pem extension.