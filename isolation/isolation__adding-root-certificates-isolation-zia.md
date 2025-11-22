# Adding Root Certificates for Isolation in ZIA
Source: https://help.zscaler.com/isolation/adding-root-certificates-isolation-zia
PDF: https://help.zscaler.com/pdf/com/en/1447291.pdf

The default Zscaler Root Certificate is deployed automatically as a placeholder root certificate for any new isolation profile. However, you can add your own root certificates to use for isolation profiles instead.
To add a ZIA root certificate:
- Go to **Administration** > **Certificates **>** Root Certificates**.
- Click **Add Root Certificate**.
The **Add Root Certificate **window appears.
- In the **Add Root Certificate** window:
- Enter a **Name**.
- For the **Type** of certificate, select **Browser Isolation** from the drop-down menu.
-
Browse your computer to choose a PEM file for the **Content**.
[See image.](#Add-Root-Cert)
- Click **Save**. The new root certificate appears in the page list.
You can add up to 10 root certificates for your organization. When added, you can [edit a root certificate](/isolation/editing-root-certificate-isolation-zia) that is not the default and not associated with an isolation profile.
To deploy root certificates to isolation profiles, see [Creating Isolation Profiles for ZIA](/isolation/creating-isolation-profiles-zia) and [Editing Your ZIA Isolation Profile](/isolation/editing-your-isolation-profile-zia).
[]![The dialog window for adding a new root certificate](/downloads/isolation/profiles/profile-certificates/adding-custom-root-certificate-isolation/Add-Root-Certificate_window_squircles.png)