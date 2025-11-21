# Configuring App Connectors
Source: https://help.zscaler.com/unified/configuring-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496026.pdf

Within the Admin Portal, you can create App Connectors, App Connector groups, and provisioning keys. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
To add a new App Connector:
- Go to the **App Connectors** page (Infrastructure > Private Access > Component > App Connectors).
-
Click **Add App Connector**.
App Connectors that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Add App Connector **window appears.
- In the **Add App Connector** window that appears:
- [1. Choose Key](#ck)
- [2. Signing Certificate](#sc)
- [3. App Connector Group](#cg)
- [4. Create Provisioning Key](#pk)
- [5. Review](#tab5)
- [6. Review Documentation](#vm)
[]Create a provisioning key or choose an existing one. The provisioning key is a secure random text string that you need to enter when you deploy the App Connector on a platform. Each key is associated with a specific App Connector group and functions like an ID for the App Connector.
After deployment, the App Connector launches and makes initial contact with the cloud. It presents a key as its ID, allowing the cloud to verify that this is an authentic App Connector and to identify which App Connector group it belongs to. Private Applications then automatically completes the deployment process.
On the **Choose Key** tab, choose one of the following options:
[See image.](#seeimage1)
- [Choose an Existing Provisioning Key](#choosekey)
- [Create a New Provisioning Key](#createkey)
[]![Add App Connector Window within Admin Portal](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector.png)
- []Select an existing provisioning key from the drop-down menu. You can click **Clear Selection** to remove any selections.
[See image.](#seeimage8)
- Click **Next**.
- When the **Review Documentation** tab appears, skip to [6. Review Documentation](/unified/configuring-app-connectors#vm) below.
[]![Add App Connector Window with Choose an existing provisioning key selected](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-existingkey.png)
[]Click **Next**.
- []On the **Signing Certificate** tab, from the drop-down menu, select the certificate that ZPA uses to sign certificates it issues to the App Connector. If you need to generate a new enrollment certificate, see [Generating an Enrollment Certificate](/unified/generating-zscaler-issued-enrollment-ca-certificates).
[See image.](#seeimage2)
- Click **Next**.
To learn more about certificates, see [About Certificates](/unified/understanding-certificates).
[]![Add App Connector window with Choose a certificate drop-down menu](/downloads/zpa/app-connector-management/app-connectors/about-connectorprovisioningwizard/zpa-add-app-connector-signing-certificate.png)
[]On the **App Connector Group** tab, choose one of the following options:
[See image.](#seeimage9)
- [Select App Connector Group](#selectconnectorgroup)
- [Add App Connector Group](#createconnectorgroup)
[]![Add App Connector window with App Connector Group tab selected ](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-conngrp.png)
- []Select an existing App Connector group from the drop-down menu. You can search for a specific group or click **Clear Selection** to remove any selections. App Connector groups can be associated with multiple provisioning keys. So, you can assign this App Connector to an existing group that's already associated to a provisioning key.
- Click **Next**.
- []Click **Add App Connector Group**:
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Make sure **Enabled** is selected.
-
**DNS Resolution Option**: Enable the necessary interface for DNS resolution checks. If the App Connectors assigned to that App Connector group should perform DNS resolution checks for applications using only IPv4, select **IPv4**. If the App Connectors assigned to the App Connector group should perform DNS resolution checks for applications using only IPv6, select **IPv6**. If you select **IPv4 and IPv6**, both interfaces can perform resolution checks for applications. The App Connector must have the corresponding interface or interfaces enabled for the DNS resolution checks to work, and the [servers](/unified/about-servers) hosting your applications must support the selected interface or interfaces. By default, **IPv4 and IPv6** is selected.
Select the **IPv6** option only if you have end-to-end IPv6 support.
- **TCP Quick Acknowledgement**: Enable TCP Quick Acknowledgement for the App Connector group to perform TCP Quick Ack for applications. TCP Quick Acknowledgement is used to improve performance of applications that use specific protocols (e.g., Server Message Block Protocol).
- **Description**: (Optional) Enter a description for the group.
-
**Disaster Recovery**: Enable to designate the App Connector group for disaster recovery. App Connector groups that are designated for disaster recovery bypass the cloud to ensure business continuity in the event of a disaster scenario. The App Connector group designated for disaster recovery must be associated with a server group that serves an application segment designated for disaster recovery. Disaster recovery is disabled by default. To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery) and [About Disaster Recovery App Connector Groups](/unified/about-disaster-recovery-app-connector-groups).
Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
-
**Disable AppProtection**: Select **Yes** to disable AppProtection for the App Connector group. By default, **No** is selected, meaning that AppProtection is enabled for the new App Connector group. If enabled, the App Connector Group with its associated App Connectors and applications can be inspected and managed via AppProtection Profiles. To learn more, see [About AppProtection Profiles](/unified/about-appprotection-profiles).
The Disable AppProtection option is displayed if your account has this feature enabled. If the feature isn’t enabled, the Disable AppProtection option is not shown.
- **Private Cloud for Business Continuity**: Select a Private Cloud to associate with the App Connector group for Business Continuity. In the event that the cloud isn't available, the associated Private Cloud provides limited support. To learn more, see [Understanding Business Continuity](/unified/understanding-business-continuity) and [About Private Clouds](/unified/about-private-clouds).
- **App Connector Allow List**: Enter the IP address or subnet of a deployed App Connector group to allow the App Connector group on a specific IP. This feature is used to add a layer of security to the App Connector enrollment process, in addition to the provisioning key and signing certificate. Both IPv4 and IPv6 IP addresses are supported. If the App Connector group is deployed in a subnet, then the subnet prefix notation can be used. For example, if the App Connector groups are deployed on 10.80.1.18 and 10.80.1.19, then the IP address can be defined as 10.80.1.0/24. You can search for a specific IP address or subnet, edit an IP address or subnet by clicking the **Edit **icon, delete an IP address or subnet by clicking the **Delete **icon, or click **Remove All** to remove all IP addresses or subnets.
This feature is in limited availability. To learn more, contact Zscaler Support. Consider the following when entering an IP address for the App Connector Allow List:
- App Connector enrollment stays pending if the App Connector IP address is not configured in the App Connector Allow List field. For example, a user configures 10.1.1.0/30 as the IP address for the App Connector Allow List. This means the App Connector Group can only have two App Connectors, and the App Connectors in this group can only use 10.1.1.1 and 10.1.1.2 as the IP addresses.
- If the IP address of the App Connector group changes due to Dynamic Host Configuration Protocol (DHCP) or other network changes, then the App Connector groups fail to enroll.
- If the App Connector is configured with a static IP, do not change the IP address unless you update the App Connector Allow List entry. If you want to add a new App Connector to the group, the App Connector Allow List must be updated so that the new App Connector can successfully enroll.
- **Persist Local Version Profile**: Enable if the App Connector group should persist the local Version Profile. By default, Disabled is selected.
- **Version Profile**: Displays the current Version Profile. The default value is set to Default. To learn more, see [Configuring a Version Profile](/unified/configuring-version-profile).
- **App Connector Software Update Schedule**: Schedule the periodic App Connector software update for the group by selecting the day of the week and start time. You can search for a specific day of the week and start time, or click **Clear Selection** to remove any selections.
- **App Connector Location**: Enter the location where the App Connectors in the group are set up. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, and **Location Address** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
[See image.](#seeimage4)
- Click **Next**.
[]![Add App Connector window in Add App Connector Group tab](/downloads/zpa/app-connector-management/app-connectors/about-connectorprovisioningwizard/Add%20App%20Connector.png)
- []On the **Create Provisioning Key **tab:
- **View or Export Provisioning Key After Creation**: Select this option if you want to view, copy, or download the provisioning key after creation. This option is enabled by default. If disabled, you cannot enable this option at a later time.
- **Name**:** **Enter a name for the provisioning key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
This name is automatically assigned as a prefix for the name of each App Connector enrolled with it. Meaning that all App Connectors in a given App Connector group use the same prefix in its name.
To help distinguish between the different App Connectors in a group, each App Connector also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth App Connector to be enrolled with the key. For example, if you enter AWS Oregon as a provisioning key name in this step, the first App Connector you enroll with this key is named AWS Oregon-1. The next App Connector you enroll with the same key is named AWS Oregon-2, and so on.
- **Maximum Reuse of Provisioning Key**:** **Enter the maximum number of instances where this key can be used to enroll an App Connector. To reduce the possibility of compromise, Zscaler recommends setting this option to the number of App Connectors you plan to deploy immediately. After adding the App Connector, [this number can be modified](/zpa/about-connectorprovisioning/edit).
The **Instances of Provisioning Key Reuse** field cannot be modified. The number of App Connectors enrolled in this App Connector group is tracked and the number is automatically displayed in this field. This helps ensure that keys are not being used improperly by unknown parties in order to enroll App Connectors.
[See image](#seeimage5)
- Click **Next**.
[]![Add App Connector window in Create Provisioning Key tab](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-creareprovisioningkey_0.png)
- []On the **Review** tab, review your configuration settings.
[See image.](#seeimage6)
- Click **Save**.
[]![Add App Connector window in Review tab](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-review_0.png)
- []On the **Review Documentation** tab:
- **Copy Provisioning Key**: Copy the App Connector provisioning key. You need to enter this key when you deploy the App Connector to a platform. You can click the **Copy **icon to copy the key to your clipboard.
- **Review Documentation**: Choose the platform you want to deploy your App Connector on, and follow the instructions that appear. To learn more, see the [App Connector Deployment Guide](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms) for your supported platform.
[See image.](#seeimage7)
- Click **Done**.
[]![Add App Connector window in Review Documentation tab](/downloads/zpa/app-connector-management/app-connectors/configuring-app-connectors/zpa-addconnector-reviewdocs.png)