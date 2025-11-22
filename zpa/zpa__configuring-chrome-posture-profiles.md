# Configuring Chrome Posture Profiles
Source: https://help.zscaler.com/zpa/configuring-chrome-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1529371.pdf

Chrome posture profiles are device posture profiles configured specifically for devices that use the Chrome Enterprise browser. They are a set of criteria that are evaluated on the device depending on the configured posture type.
To add a Chrome posture profile:
- Go to **Configuration & Control** > **Chrome Enterprise** **Browser** > **Chrome Posture Profile**.
- Click **Add**.
-
In the **Add Device Posture** window:
- Under **Define Posture and Scope**:
- **Name**: Enter the name of the device posture profile.
- **Description**: (Optional) Enter the description of the device posture profile.
- Under **Define Posture Configuration**, select which posture types to evaluate from the drop-down menus and complete the necessary configuration for each one.
- **Browser Version**: Enter the browser version.
- **Operating System**: Select the operating system (**Unspecified Operating System**, **ChromeOS**, **ChromiumOS**, **Windows**, **macOS**, **Linux**).
- **CrowdStrike Agent**: Enable or disable CrowdStrike Agent. CrowdStrike Agent protects devices by providing visible threat detection.
- **Disk Encryption**: Select the type of disk encryption (**Unspecified Disk Encryption**, **Unknown Disk Encryption**, **Disabled Disk Encryption**, **Encrypted Disk Encryption**).
- **OS Firewall**: Select the type of OS firewall to begin monitoring outgoing and incoming traffic (**Unspecified OS Firewall**, **Unknown OS Firewall**,** Disabled OS Firewall**,** Encrypted OS Firewall**).
- **Screen Lock Secured**: Select the type of screen lock after a certain idle duration period (**Unspecified Screen Lock Secured**, **Unknown Screen Lock Secured**, **Disabled Screen Lock Secured**, **Encrypted Screen Lock Secured**).
- **Secure Boot Mode**: Select the type of secure boot mode that occurs when you want to safely start up your device (**Unspecified Secure Boot Mode**, **Unknown Secure Boot Mode**, **Disabled Secure Boot Mode**, **Encrypted Secure Boot Mode**).
- **Safe Browsing Protection Level**: Select the type of safe browsing protection level that sends warnings to protect your device from security threats (**Unspecified Safe Browsing Protection Level**, **Unknown Safe Browsing Protection Level**, **Disabled Safe Browsing Protection Level**, **Encrypted Safe Browsing Protection Level**).
- **Key Trust Level**: Select the type of key trust level (**Unspecified Key Trust Level**, **ChromeOS Verified Mode**, **ChromeOS Developer Mode**, **Chrome Browser Hardware Key**, **Chrome Browser OS Key**, **Chrome Browser No Key**).
-
**Add More**: (Optional) Select more posture types.
**Add More** does not appear if you selected all the posture types.
[See image.](#posture)
- Click **Save**.
After saving the Chrome posture profile, you can begin [configuring access policies](/zpa/configuring-access-policies) in the ZPA Admin Portal to limit access to your private applications via the Chrome Enterprise browser.
[]
![Add a Chrome posture profile so that you can begin configure access policies](/downloads/zpa/browser-access/configuring-chrome-posture-profiles/ZPA-Chrome-Device-Posture-3.png)