# Deploying Digital Experience Monitoring With Workspace ONE UEM for iOS
Source: https://help.zscaler.com/unified/deploying-digital-experience-monitoring-workspace-one-uem-ios
PDF: https://help.zscaler.com/pdf/com/en/1530892.pdf

This guide is for admins only. If you are an end user, contact your organization’s administrator for deployment-related details.
With Workspace ONE Unified Endpoint Management (UEM), you can configure and deploy Digital Experience Monitoring for iOS devices. Before following this guide, ensure that Zscaler Client Connector is installed on your device. To learn more, see [Deploying Zscaler Client Connector with Workspace ONE UEM for iOS](/unified/deploying-zscaler-client-connector-workspace-one-uem-ios).
This deployment guide applies to devices running iOS version 16 and later.
To deploy Digital Experience Monitoring with Workspace ONE UEM for iOS devices:
- In the **Resources** section, go to **Profiles & Baselines**.
[See image.](#add-profile)
- Click **Add **> **Add Profile**.
- On the **Add Profile** page, click **iOS** and then **Device Profile**.
- Enter a name for your profile.
- Go to the **Custom Settings **section.
- Click **Add**.
[See image.](#custom-settings)
- In the **Custom Settings** box, copy and paste the following XML text. You can customize the `ContentFilterUUID` and `PayloadIdentifier` strings.
`<dict>
<key>ContentFilterUUID</key>
<string>6A53E317-8C38-42D6-9A49-BD2970F3A42A</string>
<key>FilterSockets</key>
<true />
<key>FilterType</key>
<string>Plugin</string>
<key>Organization</key>
<string>Zscaler</string>
<key>PayloadDescription</key>
<string>Zscaler ZDX Configuration</string>
<key>PayloadDisplayName</key>
<string>Zscaler ZDX Configuration</string>
<key>PayloadIdentifier</key>
<string>com.apple.webcontent-filter.E889893A-0185-422A-AC8F-797D4AA2766F</string>
<key>PayloadOrganization</key>
<string>Zscaler</string>
<key>PayloadType</key>
<string>com.apple.webcontent-filter</string>
<key>PayloadUUID</key>
<string>E889893A-0185-422A-AC8F-797D4AA2766F</string>
<key>PayloadVersion</key>
<integer>1</integer>
<key>PluginBundleID</key>
<string>com.zscaler.zscaler</string>
<key>UserDefinedName</key>
<string>Zscaler ZDX Configuration</string>
</dict>`
- Click **Next**.
- Assign groups.
- Click **Save & Publish**.
[See image.](#assignment)
To map a third-party app with the ZDX Configuration Profile created in the previous section:
- In the Resources section, go to **Apps** > **Native** > **Public** > **Add Application**.
[See image.](#native)
- In the **Add Application** section:
- **Managed By**: Enter the entity that manages the application. For example, `Zscaler`.
- **Platform**: Select **Apple iOS**.
- **Source**: Select **Search App Store**.
- **Name**: Enter the name of the application. For example, `Firefox`. You can choose any third-party application that you want.
[See image.](#add-application)
- Click **Next**.
- **Select** the application.
[See image.](#select-application)
- Click **Save & Assign**.
[See image.](#save-application)
- In the **Distribution** section, provide a name and assign groups.
[See image.](#distribution)
- In the **Restrictions** section, enable the** Managed Access **and **Make App MDM Managed if User Installed** options.
[See image.](#restrictions)
- In the **Tunnel & Other Attributes **section, configure `ContentFilterUUID` with the value `6A53E317-8C38-42D6-9A49-BD2970F3A42A`. The ContentFilterUUID value must match with the value in the XML text in the previous section.
[See image.](#tunnel)
- Click **Save**.
- Review the assignment and click **Save**.
[See image.](#review-assignments)
- In the next window, click **Publish**.
[See image.](#publish)
To verify that the profile is pushed to the device correctly, go to device **Settings **> **General** > **VPN & Device Management** > **Content Filter**. The Zscaler Content Filter shows as running. Clicking on the filter shows the apps associated with the filter.
[See image.](#content-filter-running)
[]![Add profile ](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Profiles.png)
[]![Copy paste XML in custom settings](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Custom-Settings.png)
[]![Add the assignment](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Assignments.png)
[]![Add a native application](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Native.png)
[]![Add the application](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Add-Application.png)
[]![Select the application](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Select-Application.png)
[]![Save and assign application](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Save-Application.png)
[]![Distribution section](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Distribution.png)
[]![Restrictions section](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Restrictions.png)
[]![Tunnel and attributes section](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Tunnel.png)
[]![Review the assigned application](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Review-Assignments.png)
[]![Publish the application ](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Publish.jpg)
[]![Content Filter is running](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZSClient-Connector-WorkSpaceONE-ZDX-iOS-Content-Filter-Running_0.png)
Open the Zscaler Client Connector app on your iOS device to see the Digital Experience Monitoring service running.
[See image.](#zdx-app)
[]![ZDX on Client Connector](/downloads/client-connector/downloading-deployment/deploying-zscaler-digital-experience-zdx-workspace-one-uem-ios/ZscalerClientConnector-ZDX-app.jpg)