# Configuring a Version Profile
Source: https://help.zscaler.com/zpa/configuring-version-profile
PDF: https://help.zscaler.com/pdf/com/en/1485026.pdf

A version profile can be used to tie an App Connector group, ZPA Private Service Edge group, or Private Cloud Controller group to a specific build. Configuring a version profile allows you to select a desired build for that profile; the version profile can then be assigned to one or more App Connector group, ZPA Private Service Edge groups, or Private Cloud Controller groups. This allows you to upgrade all App Connector groups, ZPA Private Service Edge groups, or Private Cloud Controller groups to a specific build, or take a controlled approach to upgrade select App Connector groups, ZPA Private Service Edge groups, or Private Cloud Controller groups to a specific build.
The version profile is configured in the ZPA Admin Portal on the following pages:
- App Connector Groups (**Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **App Connector Groups**)
- Private Service Edge Groups (**Configuration & Control** > **Private Infrastructure** > **Private Service Edge Management** > **Private Service Edge Groups**)
- Private Cloud Controller Groups (**Configuration & Control** > **Private Infrastructure** > **Business Continuity Management** > **Private Cloud Controller Groups**)
To configure a version profile:
- [Click the Version Profile Icon in the App Connector Group, Service Edge Group, or Private Cloud Controller Group Pages](#ClickingVersionProfile)
- [Edit the Individual App Connector Group, Private Service Edge Group, or Private Cloud Controller Group](#EditingIndividual)
Zscaler recommends the following version profile best practices to balance stability and new features across your App Connector groups, ZPA Private Service Edge groups, and Private Cloud Controller groups:
- For critical App Connector groups, ZPA Private Service Edge groups, or Private Cloud Controller groups that are vital to the function and operations of an organization, use the Previous Default version profile.
- For App Connector groups, ZPA Private Service Edge groups, or Private Cloud Controller groups that require the latest software updates and features, use the New Release version profile.
- []Go to the App Connector Groups, Private Service Edge Groups, or Private Cloud Controller Groups page in the ZPA Admin Portal.
- Click **Version Profile**.
![Clicking the version profile button in the Admin Portal](/downloads/zpa/app-connector-management/app-connector-groups/configuring-version-profile/zpa-click-version-profile_1.png)
The **Customer Version Profile** window appears.
- In the **Customer Version Profile** window, click the **Choose a Version Profile** drop-down menu and select the desired profile:
- **Default**: The cloud-wide stable and default build.
- **Previous Default**: The cloud-wide previous stable and default build. Provides a rollback ability.
- **New Release**: The latest cloud-wide released build.
- **Custom**: A specialized build released only to help resolve issues. Zscaler Support provides custom version profiles to address and debug issues. Custom version profiles might not be visible in the ZPA Admin Portal.
[See image.](#SeeImage)
An App Connector, ZPA Private Service Edge, or Private Cloud Controller build becomes a part of the default version profile once the respective profile is stable enough to push to a majority of users.
- Choose whether you want to force update the App Connector group, ZPA Private Service Edge group, or Private Cloud Controller group version profiles that have** Persist Local Profile** enabled at the App Connector group, Service Edge group, or Private Cloud Controller level. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors), [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges), and [Configuring Private Cloud Controllers](/zpa/configuring-private-cloud-controllers).
- Click **Save**.
In the scenario where a Cloud stability fix or potential staged rollout is required, Zscaler automatically assigns a build to a profile. This is denoted by the Zscaler Assigned text below the B feature. When Zscaler assigns the build for the profile, the version profile and force update features are disabled.
[See image](#SeeImage3)
The **Zscaler Assigned** version profile is displayed under the **Version Profile** feature for individual App Connector groups, ZPA Private Service Edge groups, and Private Cloud Controller groups.
After the **Zscaler Assigned** version profile is deactivated, individual App Connector groups, ZPA Private Service Edge groups, and Private Cloud Controller groups are reverted to the default version profile and cannot be reverted to the previous state of the build.
- []Go to the App Connector Groups, Private Service Edge Groups, or Private Cloud Controller Groups page in the ZPA Admin Portal.
- Click the **Edit **icon of the App Connector group, Private Service Edge group, or Private Cloud Controller group you want to configure the version profile for.
- In the **Edit App Connector Group** window, **Edit Private Service Edge Group** window, or **Edit Private Cloud Controller** window, select **Enabled** under **Persist Local Profile**.
- Click the **Version Profile **drop-down menu and select the desired profile:
- **Default**: The cloud-wide stable and default build.
-
**Previous Default**: The cloud-wide previous stable and default build. Provides a rollback ability.
If you select **Previous Default**, the App Connectors, ZPA Private Service Edges, or Private Cloud Controllers under the related App Connector group, ZPA Private Service Edge group, or Private Cloud Controller group are updated weekly.
-
**New Release**: The latest cloud-wide released build.
If you select **New Release**, the App Connectors, ZPA Private Service Edges, or Private Cloud Controllers under the related App Connector group, ZPA Private Service Edge group, or Private Cloud Controller groups are updated daily.
- **Custom**: A specialized build released only to help resolve issues. Zscaler Support provides custom version profiles to address and debug issues. Custom version profiles might not be visible in the ZPA Admin Portal.
[See image.](#SeeImage2)
An App Connector, ZPA Private Service Edge, or Private Cloud Controller build becomes a part of the default version profile once the respective profile is stable enough to push to a majority of users.
- Click **Save**.
The** Zscaler Assigned** version profile is displayed under the **Version Profile** feature for the specific App Connector groups, ZPA Private Service Edge groups, and Private Cloud Controller groups which have been selected by Zscaler.
[See image](#SeeImage4)
Admins can still override the version profile. However, Zscaler recommends the version profile is not changed when **Force update the version profiles with persist local profile** is enabled.
After the **Zscaler Assigned** version profile is deactivated, individual App Connector groups, ZPA Private Service Edge groups, and Private Cloud Controller groups are reverted to the default version profile and cannot be reverted to the previous state of the build.
[]![Choose a Version Profile window in the Admin Portal](/downloads/zpa-version-profile-window-admin-portal.png)
[]![Editing a Version Profile in the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connector-groups/configuring-version-profile/zpa-select-version-profile-for-appConnector-privateServiceEdge.png)
[]![Zscaler Assigned Version Profile at the customer level](/downloads/zpa-zscaler-assigned-version-profile-customer.png)
[]![Zscaler Assigned Version Profile at the App Connector and Service Edge Group level](/downloads/zpa-zscaler-assigned-version-profile-individual.png)