# Adding Root Certificates
Source: https://help.zscaler.com/unified/adding-root-certificates
PDF: https://help.zscaler.com/pdf/com/en/1497751.pdf

This article describes adding a custom root certificate for a third-party proxy chaining service or isolation profile in the Admin Portal. The Root Certificates page already carries the default Zscaler Root Certificate, which cannot be edited. You can add up to 10 root certificates for your organization.
Adding Third-Party SSL Root Certificates
If your upstream proxy (third-party proxy service) is performing SSL inspection, Zscaler requires you to install the root certificates of the proxy service to sign the MITM certificates.
To add a root certificate for proxy chaining:
- Go to **Infrastructure** >** Internet SaaS **>** Network Policies **>** Root Certificates**.
- Click **Add Root Certificates**.
-
In the **Add Root Certificates** window:
- **Name**: Enter a name for your certificate.
- **Type**: Select **Proxy Chaining** from the drop-down menu.
- **Content: **Browse and select the required root certificate (.pem file) from your system.
[See image.](#root-cert-proxy-chaining)
- Click **Save**.
[]![Screenshot of adding Proxy Chaining Root Certificate in the ZIA Admin Portal](/downloads/zia/authentication-administration/certificates/adding-root-certificates/zia-adding-root-certificates-proxy-chaining.png)