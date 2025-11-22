# Configuring Device Posture Profiles
Source: https://help.zscaler.com/zscaler-client-connector/configuring-device-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1296826.pdf

[Watch a video on Device Posture Profiles.](https://fast.wistia.net/embed/iframe/8op4rkia3r)
Posture profiles for both Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) devices are created in the Device Posture section. To learn more about posture profiles, see [About Device Posture Profiles](/zscaler-client-connector/about-device-posture-profiles). The posture profiles are used for [configuring access policies](/zpa/configuring-access-policies) in the ZPA Admin Portal and for [adding posture profile trust levels](/zscaler-client-connector/adding-zia-posture-profiles) for ZIA. To learn more about posture profiles for ZIA, see [About ZIA Posture Profiles](/zscaler-client-connector/about-zia-posture-profiles).
To configure a device posture profile for Zscaler Client Connector:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, select **Device Posture**.
- Click **Add Device Posture**.
- In the **Add Device Posture **window:
- **Name**:** **Enter a name for the device posture profile.
- **Platform**: Select one or more of the following platform options:
- **Windows**
- **macOS**
- **Linux**
- **Android**
- **iOS**
- **Apply to Windows Machine Tunnel**: When selected, the posture type is evaluated and applied to the ZPA pre-Windows login machine tunnel. If not selected, the posture type is only evaluated for ZPA and ZIA tunnels. Applies to the following device postures for Windows: Client Certificate, Certificate Trust, File Path, Registry Key, Firewall, Full Disk Encryption, Domain Joined, AzureAD Domain Joined, Server Validated Client Certificate, OS Version and Zscaler Client Connector Version.
- **Apply to macOS Machine Tunnel**: When selected, the posture type is evaluated and applied to the ZPA pre-macOS login machine tunnel. If not selected, the posture type is only evaluated for ZPA and ZIA tunnels. Applies to the following device postures for macOS: CrowdStrike ZTA Score, Full Disk Encryption, File Path, Firewall, Domain Joined, and OS Version.
- **Apply when added as Partner Tenant**: Applies to Zscaler Client Connector version 4.6 and later for Windows. When selected, the posture type is evaluated and applied to the ZPA tunnel used to connect to a partner tenant. If not selected, the posture type is only evaluated for ZPA and ZIA tunnels.
-
**Frequency (In Minutes)**: Applies to Zscaler Client Connector version 4.4 and later for Windows and Zscaler Client Connector version 4.5 and later for macOS. For each posture type, select how often Zscaler Client Connector evaluates device posture by selecting a value, in one-minute intervals, from the drop-down menu. The maximum default value is 15 minutes. The minimum value is 2 minutes.
For the following posture checks, Zscaler Client Connector evaluates device posture immediately when the posture changes on a device, regardless of what is configured in the **Frequency (In Minutes)** field:
- **Process Check**
- **Detect Carbon Black**
- **Detect CrowdStrike**
- **Detect SentinelOne**
- **Detect Microsoft Defender**
However, Zscaler Client Connector continues to evaluate device posture according to the configuration in the **Frequency (in Minutes)** field.
This feature is enabled by default. Contact Zscaler Support to disable this feature.
-
**Posture Type**: Complete the following steps, depending on the platforms you selected.
- [Certificate Trust](#Certificate-Trust)
- [File Path](#FilePath)
- [Registry Key](#Registry-Key)
- [Client Certificate](#Client-Certificate)
- [Firewall](#Firewall)
- [Full Disk Encryption](#Full-Disk-Encryption)
- [Domain Joined](#Domain-Joined)
- [Process Check](#Process-Check)
- [Detect Carbon Black](#Detect-Carbon-Black)
- [Detect CrowdStrike](#Detect-CrowdStrike)
- [CrowdStrike ZTA Score](#CrowdStrike-ZTA)
- [Detect SentinelOne](#Detect-SentinelOne)
- [Ownership Variable](#Ownership-Variable)
- [Unauthorized Modification](#Unauthorized-Modification)
- [Detect Microsoft Defender](#Detect-MS-Defender)
- [Detect Antivirus](#Detect-Antivirus)
- [OS Version](#OS-Version)
- [JAMF Detection](#JAMF-detection)
- [AzureAD Domain Joined](#azuread)
- [Server Validated Client Certificate](#Server-Validated-Client-Certificate)
- [CrowdStrike ZTA Device OS Score](#CrowdStrike-ZTA-Device-OS-Score)
- [CrowdStrike ZTA Sensor Setting Score](#CrowdStrike-ZTA-Sensor-Setting-Score)
- [Zscaler Client Connector Version](#zscaler-client-connector-version)
Not all device posture types work for all platforms. If you select a device that doesn't support a specific posture type, the posture type is unavailable.
- (Optional) Enter a **Device Posture Description**.
- Click **Save**.
After configuring the posture profiles, you can use these profiles to [configure access policies](/zpa/configuring-access-policies) in the ZPA Admin Portal and [add posture profile trust levels](/zscaler-client-connector/adding-zia-posture-profiles) for ZIA.
[]Applies to Windows, macOS, Linux, Android, or iOS. Select **Certificate Trust** from the drop-down menu and upload a certificate issued by an internal root Certificate Authority (CA) trusted by your organization's users. The user's device must trust the certificate to pass the posture validation check.
For iOS, the certificate must be trusted directly by the device. An intermediate certificate doesn’t work.
Zscaler accepts Base64-encoded .pem and .cer files, and you can upload any one of the following:
- A root CA certificate
- An intermediate certificate
- A client certificate
![Certificate Trust Device Posture Type](/downloads/z-app/policy-administration-settings/device-posture/configuring-device-posture-profiles-zpa/client-connector-certificate-trust-posture-type.png)
[]Applies to Windows or macOS. Select **File Path** from the drop-down menu and enter a file path that can be found on your users' systems. For example, you can enter: C:\Program Files(x86)\Example\AV.txt.
The user's device must have the specified file path to pass the posture validation check.
![File Path Device Posture Type](/downloads/z-app/policy-administration-settings/device-posture/configuring-device-posture-profiles-zpa/client-connector-file-path-posture-type.png)
If you choose more than one platform, the File Path option is not available. Instead, you must use the Certificate posture type.
[]Applies to Windows only. Select **Registry Key** from the **Posture Type** drop-down menu. Enter the registry key in the **Registry Key** field.
From the **Match Type **drop-down menu, select either **Path **or **Value**:
- If you select **Path**, ensure that the registry key begins with HKEY. For example, `\HKEY_CURRENT_USER\Software\Zscaler\App`.
- If you select **Value**, you must also complete the **Name **and **Data **fields. For example, if you enter the registry key `\HKEY_CURRENT_USER\Software\Zscaler\App`, you would enter `ZNW_State` in the **Name** field and `CONNECTING` in the **Data** field to describe that the service is connecting. To learn more, see [Zscaler Client Connector: Windows Registry Keys](/zscaler-client-connector/zscaler-app-registry-keys).
The app checks against the registry key **Path **or the **Value**. The user's device must have the specified registry key to pass the posture validation check. The registry key check runs in the user context. If your permissions prevent users from accessing the system keys (e.g., HKLM), you must create the registry key where users can access it.
![Registry Key Device Posture Type](/downloads/zscaler-client-connector/device-posture-profiles/configuring-device-posture-profiles/Registry_Key_resized.png)
[]Applies to Windows, macOS, Linux, and Android. For details on how to configure Linux for the Client Certificate, see [Configuring the Client Certificate Posture Check for Linux](/zscaler-client-connector/configuring-client-certificate-posture-check-linux).
As of Zscaler Client Connector version 1.14 for Android, Zscaler ended support for the Knox Admin and the Client Certificate posture type for Samsung Android devices. Zscaler recommends you remove the Client Certificate posture check for Samsung Android devices in the Zscaler Client Connector Portal. To learn more, see [End-of-Support for the Client Certificate Posture Check and Device Admin for Samsung Android Devices](/eos-eol/end-support-client-certificate-posture-check-and-device-admin-samsung-android-devices).
Select **Client Certificate** from the drop-down menu and upload a certificate issued by an internal root Central Authority (CA) trusted by your organization's users. The certificate must be in the user store at the endpoint, issued by the CA that matches the uploaded certificate in the posture profile. The user must have a private and public key pair issued by the specified CA to pass this posture validation check.
Zscaler accepts Base64-encoded .pem and .cer files, and you can upload any one of the following:
- A root CA certificate
- An intermediate certificate
After uploading a certificate, enable or disable the **Non-Exportable Private Key**. If enabled, Zscaler Client Connector must check if the certificate's private key can or cannot be exported. Posture validation fails if **Non-Exportable Private Key **is enabled and the key is exportable.
Optionally, enable **Perform CRL Check**. If enabled, Zscaler Client Connector can help detect whether the certificate was revoked. The Certificate Revocation List (CRL) contains digital certificates that were revoked by the issuing CA before their scheduled expiration date, and those certificates should no longer be trusted. If a certificate was revoked, the posture check fails.
Zscaler Client Connector for Windows checks the CRL that was downloaded from the CA server and cached by a Microsoft API. If you use Zscaler Client Connector version 4.8 and later for Windows, you can have Zscaler Client Connector download, validate, and cache the CRL locally based on a configurable cache interval (0 to 30 minutes). Zscaler recommends using this option only in these scenarios:
- The CRL server experiences instability due to fluctuating between reachable and unreachable states.
- The CRL server is hosted as a ZPA application which could lead to ambiguous caching behavior due to ZPA access expiration.
- You require frequent CRL downloads or granular control over caching intervals for near real-time validation.
Contact Zscaler Support to enable this feature.
For Windows and macOS only, enter a value in the **Client Certificate Template Information** field that matches the certificate issued by the uploaded root certificate.
![Client Certificate Device Posture Type](/downloads/zscaler-client-connector/device-posture-profiles/configuring-device-posture-profiles/zclient-connector-device-posture-client-certificate.png)
[]Applies to Windows or macOS. Select **Firewall** from the drop-down menu. Zscaler Client Connector checks the firewall status for all three firewall profiles: public, private, and domain. At least one of these profiles must be active to pass the posture validation check.
Zscaler Client Connector doesn't check for the presence of third-party firewalls. Third-party firewalls don't fulfill the posture check requirement.
![Firewall Posture Type](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/Client_Connector_PostureType_Firewall_650.png)
[]Applies to Windows, macOS, and Android. Also applies to Zscaler Client Connector version 1.4 and later for Linux. Select **Full Disk Encryption** from the drop-down menu. Zscaler Client Connector checks if the device has full disk encryption enabled or disabled. The user must have full disk encryption enabled to pass the posture validation check.
![Full Disk Encryption Posture TYpe](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/Client_Connector_PostureType_Full_Disk_Encryption_650.png)
For Linux only, provide a value in the **File Path** field to check whether or not the disk or the disk partition that contains the File Path is encrypted.
![Disk Encryption posture type for Linux](/downloads/client-connector/policy-administration-settings/device-posture/configuring-device-posture-profiles/linux%20disk%20encryption.png)
[]Applies to Windows or macOS. Select **Domain Joined** from the drop-down menu and enter the domain or workgroup to match. Zscaler Client Connector checks if the device is joined to the domain or workgroup. The user's device must have a matching domain to pass the posture validation check.
![Domain Joined Posture Type](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/Client_Connector_Domain_Joined.png)
[]Applies to Zscaler Client Connector version 2.1.2 and later for Windows or macOS or Zscaler Client Connector version 1.3 and later for Linux. Select **Process Check** from the drop-down menu. For **Process Path**, enter the name and absolute path for the process (e.g., `c:\folder\process.exe`). Do not use double quotes. For **Signer Certificate Thumbprint, **enter the unique identifier of the process signer certificate. You can add multiple thumbprints for a single Process Check by separating each thumbprint with a comma.
- [Locating the Signer Certificate Thumbprint for Windows](#win)
- [Locating the Signer Certificate Thumbprint for macOS](#macos)
![Process Check Posture Type](/downloads/z-app/policy-administration-settings/device-posture/configuring-device-posture-profiles-zpa/Client_Connector_Process_Check_1_0.png)
[]
In Windows Explorer:
- Go to **Program Files** > **Zscaler **> **ZSATunnel**.
- Right-click the **ZSATunnel** file and select **Properties**.
- Click the **Digital Signatures** tab.
- Select the signature from the list and click **Details**.
- Click **View Certificate**.
- Click the **Details **tab. Scroll down and click **Thumbprint**. The thumbprint displays in a window from which you can copy and paste it into the **Signer Certificate Thumbprint** field.
[]
In the terminal window:
- Extract the certificates associated with binary codesign -d --extract-certificates binarypath: (e.g., `codesign -d --extract-certificates /Library/CS/CSDaemon <binary path>`)
- Parse the certificate: `for ((certnumber=0 ; certnumber<=2; certnumber++)) ; do openssl asn1parse -in codesign${certnumber} -inform der -out codesign${certnumber}.der ; done`
- Convert to a PEM file: `for ((certnumber=0 ; certnumber<=2; certnumber++)) ; do openssl x509 -inform der -in codesign${certnumber}.der -out codesign${certnumber}.pem ; done`
- Extract the certificates using the following command: `openssl x509 -noout -sha1 -fingerprint -inform pem -in codesign0.pem`
You can change `-sha1` to `-sha256`.
- Remove the colons from the output.
[]This is only applicable if you’re using Zscaler Client Connector version 2.1.2 and later for Windows or macOS. Select **Detect Carbon Black**. The user must have Carbon Black running on the device to pass the posture validation check.
![Carbon Black Posture Type](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/Client_Connector_Carbon_Black.png)
The following signer certificate matching thumbprints are supported for the Carbon Black **RepMgr.exe** executable for Windows:
| Zscaler Client Connector version 3.5 and later for Windows |
| ---------------------------------------------------------- |
| 4d66d506976bde36ae01ab3335d501bec9fb9837f855a4a29ecefdd9ad04384ae3a099aff61d717f9033309926659b4346c496d44407d39e0487868cd9665dc3abce52eaf263dad3412c7cedb9e79b9dfce3566368d917acf28779b98d996f416fef1f2b |
For Zscaler Client Connector version 4.5 and later for Windows, if there are no matching thumbprints, the posture check still passes if Carbon Black is installed and turned on in Windows Security Center.
The next table displays the signer certificate matching thumbprints supported for the following Carbon Black binaries for macOS:
- `/Applications/Confer.app/Contents/MacOS/repmgr`
- `/Applications/VMware Carbon Black Cloud/repmgr.bundle/Contents/MacOS/repmgr`
- `/Library/SystemExtensions/<UUID>/com.vmware.carbonblack.cloud.se-agent.extension.systemextension/Contents/MacOS/se_agent`
The **UUID** varies depending on your system settings.
If you are using an older version of Zscaler Client Connector, look at the thumbprints of the Carbon Black release to ensure that the thumbprints are supported by the posture.
| **Zscaler Client Connector version 4.3 and later for macOS** |
| ------------------------------------------------------------ |
| 8F262B63E0DA232A95111C9E1428BBCE76E609B7B19EE7CB9B1FEA04F201BBF12F71EE54DC38EDDBD2C80F662EC15090DD442266DAE2AE5FF662A39BC591E0FF2F3BB7BD2E00C23D |
For Zscaler Client Connector version 4.3 and later for macOS, if there are no matching thumbprints, the posture check still passes if Carbon Black is installed and the process is running.
[]This is only applicable if you’re using Zscaler Client Connector version 2.1.2 and later for Windows or macOS. Select **Detect CrowdStrike**. The user must have CrowdStrike running on the device to pass the posture validation check.
![Detect CrowdStrike Device Posture Type](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/dectect_crowdstrike.png)
The following signer certificate matching thumbprints are supported for the CrowdStrike **CSFalconService.exe** executable for Windows:
| Zscaler Client Connector version 3.5 and later for Windows |
| ---------------------------------------------------------- |
| cd485eaadb584dcf911bb9dae6ecae1253f0530893324968ecd73a9570c347cf0c8ee4bc390d394838b7c74e37392713e436e19a2be053100115da880e2f50955c71c9a9b5e6f9c0ecb1c1b198249f4f9c4a4665abbcd3d4a8bffcd9251b21bb2ec6e341426510225a68b9260814230b37e289bfe0566f28ca5296e9d87044679d0b405104b8db2c8d56eb03b878d8eb696cf3d4505e2f6641c57af9062ec51a1935420a805a0cefebecdbe59a391a69db32eab316adfe3b79a93d4b1fa7b8e6b2c972c99bfdc84962c16976bfbbf57b8f8b588a043b4fb0bc294a6d |
For Zscaler Client Connector version 4.5 and later for Windows, if there are no matching thumbprints, the posture check still passes if Crowdstrike is installed and turned on in Windows Security Center.
The next table displays the signer certificate matching thumbprints supported for the following CrowdStrike binaries for macOS:
- `/Library/CS/falcond`
- `/Applications/Falcon.app/Contents/Resources/falcond`
- `/Library/SystemExtensions/<**UUID**>/com.crowdstrike.falcon.Agent.systemextension/Contents/MacOS/com.crowdstrike.falcon.Agent`
The `**UUID**` is different for every installation. For example: `/Library/SystemExtensions/7F3C861E-7137-4797-AA86-CFD764D1796F/com.crowdstrike.falcon.Agent.systemextension/Contents/MacOS/com.crowdstrike.falcon.Agent`
If you are using an older version of Zscaler Client Connector, look at the thumbprints of the CrowdStrike release to ensure that the thumbprints are supported by the posture.
| **Zscaler Client Connector 4.3 and later for macOS** |
| ---------------------------------------------------- |
| 475B2989BAE075A1F444B76ADAABE8EDF33A0ADFB7447A2DAE7B0C3016274ACBB55F7AA8A7349ACF5B45F61068B29FCC8FFFF1A7E99B78DA9E9C4635611E5B662C593A08FF58D14AE22452D198DF6C60 |
For Zscaler Client Connector version 4.3 and later for macOS, if there are no matching thumbprints, the posture check still passes if CrowdStrike is installed and the process is running.
[]This is only applicable if you’re using Zscaler Client Connector version 3.4 and later for Windows or macOS. Select **CrowdStrike ZTA Score**. The user must have CrowdStrike running on the device to pass the posture validation check.
Users must enable the CrowdStrike ZTA feature in CrowdStrike. Contact CrowdStrike Support to enable this feature.
Enter a score between `1` and `100`. This number represents a risk score that helps determine the security level of the device. The higher the number you designate, the more secure you consider the device. Zscaler Client Connector compares this number against an overall score (a combined score based on the device OS settings and sensor settings) assigned by CrowdStrike’s user agent. If that overall score is greater than or equal to the score you’ve entered, the posture check passes. If the overall score is less than the score you entered, the posture check fails. To learn more about the ZTA score, refer to the CrowdStrike documentation.
![CrowdStrike ZTA Score Device Posture Type](/downloads/zscaler-client-connector/end-user-guide/viewing-information-about-private-access-zscaler-client-connector/zscaler-client-connector-device-posture-crowdstrike-zta.png)
[]This is only applicable if you’re using Zscaler Client Connector version 2.1.2 and later for Windows or macOS. Select **Detect SentinelOne**. The user must have SentinelOne running on the device to pass the posture validation check.
![Sentinel One Posture Type](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-device-posture-profiles-zpa/Client_Connector_SentinelOne.png)
The following signer certificate matching thumbprints are supported for the SentinelOne **SentinelAgent.exe** executable for Windows:
| Zscaler Client Connector version 3.6 and later for Windows | Zscaler Client Connector version 3.5 and later for Windows |
| ---------------------------------------------------------- | ---------------------------------------------------------- |
| f1654692e31c02872d73507de97617fd6dc14c8c910b496dc984d3818001dbfe1a75cf75e46aef0e2b90394e9b094f067f84d9a0b15009d51fda20dd22C492673C2651B397AC13750978220A87E03CD569640f124bafc9a891fc4b51fcfd0ddf8785a6e55dfc737f10a570899baf8209e9e5cd4cfdfd6aed403e7374894c743e3ebd2ecc15f8a46091ff6a4d2349d742850cafb6f691b5d2b79b3d47576ec52a | f1654692e31c02872d73507de97617fd6dc14c8c910b496dc984d3818001dbfe1a75cf75e46aef0e2b90394e9b094f067f84d9a0b15009d51fda20dd |
For Zscaler Client Connector version 4.5 and later for Windows, if there are no matching thumbprints, the posture check still passes if SentinelOne is installed and turned on in Windows Security Center.
The next table displays the signer certificate matching thumbprints supported for the following SentinelOne binaries for macOS:
`/Library/Sentinel/sentinel-agent.bundle/Contents/MacOS/sentineld`
If you are using an older version of Zscaler Client Connector, look at the thumbprints of the SentinelOne release to ensure that the thumbprints are supported by the posture.
| **Zscaler Client Connector 3.7 and later for macOS** |
| ---------------------------------------------------- |
| CAF5A626546E84A2036913B07FCB835EB60D4F95c885b2ee5abf5815455f274990215f1b29514b49 |
For Zscaler Client Connector version 4.3 and later for macOS, if there are no matching thumbprints, the posture check still passes if SentinelOne is installed and the process is running.
[]Applies to Android or iOS. Select **Ownership Variable** from the drop-down menu. Enter a variable using an alphanumeric value no greater than 32 characters.
The user's device must have the variable to pass the posture validation check. Your device management solution pushes the variable to the device during installation.
The Ownership Variable must be set through mobile device management when deploying Zscaler Client Connector. For successful deployment of Zscaler Client Connector to your users’ devices, see the following articles:
- [Customizing Zscaler Client Connector with Install Options for Android](/zscaler-client-connector/deploying-zscaler-app-microsoft-intune-android#google-play-with-android-enterprise-enabled)
- [Customizing Zscaler Client Connector with Install Options for iOS](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-ios)
![Ownership Variable Device Posture Type](/downloads/z-app/policy-administration-settings/device-posture/configuring-device-posture-profiles-zpa/client-connector-ownership-variable-posture-type.png)
[]Applies to Android or iOS. Select **Unauthorized Modification** from the drop-down menu. Zscaler Client Connector checks for unauthorized modifications on the device, such as jailbreaking or rooting. The user's device must not have unauthorized modifications to pass the posture validation check.
![Unauthorized Modification Device Posture Type](/downloads/z-app/policy-administration-settings/device-posture/configuring-device-posture-profiles-zpa/client-connector-unauthorized-modification-posture-type.png)
If you are using Zscaler Client Connector version 1.5.2 for iOS or Zscaler Client Connector version 1.5.0 for Android, see [Using the Unauthorized Modification Device Posture Profile](/zscaler-client-connector/known-issues-device-posture-profiles) for known issues.
[]Applies to Zscaler Client Connector version 2.1.1 and later for Windows or macOS, or Zscaler Client Connector version 1.4 and later for Linux. Select **Detect Microsoft Defender**. The user must have Microsoft Defender Advanced Threat Protection running on the device to pass the posture validation check.
For Linux only, enter the executable path for the Microsoft Defender endpoint on Linux.
![Microsoft Defender Device Posture Type](/downloads/z-app/configuring-policy-and-administration-settings/device-posture/configuring-device-posture-profiles/MS%20Defender.png)
The next table displays the signer certificate matching thumbprints supported for the following Detect Microsoft Defender binaries for macOS:
`/Library/SystemExtensions/<UUID>/com.microsoft.wdav.epsext.systemextension/Contents/MacOS/epsext`
| **Zscaler Client Connector version 3.7 and later for macOS** |
| ------------------------------------------------------------ |
| 2ED71A71E4BFC746CBB0C0B1C80AADCE899A67F27D4DE827C9FA532C2C65684AD5DDB003231DDF9F |
[]This is only applicable if you’re using Zscaler Client Connector version 3.6 and later for Windows or macOS. Select **Detect Antivirus** from the drop-down menu.
For Windows, you can enter the antivirus name in the **AV Name **field and enable **Check if AV Definitions Are Up-to-Date**. When enabled, Zscaler Client Connector detects if an antivirus is running on the system. If you specify an antivirus name, the antivirus must be running on the system for the posture check to pass. If you leave the **AV Name** field blank, Zscaler Client Connector detects any antivirus running on the system.
For macOS, you must specify the antivirus name in the **AV Name** field. Include the system extension name as part of the antivirus name. You can use the command line tool `systemextensionsctl` to identify the complete name.
![Detect Antivirus for Device Posture Configuration on the Zscaler Client Connector portal](/downloads/zscaler-client-connector/device-posture-profiles/configuring-device-posture-profiles/clientconnector-configpostureprofile-detectantivirus.png)
[]Applies to Zscaler Client Connector version 3.6 and later for Windows or macOS, or Zscaler Client Connector 1.4 and later for Linux, or** **Zscaler Client Connector 3.7 and later for Android.** **Select **OS Version** from the drop-down menu.
For Windows** **only, select an edition from the **OS Editions** drop-down menu, click **Add OS **to add it, and then select a build from the **OS Build** drop-down menu. If the machine is running this version or later, then the posture check passes. You can add additional OS Editions if more are available after your initial OS selection.
![Detect OS for Device Posture Configuration ](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profiles-doc-50086/OS_Version_Windows.png)
For macOS only, select a version from the** OS Versions **drop-down menu, click **Add OS** to add it, and then enter the OS version. You can add additional OS versions if more are available after your initial OS selection.
![OS Version posture type macOS](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profiles-doc-50086/OS_version_macOS.png)
For Linux only, select a distribution from the **Linux Distributions** drop-down menu, click **Add OS **to add it, and then enter the OS version. You can add additional Linux distributions if more are available after your initial selection.
![Client Connector OS Version for Linux](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profiles-doc-50086/Linux_OS_Version.png)
For Android only, select an edition from the **OS Editions** drop-down menu, click **Add OS **to add it, and then click the **Calendar** icon to select a month for the patch date. You can add additional OS Editions if more are available after your initial OS selection.
![Client Connector Device Posture Android OS Version](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profiles-doc-50086/OS-Version_Android1.png)
[]Applies to Zscaler Client Connector version 4.3 and later for macOS.
- **JAMF Detection**: Zscaler Client Connector checks if JAMF is running on the device.
- **JAMF Risk Level**: Zscaler Client Connector checks for JAMF-provided risk levels. Choose from **Secure**, **Low**, **Medium**, or **High**.
If you are using JAMF Detection posture check, when removing an MDM profile from a device, the JAMF daemon might still be running. To ensure it is not running, on unenrollment, admins must add the command `sudo jamf -removeFramework` to JAMF Pro to completely remove the JAMF daemon from running on the system.
[]Applies to Windows only. Select **AzureAD Domain Joined** from the drop-down menu and then enter a globally unique identifier in the **Tenant Id** field. Zscaler Client Connector checks if the device is AzureAD Domain Joined to the specified Tenant Id.
A device can be only Domain Joined, only AzureAD Domain Joined, or both AzureAD Domain Joined and Domain Joined (i.e., hybrid join).
![AzureAD Domain-Joined](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profile-doc-49753/Device-Posture-AzureAD-Client_Connector.png)
[]Applies only to Zscaler Client Connector version 4.4 and later for Windows.
Select **Server Validated Client Certificate** from the drop-down menu and upload a CA certificate trusted by your organization's users. The client certificate must be either in the current user personal store or local computer personal store at the endpoint. The client certificate must be issued by the CA certificate uploaded in the posture profile.
For this posture validation check, the server sends a challenge to the client. After locating the private key and the root CA on the certificate chain, the client sends the signed challenge back to the server to pass the validation.
Zscaler accepts Base64-encoded .pem and .cer files, and you can upload any one of the following:
- A root CA certificate
- An intermediate certificate
After uploading a certificate, enable or disable the **Non-Exportable Private Key**. If enabled, Zscaler Client Connector must check if the certificate's private key can or cannot be exported. Posture validation fails if **Non-Exportable Private Key **is enabled and the key is exportable.
If you upload a large number of certificates (more than 50), the response from the server might take some time (around 10 seconds).
Enable the** Perform CRL Check **option to allow Zscaler Client Connector to help detect whether the certificate was revoked. The Certificate Revocation List (CRL) contains digital certificates that were revoked by the issuing CA before their scheduled expiration date, and those certificates should no longer be trusted. If a certificate was revoked, the posture check fails.
![Server Certificate Device Posture Type](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-device-posture-profiles-doc-56398/server-validated-client-certificate.png)
[]This is only applicable if you’re using Zscaler Client Connector version 4.6 and later for Windows or macOS. Select **CrowdStrike ZTA Device OS Score**. The user must have CrowdStrike running on the device to pass the posture validation check.
Users must enable the CrowdStrike ZTA feature in CrowdStrike. Contact CrowdStrike Support to enable this feature.
Enter a score between `1` and `100`. This number represents a risk score that helps determine the security level of the device. The higher the number you designate, the more secure you consider the device. Zscaler Client Connector compares this number against the OS score assigned by CrowdStrike’s user agent. If that overall score is greater than or equal to the score you’ve entered, the posture check passes. If the overall score is less than the score you entered, the posture check fails. To learn more about the OS score, refer to the CrowdStrike documentation.
![CrowdStrike ZTA Score Device Posture Type](/downloads/zscaler-client-connector/end-user-guide/viewing-information-about-private-access-zscaler-client-connector/zscaler-client-connector-device-posture-crowdstrike-os.png)
[]This is only applicable if you’re using Zscaler Client Connector version 4.6 and later for Windows or macOS. Select **CrowdStrike ZTA Sensor Setting Score**. The user must have CrowdStrike running on the device to pass the posture validation check.
Users must enable the CrowdStrike ZTA feature in CrowdStrike. Contact CrowdStrike Support to enable this feature.
Enter a score between `1` and `100`. This number represents a risk score that helps determine the security level of the device. The higher the number you designate, the more secure you consider the device. Zscaler Client Connector compares this number against the sensor setting score assigned by CrowdStrike’s user agent. If that overall score is greater than or equal to the score you’ve entered, the posture check passes. If the overall score is less than the score you entered, the posture check fails. To learn more about the sensor setting score, refer to the CrowdStrike documentation.
![CrowdStrike ZTA Score Device Posture Type](/downloads/zscaler-client-connector/end-user-guide/viewing-information-about-private-access-zscaler-client-connector/zscaler-client-connector-device-posture-crowdstrike-sensor.png)
[]Applies to Zscaler Client Connector version 4.8 and later for Windows. Select** Zscaler Client Connector Version** from the drop-down menu. Enter up to five versions in the Version field in a minimum two-version level to maximum 4-version level format. If you select **Exact Match**, the exact version number is required to pass the check.
You can enter only values 4.8 and higher (e.g., 4.8, 4.8.0.456, 4.8.0.789). The following table shows example results for different values:
| Values in Version Field | Exact Match | Passing Versions |
| ----------------------- | ----------- | ---------------- |
| 4.8 | Selected | Only 4.8.X.X versions |
| Cleared | All versions 4.8.X.X and later |
| 4.8.0.456, 4.8.0.789 | Selected | Only versions 4.8.0.456 and 4.8.0.789 |
| Cleared | All versions 4.8.0.456 and later |
![Zscaler Client Connector Version device posture](/downloads/zscaler-client-connector/device-posture-profiles/configuring-device-posture-profiles/zclient-connector-device-posture-client-connector-version.png)