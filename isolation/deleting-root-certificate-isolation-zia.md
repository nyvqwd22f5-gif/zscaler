# Deleting a Root Certificate for Isolation in ZIA
Source: https://help.zscaler.com/isolation/deleting-root-certificate-isolation-zia
PDF: https://help.zscaler.com/pdf/com/en/1447366.pdf

Almost all root certificates can be deleted, excluding the default Zscaler Root Certificate. This is because at least one root certificate is required per isolation profile. To learn more, see [About Root Certificates in Isolation](/isolation/about-root-certificates-isolation-zia).
Additionally, if any other root certificates are associated with an isolation profile, you cannot delete them. You must first disable the certificate from the isolation profile before deleting it. To learn more, see [Editing Your ZIA Isolation Profile](/isolation/editing-your-zia-isolation-profile-0).
To delete a root certificate:
- Go to **Administration** > **Proxy Chaining** >** Root Certificates**.
- Click the **Edit** button next to the certificate.
[See image.](#Root-Certificates_Edit-icon)
The **Edit Root Certificate** window appears. In the **Edit Root Certificate** window:
- Click **Delete**. If the certificate is the default or is associated with an isolation profile, the delete button is grayed out.
[See image.](#Edit-Root-Cert_Delete_window)
- A warning message appears to confirm that you would like to delete the certificate. Click **Confirm**.
[See image.](#Confirmation-warning-window)
[]![The Edit Root Certificate window appears. ](/downloads/isolation/profiles/profile-certificates/deleting-root-certificate-isolation-zia/Admin_Root-Certificates_Edit-button-squircle.png)
[]![The Edit Root Certificate window appears. Click Delete. ](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Edit-Root-Certificate-window_Delete.png)
[]![A warning message will appear to confirm that you would like to delete the certificate. Click Confirm.](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete-Root-Certificate_confirmation-window.png)