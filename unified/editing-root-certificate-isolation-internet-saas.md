# Editing a Root Certificate for Isolation in Internet & SaaS
Source: https://help.zscaler.com/unified/editing-root-certificate-isolation-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1500396.pdf

Once a root certificate is added to your organization for Isolation, you can edit it at any time, even while it's associated with an isolation profile. The only certificate you cannot fully edit is the default Zscaler Root Certificate. To learn more, see [About Root Certificates in Isolation in Internet & SaaS](/unified/about-root-certificates-isolation-internet-saas).
To edit a root certificate:
- Go to **Infrastructure **>** Internet & SaaS **>** Network Policies **>** Root Certificates**.
- Click the **Edit** button next to the certificate.
The **Edit Root Certificate** window appears. In the **Edit Root Certificate** window:
- Edit the **Name** for the root certificate. The PEM file in the certificate cannot be changed. To use a different PEM file, you must [add a new root certificate](/unified/adding-root-certificates-isolation-internet-saas).
[See image.](#Edit-Root-Cert-window)
- Edit the **Type** of the root certificate. Use the dropdown menu to add or remove the selected type(s).
- Click **Done**.
[See image.](#Edit-Root-Cert_Type)
- Click **Save**.
[]![The Edit Root Certificate window appears. ](/downloads/isolation/profiles/profile-certificates/editing-custom-root-certificate-isolation/Edit-Root-Certificate-window.png)
[]![Edit the Root Certificate Type from the dropdown menu.](/downloads/isolation/profiles/profile-certificates/editing-custom-root-certificate-isolation/Edit-Root-Certificate-window_Type.png)