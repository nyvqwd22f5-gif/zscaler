# Deleting a Root Certificate for Isolation in ZPA
Source: https://help.zscaler.com/isolation/deleting-root-certificate-isolation-zpa
PDF: https://help.zscaler.com/pdf/com/en/1450601.pdf

Almost all root certificates can be deleted, excluding the default Zscaler Root Certificate. This is because at least one root certificate is required per isolation profile. To learn more, see [About Root Certificates for Isolation in ZPA](/isolation/about-root-certificates-isolation-zpa).
Additionally, if any other custom root certificates are associated with an isolation profile, you cannot delete them. You must first disable the certificate from the isolation profile before deleting it. To learn more, see [Editing Your Isolation Profile for ZPA](/isolation/editing-your-isolation-profile-zpa).
To delete a root certificate:
- Go to **Certificate Management** > **Root Certificates**.
- Click the **Delete** icon next to the certificate you want to delete. If the certificate is the default or is associated with an isolation profile, the delete icon is not available.
[See image.](#Delete-root-cert)
- A warning message appears to confirm deletion of the certificate. Click **Delete**.
[See image.](#Delete-root-cert-confirm-window)
The Root Certificates page refreshes and removes the deleted profile from the list.
[][![Click the Delete icon for the Root Certificate.](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete-Root-Certificate_squircle.png)
]
[][![Delete confirmation window](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete-root-certificate-window_squirclw.png)
]