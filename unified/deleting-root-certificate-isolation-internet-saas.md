# Deleting a Root Certificate for Isolation in Internet & SaaS
Source: https://help.zscaler.com/unified/deleting-root-certificate-isolation-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1500401.pdf

Almost all root certificates can be deleted, excluding the default Zscaler Root Certificate. This is because at least one root certificate is required per isolation profile. To learn more, see [About Root Certificates in Isolation in Internet & SaaS](/unified/about-root-certificates-isolation-internet-saas).
Additionally, if any other root certificates are associated with an isolation profile, you cannot delete them. You must first disable the certificate from the isolation profile before deleting it. To learn more, see [Editing Your Isolation Profile for Internet & SaaS](/unified/editing-your-isolation-profile-internet-saas).
To delete a root certificate:
- Go to **Infrastructure **>** Internet & SaaS **>** Network Policies **>** Root Certificates**.
- Click the **Edit** button next to the certificate.
The **Edit Root Certificate** window appears. In the **Edit Root Certificate** window:
- Click **Delete**. If the certificate is the default or is associated to an isolation profile, the delete button is grayed out.
[See image.](#Edit-Root-Cert_window_Delete)
- A warning message appears to confirm that you would like to delete the certificate. Click **Confirm**.
[See image.](#Confirmation-warning)
[]![The Edit Root Certificate window appears. Click Delete. ](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Edit-Root-Certificate-window_Delete.png)
[]![A warning message will appear to confirm that you would like to delete the certificate. Click Confirm.](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete-Root-Certificate_confirmation-window.png)