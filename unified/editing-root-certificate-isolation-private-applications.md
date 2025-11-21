# Editing a Root Certificate for Isolation in Private Applications
Source: https://help.zscaler.com/unified/editing-root-certificate-isolation-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1500421.pdf

After a root certificate is [added](/isolation/adding-root-certificates-isolation-zpa) to your organization, you can edit it at any time, even while it's associated with an isolation profile. The only root certificate you cannot edit is the default Zscaler Root Certificate. To learn more, see [About Root Certificates for Isolation in Private Applications](/unified/about-root-certificates-isolation-private-applications).
To edit a root certificate:
- Go to **Policies** > **Access Control** > **Clientless** > **Root Certificates**.
- Click the **Edit** icon next to the certificate you want to edit.
The **Edit Root Certificate** window appears.
- In the **Edit Root Certificate** window, edit the **Name** for the root certificate.
The PEM file cannot be changed. To use a different PEM file, [create a new custom root certificate](/unified/adding-root-certificates-isolation-private-applications).
[See image.](#Edit-Root-Cert)
- Click **Save**.
[![Edit window for root certificate](/downloads/isolation/profiles/profile-certificates/editing-root-certificate-isolation-zia/Edit-Root-Certificate_window.png)
]