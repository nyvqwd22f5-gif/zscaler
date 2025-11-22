# Creating Isolation Profiles for Internet & SaaS
Source: https://help.zscaler.com/unified/creating-isolation-profiles-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1492776.pdf

When creating an Internet & SaaS policy with the action as Isolate, you must reference an isolation profile in the policy you're creating. These profiles determine certain attributes and specifications about how the user interacts with the isolated web page, where the isolation containers are spun up, and what the isolation experience looks like to the user.
You can use [Private Applications isolation profiles](/unified/creating-isolation-profiles-private-applications) to create policies in Private Applications to isolate specific web applications. To learn more, see [About Isolation Policy](/unified/about-isolation-policy).
For any organization that is using Isolation, Internet & SaaS and Private Applications automatically create default isolation profiles. You can use the default isolation profiles or manually create isolation profiles to use in Internet & SaaS and Private Applications policies. To learn more, see [Default Isolation Profiles in Isolation](/unified/default-isolation-profiles-isolation).
For certain levels of Internet & SaaS and Isolation integration access, admins are provided with preconfigured profiles that are only partially editable. To learn more, see [Understanding Isolation of Miscellaneous and Unknown Category in Internet & SaaS](/unified/understanding-isolation-miscellaneous-and-unknown-category-internet-saas) and [Editing Your Isolation Profile for Internet & SaaS](/unified/editing-your-isolation-profile-internet-saas).
Prerequisites
Before creating an isolation profile for Internet & SaaS, ensure the following:
- For isolation policies to be applied, the Zscaler service must authenticate the web traffic. Unauthenticated traffic or traffic from locations with authentication disabled is not subjected to isolation policies.
- For HTTPS web pages to be isolated, the Zscaler service must SSL inspect the traffic.
Creating an Isolation Profile for Internet & SaaS
To create a new isolation profile:
- Go to **Policies **>** Common Configuration **>** Resources **>** Browser Isolation**.
The **Isolation Profiles** menu appears and displays the Internet & SaaS profiles view.
- Click **Add Profile**.
The **Add Isolation Profile** window appears.
- In the **Add Isolation Profile** window:
- On the **General** tab:
- **Name**: Enter a name for the Internet & SaaS isolation profile.
- **Turbo Mode**: Enable or disable Turbo Mode.
- **Description**: (Optional) Enter a description of the profile.
Click **Next**.
[See image.](#Add-Isolation-Profile-General-Info)
- On the **Company Settings** tab:
- Choose to use either the** **recommended PAC file URL or your own manually configured PAC file URL:
- If you select **Use recommended PAC file URL**, the** Automatic proxy configuration URL **field is populated by default with the recommended PAC file from your Hosted PAC Files list in Internet & SaaS. The isolation browser configures the PAC file within the endpoint experience containers, and any traffic to the internet from the isolated browser is also forwarded through the Internet & SaaS cloud.
- Enable or disable **Override PAC file and return traffic to the Internet & SaaS Public Service Edge**. The Internet & SaaS Public Service Edges use auto-geoproximity, meaning that the traffic is returned to the service edge closest to the location of the user, not the location of the isolation browser. To see the full list of Internet & SaaS Public Service Edges, see the [Zscaler Configuration Portal](https://config.zscaler.com/zscaler.net/cenr?_gl=1*1hlfti1*_gcl_au*MTA2ODE5OTQ4NS4xNzIxMDY2MjU5*_ga*MTA0ODcwOTQ4My4xNzA1NDMwMjk4*_ga_10SPJ4YJL9*MTcyNzEyNTIyMC4zMDkuMS4xNzI3MTI5MzYwLjYwLjAuMTc5MDE2OTU4OQ..).
[See image.](#Add-Isolation-Profile_Company-Settings_PAC-File-URL)
- Enable or disable **Debug Mode**. If you enable it, you must set a password for the ZIP file that is created at the end of a debug troubleshoot. Make sure to share the password with the user associated with the isolation profile.
[See image.](#Enable-Debug-Mode)
- From the **Root Certificate** drop-down menu, select at least one file. The **Zscaler Root Certificate** that Internet & SaaS uses for SSL inspection appears by default in the drop-down menu. If your organization uses custom root certificates for SSL inspection, you can add them before creating isolation profiles. You can [add](/unified/adding-root-certificates-isolation-internet-saas) up to 10 root certificates for your organization. To learn more, see [About Internet & SaaS Root Certificates for Isolation](/unified/about-root-certificates-isolation-internet-saas).
[See image.](#Add-Isolation-Profile_Company-Settings_Root-Certificates)
- Click **Done**.
Click **Next**.
- On the **Security** tab:
- Enable or disable to **Allow copy & paste **to and from your computer and the isolation browser.
- Enable or disable to **Allow file transfers **to and from your computer and the isolation browser. If you enable for **isolation to local computer**, select whether the file transfer will be a Flattened PDF, Sandbox Scanned File, or the Original File. To learn more, see [Sandbox Integration with Isolation](/unified/sandbox-integration-isolation).
- Enable or disable to **Allow printing **of web pages and inline content from isolation.
- Enable or disable to restrict keyboard/text input to isolated web pages to be** Read-Only**.
- Enable or disable to allow the **View of Office files in isolation**.
- Enable or disable to **Allow local browser rendering** while in isolation.
- Enable or disable **Microphone and Camera** to allow the user to access their device's microphone and camera functionality while in an isolated session. This option can only be enabled if Turbo Mode is also enabled.
[See image.](#Add_Isolation_Profile_Security)
- Enable or disable the options for **Votiro CDR Integration**.
- **Enable Votiro CDR**: Enable to allow Votiro to sanitize all uploaded and downloaded files by default.
- **Download**: Enable or disable Votiro sanitizing files that you download.
- **Upload**: Enable or disable Votiro sanitizing files that you upload.
- **Votiro Policy Name**: Select the Votiro policy to enforce the sanitization. If you do not select a policy, a default Votiro policy is applied. To learn more, see [Configuring Votiro Integration for Isolation](/unified/understanding-votiro-integration-isolation) and [About Partner Integrations](/unified/about-partner-integrations).
[See image.](#Enable-Votiro-options)
- Enabling **Application Deep Linking** allows the user to open applications from their local machine via the rendered deep link data on an isolated web page. From there, the user can click the rendered link in the isolated browser and open the application for use on their machine. If you enable this option, add the specific links for the allowed applications to the list. If you disable this feature for the isolation profile, or an application is not on the list in the isolation profile, the user sees an error message explaining that the application isn't allowed by policy.
[See image.](#enable-application-deep-linking)
- On the **Regions** tab:
- From the drop-down menu, select at least two regions. The isolation containers are leased to the user only from the selected regions based on the least network latency.
- Click **Done**.
- Click **Next**.
[See image.](#Add_Isolation_Profile_Regions)
- On the **Isolation Experience** tab:
- From the drop-down menu, select an **Isolation Banner**. The option you choose shows a preview banner in the window. Choose from existing banners, or create custom isolation banners to use for your isolation profiles. To learn more, see [Adding a Banner Theme for the Isolation End User Notification in Internet & SaaS](/unified/adding-banner-theme-isolation-end-user-notification-internet-saas).
- Enable or disable the option to have a persisting isolation URL bar.
- Select the **Isolation Experience **mode:
- **Native browser experience**: This mode provides the user with a browsing experience similar to accessing the native web page with a typical browser. The user can customize this view.
- **Browser-in-browser experience**: This mode provides the user with the complete look and feel of an isolated session experience.
[See image.](#Add_Isolation_Profile_Isolation-Experience)
- Enable or disable the option to use a watermark while in isolation. Admins can enable watermarking per isolation profile and choose to display the user ID, date and timestamp (in UTC), and a custom message.
[See image.](#watermark)
- (Optional) Enable **Persistent State**: Enabling this option causes the data from a user's active session to carry over to their new session each time they enter an isolated session. If you enable this feature, the **Enable Persistent State **window displays a consent message for you to read before confirming enablement. Click **Enable**. If you do not enable it, the data does not persist, meaning it is destroyed with the container when the user logs out or exceeds the session timeout.
[See images.](#Persistent-State-toggle)
- (Optional) Enable **Language Translation**. This option allows the user to translate any text from isolated web pages to the language of the user's choice.
[See image.](#Enable-Language-Translation)
- Click **Save**.
After you save your new isolation profile, it appears in the list of Internet & SaaS isolation profiles. To edit a profile directly from the list, click the **Edit** icon. To learn more, see [Editing Your Internet & SaaS Isolation Profile](/unified/editing-your-isolation-profile-internet-saas) and [Deleting Your Internet & SaaS Isolation Profile](/unified/deleting-your-isolation-profile-internet-saas).
You can use this isolation profile to create a policy in Internet & SaaS to allow traffic forwarding through browser isolation. To learn more, see [Configuring Internet & SaaS for Isolation](/unified/configuring-internet-saas-isolation).
[]![Add Isolation Profile window appears, starting with General Information section.](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zia-draft-doc-49518/ZIA_Add-Isolation-Profile_General-section.png)
[]![Make your selections in the PAC File URL fields of the Company Settings section. ](/downloads/tech-pubs-drafts/isolation-draft-articles/Add-Isolation-Profile_Company-Settings_PAC-File-URL-section_squircle.png)
[]![Select the root certificate for the ZIA isolation profile. ](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_Company-Settings_Root-Certificates-section_squircles.png)
[]![Enable or disable the options in the Security section.](/downloads/isolation/profiles/zia-profiles/creating-isolation-profiles-zia/Security_all-options-enabled.png)
[]![Select at least 2 regions for the isolation profile.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_Regions_2-chosen_squircle.png)
[]![Make your selections for the Isolation Experience.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Add-Isolation-Profile_Iso-UX_Persist-Isolation-URL-Bar.png)
[]![Enable or disable the options for Watermarking.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/ZIA_Add-Isolation-Profile_Iso-UX_Watermarking.png)
[]![Add-Isolation-Profile_Company-Settings_PAC-File_Debug-Mode.png](/downloads/tech-pubs-drafts/isolation-draft-articles/Add-Isolation-Profile_Company-Settings_PAC-File_Debug-Mode.png)
[]![Add-Iso-Profile_Votiro-toggles-enabled.png](/downloads/isolation/profiles/zia-profiles/creating-isolation-profiles-zia/Add-Iso-Profile_Votiro-toggles-enabled.png)
[]![enable-app-deep-link-ZIA.png](/downloads/isolation/profiles/zia-profiles/enable-app-deep-link-ZIA.png)
[]![Add-Isolation-Profile_Iso-UX_Enable-Language-Translation.png](/downloads/isolation/profiles/zia-profiles/creating-isolation-profiles-zia/Add-Isolation-Profile_Iso-UX_Enable-Language-Translation.png)
[]![Persistent-State_enabled.png](/downloads/isolation/profiles/zia-profiles/creating-isolation-profiles-zia/Persistent-State_enabled.png)
![If you choose to enable Cookie Persistence, the disclaimer message displays. ](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zia-draft-doc-53403/Enable-Persistent-State_confirmation-window.png)