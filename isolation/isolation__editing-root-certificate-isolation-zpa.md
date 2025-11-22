# Editing a Root Certificate for Isolation in ZPA
Source: https://help.zscaler.com/isolation/editing-root-certificate-isolation-zpa
PDF: https://help.zscaler.com/pdf/com/en/1450596.pdf

After a root certificate is [added](/isolation/adding-root-certificates-isolation-zpa) to your organization, you can edit it at any time, even while it's associated with an isolation profile. The only root certificate you cannot edit is the default Zscaler Root Certificate. To learn more, see [About Root Certificates for Isolation in ZPA](/isolation/about-root-certificates-isolation-zpa).
To edit a root certificate:
- Go to **Certificate Management** > **Root Certificates**.
- Click the **Edit** icon next to the certificate you want to edit.
The **Edit Root Certificate** window appears.
[See image.](#Edit-Root-Certificate_icon)
- In the **Edit Root Certificate** window, edit the **Name** for the root certificate.
The PEM file cannot be changed. To use a different PEM file, [create a new custom root certificate](/isolation/adding-root-certificates-isolation-zpa).
[See image.](#Edit-Root-Cert-window)
- Click **Save**.
[]![Click Edit for the desired root certificate. ](/downloads/isolation/profiles/profile-certificates/editing-root-certificate-isolation-zpa/Edit-Root-Certificate_squircle.png)
[]![Edit window for root certificate](/downloads/isolation/profiles/profile-certificates/editing-root-certificate-isolation-zia/Edit-Root-Certificate_window.png)