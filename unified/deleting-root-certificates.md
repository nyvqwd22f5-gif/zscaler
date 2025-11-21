# Deleting Root Certificates
Source: https://help.zscaler.com/zia/deleting-root-certificates
PDF: https://help.zscaler.com/pdf/com/en/1450036.pdf

You can delete all custom root certificates except the default Zscaler Root Certificate. Also, if a root certificate is associated with an isolation profile, you cannot delete it. You must first disable the certificate from the isolation profile before deleting it.
To delete a root certificate:
- Go to **Administration** >** Root Certificates**.
- Click the **Edit** icon next to the certificate.
[See image.](#Root-Certificates_Edit-button)
The **Edit Root Certificate** window appears. In the **Edit Root Certificate** window:
- Click **Delete**. If the certificate is the default certificate or is associated with an isolation profile, the delete button is grayed out.
[See image.](#Edit-Root-Cert_window_Delete)
- A warning message appears to confirm that you want to delete the certificate. Click **Confirm**.
[See image.](#Confirmation-warning)
[![The Edit Root Certificate window appears. ](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/zia_admin_root_certificates_delete_button-squircle.png)
]
[![The Edit Root Certificate window appears. Click Delete. ](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Edit_root_certificate_window_Delete.png)
]
[![A warning message will appear to confirm that you would like to delete the certificate. Click Confirm.](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete_root_certificate_confirmation_window.png)
]