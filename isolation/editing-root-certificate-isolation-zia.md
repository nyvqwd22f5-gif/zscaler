# Editing a Root Certificate for Isolation in ZIA
Source: https://help.zscaler.com/isolation/editing-root-certificate-isolation-zia
PDF: https://help.zscaler.com/pdf/com/en/1447361.pdf

Once a root certificate is added to your organization for Isolation, you can edit it at any time, even while it's associated with an isolation profile. The only certificate you cannot fully edit is the default Zscaler Root Certificate. To learn more, see [About Root Certificates in Isolation](/isolation/about-root-certificates-isolation-zia).
To edit a root certificate:
- Go to **Administration** > **Certificates** >** Root Certificates**.
- Click the **Edit** button next to the certificate.
[See image.](#Root-Cert-page_Edit-button)
The **Edit Root Certificate** window appears. In the **Edit Root Certificate** window:
- Edit the **Name** for the root certificate. You cannot change the PEM file in the certificate. To use a different PEM file, you must [add a new root certificate](/isolation/adding-root-certificates-isolation-zia).
[See image.](#Edit-Root-Cert-window)
- Edit the **Type** of the root certificate. Use the drop-down menu to add or remove the selected type(s).
- Click **Done**.
[See image.](#Edit-Root-Cert_Type)
- Click **Save**.
[][![ZIA Root Certificates Page](/downloads/isolation/profiles/profile-certificates/editing-custom-root-certificate-isolation/Admin_Root-Certificates_Edit-button-squircle.png)
]
[][![The Edit Root Certificate window appears. ](/downloads/isolation/profiles/profile-certificates/editing-custom-root-certificate-isolation/Edit-Root-Certificate-window.png)
]
[][![Edit the Root Certificate Type from the dropdown menu.](/downloads/isolation/profiles/profile-certificates/editing-custom-root-certificate-isolation/Edit-Root-Certificate-window_Type.png)
]