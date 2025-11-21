# Creating Isolation Profiles for Private Applications
Source: https://help.zscaler.com/unified/creating-isolation-profiles-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1500351.pdf

To configure browser isolation for your application, you must use a Private Applications isolation profile. These profiles determine certain attributes and specifications of the isolation browser. They also define how the isolation browser handles web requests, as well as the level of interaction with the user's native browser. You can use isolation profiles to create policies to isolate specific web applications. To learn more, see [About Isolation Policy](/zpa/about-isolation-policy) and [Configuring Isolation Policies](/unified/configuring-isolation-policies).
Prerequisites
Before creating an isolation profile for Private Applications, make sure Isolation is enabled for your organization.
Creating a Private Applications Isolation Profile
To create a new Private Applications isolation profile:
- Go to **Policies** > **Access Control** > **Clientless **> **Profiles**.
- Click** Add Isolation Profile**.
The **Add Isolation Profile** window appears.
- In the **Add Isolation Profile **window:
- On the **General **tab:
- **Name**: Create a name for the Private Applications isolation profile.
- **Turbo Mode:** Enable or disable Turbo Mode. To learn more, see [Using Turbo Mode for Isolation](/isolation/understanding-turbo-mode-isolation).
- **Description**: (Optional) Enter a description.
Click **Next**.
[See image.](#General-Info)
- On the **Company Settings** tab:
- Enable or disable **Forward Internet Traffic via ZIA**. To learn more, see [Forwarding Traffic from ZPA Profiles to ZIA in Isolation](/isolation/forwarding-traffic-zpa-profiles-zia-isolation).
- Enter the **Organization ID** and **Cloud Name**.
- Select to use either a recommended or custom PAC file.
[See image.](#forward-traffic-to-zia)
- Enable at least one **Root Certificate** to deploy. The Zscaler Root Certificate is applied by default, and you cannot disable it. To learn more, see [About Root Certificates for Isolation in Private Applications](/isolation/about-root-certificates-isolation-zpa).
[See image.](#Company-Settings)
- Enable or disable **Debug Mode**. If you enable it, you must set a password for the ZIP file that is created at the end of a debug troubleshoot. Make sure to share the password with the user associated with the isolation profile. To learn more, see [Using Debug Mode for Isolation](/isolation/using-session-debug-mode-isolation).
[See image.](#Enable-debug-mode)
Click **Next**.
- On the **Security** tab, enable or disable the desired settings:
- Allow copying and pasting between your computer and the isolation browser.
- Allow file transfers between your computer and the isolation browser. If enabled, select whether the file transfer will be a flattened PDF or the original file.
- Allow printing of web pages and inline content from isolation.
- Restrict keyboard/text input to isolated web pages.
- Allow viewing Office files while in isolation.
- Allow local browser rendering while in isolation.
- Enabling Mic and Camera means the user can access their device's microphone and camera functionality while in an isolated session. This option can only be enabled if Turbo Mode is also enabled.
- Enabling Application Deep Linking allows users to open applications from their local machine via the rendered deep link data on an isolated web page. From there, the user can click the rendered link in the isolated browser, and open the application for use on their machine. If you enable this, add the specific links for the allowed applications to the list. If this feature is disabled for the isolation profile, or an application is not added to the list in the isolation profile, the user sees an error message explaining that the application isn't allowed by policy.
[See image.](#Security)
Click **Next**.
- On the **Regions** tab, from the drop-down menu, select at least two regions where the isolation profile should be available.
Click **Next**.
[See image.](#Regions)
- On the **Isolation Experience** tab:
- From the drop-down menu, select an **Isolation Banner**. The option you choose shows a preview banner in the window. Choose from existing banners, or create custom isolation banners to use for your isolation profiles. To learn more, see [Adding a Banner Theme for the Isolation End User Notification in Private Applications](/isolation/adding-banner-theme-isolation-end-user-notification-zpa).
- Enable or disable the option to have a persisting isolation URL bar.
- Select the **Isolation Experience **mode:
- **Native browser experience**: This mode provides the user with a browsing experience similar to accessing the native web page with a typical browser. Admins can also customize this view.
-
**Browser-in-browser experience**: This mode provides the user with the complete look and feel of an isolated session experience. To learn more, see [User Experience Modes in Isolation](/isolation/user-experience-modes-cloud-browser-isolation).
[See image.](#Iso-UX)
- (Optional) Enable **Persistent State**: Enabling this option causes the data from a user's active session to carry over to their new session each time they begin an isolated session. If you enable this feature, the Enable Persistent State window displays a consent message for you to read before confirming enablement. Click **Enable**. If you do not enable it, the data does not persist, meaning it is destroyed with the container when the user logs out or exceeds the session timeout.
[See image.](#Cookie-Persistence)
- Enable or disable the option to use a watermark while in isolation. Admins can enable watermarking per isolation profile and choose to display the user ID, date and timestamp (in UTC), and a custom message.
[See image.](#watermarking)
- (Optional) Enable **Language Translation**: This allows the user to translate any text from isolated web pages to the language of the user's choice.
[See image.](#Enable-Google-Translate)
- Click **Save**.
When saved, your new profile appears in the list of Private Applications isolation profiles. You can edit or delete a profile directly from the list. However, you cannot delete Private Applications isolation profiles used in isolation policies. To learn more, see [Editing Your Isolation Profile for Private Applications](/isolation/editing-your-isolation-profile-zpa) and [Deleting an Isolation Profile for Private Applications](/isolation/deleting-isolation-profile-zpa).
You can use this isolation profile to create policies in Private Applications to isolate specific web applications. To learn more, see [Configuring Isolation Policies](/zpa/configuring-isolation-policies).
[]
![Enter details in the General Information section.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_General_squircle.png)
[]
![Enter details in the Company Settings section.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_Company-Settings_Root-Certificates-section_squircles.png)
[]
![Enable or disable the options in the Security section.](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/ZPA_Add-Isolation-Profile_Security-tab_all-options-enabled_LINKS-ADDED_1.png)
[]
![Enable at least 2 regions for the profile. ](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_Regions_2-chosen_squircle.png)
[]
![Persistent state toggle.](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Persistent-State_enabled.png)
![Enable or disable Cookie Persistence. ](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Enable-Persistent-State_confirmation-window.png)
[]
![Select your options for the Isolation Experience section. ](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/ZPA-UI_Step-5_Isolation-Experience.png)
[]
![Enable watermarking. ](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zia-draft/ZIA_Add-Isolation-Profile_Iso-UX_Watermarking.png)
[]
![Enable company setting Options](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zpa-draft/Add-Isolation-Profile_traffic-forwarding.png)
[]![Enabling Debug Mode](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Add-Isolation-Profile_Company-Settings_ZPA-config_Debug-Mode.png)
[]![Enabling Language Translation](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zpa-draft-doc-53403/Add-Isolation-Profile_Iso-UX_Enable-Language-Translation.png)