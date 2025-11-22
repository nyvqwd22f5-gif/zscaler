# Deleting a Root Certificate for Isolation in Private Applications
Source: https://help.zscaler.com/unified/deleting-root-certificate-isolation-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1500426.pdf

Almost all root certificates can be deleted, excluding the default Zscaler Root Certificate. This is because at least one root certificate is required per isolation profile. To learn more, see [About Root Certificates for Isolation in Private Applications](/unified/about-root-certificates-isolation-private-applications).
Additionally, if any other custom root certificates are associated with an isolation profile, you cannot delete them. You must first disable the certificate from the isolation profile before deleting it. To learn more, see [Editing Your Isolation Profile for Private Applications](/unified/editing-your-isolation-profile-private-applications).
To delete a root certificate:
- Go to **Policies** > **Access Control** > **Clientless** > **Root Certificates**.
- Click the **Delete** icon next to the certificate you want to delete. If the certificate is the default or is associated with an isolation profile, the delete icon is not available.
- A warning message appears to confirm deletion of the certificate. Click **Delete**.
[See image.](#Delete-Root-Cert)
The Root Certificates page refreshes and removes the deleted profile from the list.
[][![Delete confirmation window](/downloads/isolation/profiles/profile-certificates/deleting-custom-root-certificate-isolation/Delete-root-certificate-window_squirclw.png)
]