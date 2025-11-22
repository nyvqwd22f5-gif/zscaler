# Creating Isolation Profiles for ZPA
Source: https://help.zscaler.com/isolation/creating-isolation-profiles-zpa
PDF: https://help.zscaler.com/pdf/com/en/1447731.pdf

[Watch a video about creating a ZPA Isolation Profile for Isolation.](https://fast.wistia.net/embed/iframe/bbh6zk55s2)
To configure browser isolation for your application, you must use a Zscaler Private Access (ZPA) isolation profile. These profiles determine certain attributes and specifications of the isolation browser. They also define how the isolation browser handles web requests, as well as the level of interaction with the user's native browser. You can use isolation profiles to create policies in ZPA to isolate specific web applications. To learn more, see [About Isolation Policy](/zpa/about-isolation-policy) and [Configuring Isolation Policies](/zpa/configuring-isolation-policies).
Prerequisites
Before creating an isolation profile for ZPA, make sure Isolation is enabled for your organization in ZPA.
Creating a ZPA Isolation Profile
To create a new ZPA isolation profile:
- Go to **Configuration & Control** > **Browser Isolation** > **Isolation Profiles**.
- Click** Add Isolation Profile**.
The **Add Isolation Profile** window appears.
[See image.](#Add-Isolation-Profile-button)
- In the **Add Isolation Profile **window:
- On the **General **tab:
- **Name**: Create a name for the ZPA isolation profile.
- **Turbo Mode**: Enable or disable Turbo Mode. To learn more, see [Using Turbo Mode for Isolation](/isolation/using-turbo-mode-isolation).
- **Description**: (Optional) Enter a description.
Click **Next**.
[See image.](#General-Info)
- On the **Company Settings** tab:
- Enable or disable **Forward Internet Traffic via ZIA**. To learn more, see [Forwarding Traffic from ZPA Profiles to ZIA in Isolation](/isolation/forwarding-traffic-zpa-profiles-zia-isolation).
- Enter the **Organization ID** and **Cloud Name**.
- Select to use either a recommended or custom PAC file.
[See image.](#forward-traffic-to-zia)
- Enable at least one **Root Certificate** to deploy. The Zscaler Root Certificate is applied by default, and you cannot disable it. To learn more, see [About Root Certificates for Isolation in ZPA](/isolation/about-root-certificates-isolation-zpa).
[See image.](#Company-Settings)
- Enable or disable **Debug Mode**. If you enable it, you must set a password for the ZIP file that is created at the end of a debug troubleshoot. Make sure to share the password with the user associated with the isolation profile. To learn more, see [Using Debug Mode for Isolation](/isolation/using-session-debug-mode-isolation).
[See image.](#Enable-debug-mode)
Click **Next**.
- On the **Security** tab, enable or disable the following settings:
- Allow copying and pasting between your computer and the isolation browser.
- Allow file transfers between your computer and the isolation browser. If you enable this feature, select whether the file transfer will be a Flattened PDF or the Original File.
- Allow printing of web pages and inline content from isolation.
- Restrict keyboard/text input to isolated web pages.
- Allow viewing Office files while in isolation.
- Allow local browser rendering while in isolation.
- Enabling Mic and Camera means the user can access their device's microphone and camera functionality while in an isolated session. This option can only be enabled if Turbo Mode is also enabled.
- Enabling Application Deep Linking allows users to open applications from their local machine via the rendered deep link data on an isolated web page. From there, the user can click the rendered link in the isolated browser, and open the application for use on their machine. If you enable this feature, add the specific links for the allowed applications to the list. If you disable this feature for the isolation profile, or an application is not on the list in the isolation profile, the user sees an error message explaining that the application isn't allowed by policy.
[See image.](#Security)
Click **Next**.
- On the **Regions** tab, from the drop-down menu, select at least two regions where the isolation profile should be available.
Click **Next**.
[See image.](#Regions)
- On the **Isolation Experience** tab:
- From the drop-down menu, select an **Isolation Banner**. The option you choose shows a preview banner in the window. Choose from existing banners, or create custom isolation banners to use for your isolation profiles. To learn more, see [Adding a Banner Theme for the Isolation End User Notification in ZPA](/isolation/adding-banner-theme-isolation-end-user-notification-zpa).
- Enable or disable the option to have a persisting isolation URL bar.
- Select the **Isolation Experience **mode:
- **Native browser experience**: This mode provides the user with a browsing experience similar to accessing the native web page with a typical browser. Admins can also customize this view.
- **Browser-in-browser experience**: This mode provides the user with the complete look and feel of an isolated session experience. To learn more, see [User Experience Modes in Isolation](/isolation/user-experience-modes-cloud-browser-isolation).
[See image.](#Iso-UX)
- (Optional) Enable **Persistent State**: Enabling this option causes the data from a user's active session to carry over to their new session each time they begin an isolated session. If you enable this feature, the Enable Persistent State window displays a consent message for you to read before confirming enablement. Click **Enable**. If you do not enable it, the data does not persist, meaning it is destroyed with the container when the user logs out or exceeds the session timeout. To learn more, see [Using Persistent State for Isolation](/isolation/using-persistent-state-isolation).
[See image.](#Cookie-Persistence)
- Enable or disable the option to use a watermark while in isolation. Admins can enable watermarking per isolation profile and choose to display the user ID, date and timestamp (in UTC), and a custom message.
[See image.](#watermarking)
- (Optional) Enable **Language Translation**: This allows the user to translate any text from isolated web pages to the language of the user's choice. To learn more, see [Using the Isolation Bar in Native Browser Experience].
[See image.](#Enable-Google-Translate)
- Click **Save**.
When saved, your new profile appears in the list of ZPA **isolation profiles**. You can edit or delete a profile directly from the list. However, you cannot delete ZPA isolation profiles used in ZPA isolation policies. To learn more, see [Editing Your Isolation Profile for ZPA](/isolation/editing-your-isolation-profile-zpa) and [Deleting an Isolation Profile for ZPA](/isolation/deleting-isolation-profile-zpa).
You can use this isolation profile to create policies in ZPA to isolate specific web applications. To learn more, see [Configuring Isolation Policies](/zpa/configuring-isolation-policies).
[]
![Click Add Isolation Profile.](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Configuration-and-Control_Browser-Isolation_Add-Isolation-Profile_squircle.png)
[]
![Enter details in the General Information section.](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/ZIA_Add-Isolation-Profile_General-section.png)
[]
![Enter details in the Company Settings section.](/downloads/isolation/profiles/zia-profiles/creating-zia-isolation-profile-isolation/Add-Isolation-Profile_Company-Settings_Root-Certificates-section_squircles.png)
[]
![Enable or disable the options in the Security tab.](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Security_all-options-enabled.png)
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
[]![Add-Isolation-Profile_Company-Settings_ZPA-config_Debug-Mode.png](/downloads/isolation/profiles/zpa-profiles/creating-isolation-profiles-zpa/Add-Isolation-Profile_Company-Settings_ZPA-config_Debug-Mode.png)
[]![Add-Isolation-Profile_Iso-UX_Enable-Language-Translation.png](/downloads/tech-pubs-drafts/isolation-draft-articles/creating-isolation-profiles-zpa-draft-doc-53403/Add-Isolation-Profile_Iso-UX_Enable-Language-Translation.png)