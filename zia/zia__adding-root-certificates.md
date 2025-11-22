# Adding Root Certificates
Source: https://help.zscaler.com/zia/adding-root-certificates
PDF: https://help.zscaler.com/pdf/com/en/1450026.pdf

This article describes adding a custom root certificate for a third-party proxy-chaining service or isolation profile in the ZIA Admin Portal. The Root Certificates page already carries the default Zscaler Root Certificate, which cannot be edited. You can add up to 10 root certificates for your organization. To learn about downloading certificates for SSL Inspection, see [Choosing the CA Certificate for SSL Inspection](/zia/choosing-ca-certificate-ssl-inspection).
- [Adding Third-Party SSL Root Certificates](#third-proxy)
- [Adding Root Certificates for Isolation](/isolation/adding-root-certificates-isolation-zia)
[]If your upstream proxy (third-party proxy service) is performing SSL Inspection, Zscaler requires you to install the root certificates of the proxy service to sign the MITM certificates.
To add a root certificate for proxy chaining:
- Go to **Administration** >** Root Certificates**.
- Click **Add Root Certificates**.
- In the **Add Root Certificates** window:
- **Name**: Enter a name for your certificate.
- **Type**: Select **Proxy Chaining** from the drop-down menu.
- **Content: **Browse and select the required root certificate (.pem file) from your system.
[See image.](#root-cert-proxy-chaining)
- Click **Save**.
[]![Adding Proxy Chaining Root Certificate in the ZIA Admin Portal](/downloads/zia/authentication-administration/certificates/adding-root-certificates/zia-adding-root-certificates-proxy-chaining.png)