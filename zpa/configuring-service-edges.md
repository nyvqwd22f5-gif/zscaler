# Configuring ZPA Private Service Edges
Source: https://help.zscaler.com/zpa/configuring-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1484481.pdf

Within the ZPA Admin Portal, you can add up to 100 ZPA Private Service Edges, 100 ZPA Private Service Edge groups, and 100 provisioning keys. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To add a new ZPA Private Service Edge:
- Go to **Configuration & Control** > **Private Infrastructure** > **Private Service Edge Management** > **Private Service Edges**.
-
Click **Add Private Service Edge**.
ZPA Private Service Edges that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Add Private Service Edge** window appears.
- In the **Add Private Service Edge** window:
- [1. Choose Key](#chkey)
- [2. Signing Certificate](#signcert)
- [3. Private Service Edge](#svcedgegroup)
- [4. Create Provisioning Key](#createkey)
- [5. Review](#review)
- [6. Review Documentation](#deploysvcedge)
[]The provisioning key is a secure random text string that you need to enter when you deploy the ZPA Private Service Edge on a platform. Each key is associated with a specific ZPA Private Service Edge group and functions like an ID for the ZPA Private Service Edge. You can create a provisioning key or choose an existing one.
After deployment, the ZPA Private Service Edge launches and makes initial contact with the ZPA cloud. It presents a key as its ID, allowing the ZPA cloud to verify that this is an authentic ZPA Private Service Edge and to identify which ZPA Private Service Edge group it belongs to. ZPA then automatically completes the deployment process.
On the **Choose Key** tab, choose one of the following options:
[See image.](#key_pic)
- [Choose an existing provisioning key](#existkey)
- [Create a new provisioning key](#newkey)
-
[]Select an existing provisioning key from the drop-down menu. You can click **Clear Selection** to remove any selections.
If you use an existing provisioning key, only keys that can be viewed or exported after creation appear in the drop-down menu.
- Click **Next**.
- When the **Review Documentation** tab appears, skip to [6. Review Documentation](/zpa/configuring-service-edges#deploysvcedge) below.
[]Click **Next**.
- []On the **Signing Certificate** tab, select the signing certificate that ZPA uses to sign certificates it issues to the ZPA Private Service Edge. If you need to generate a new enrollment certificate, see [Generating an Enrollment Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates).
Make sure the certificate used to enroll ZPA Private Service Edges has the same root certificate as the root certificate used by the enrollment certificate for enrolling App Connectors and Zscaler Client Connector.
[See image.](#signcert_pic)
- Click **Next**.
To learn more about certificates, see [About Certificates](/zpa/about-certificates).
[]On the **Private Service Edge Group** tab, choose one of the following options:
- [Select Private Service Edge Group](#selectgroup)
- [Add Private Service Edge Group](#addgroup)
- []Select an existing ZPA Private Service Edge group from the drop-down menu. You can search for a specific group or click **Clear Selection** to remove any selections. ZPA Private Service Edge groups can be associated with multiple provisioning keys. So, you can assign this ZPA Private Service Edge to an existing group that's already associated to a provisioning key.
[See image.](#selectsegroup_pic)
- Click **Next**.
- []Click **Add Private Service Edge Group** and enter the following information:
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the group.
- **Status**: Make sure **Enabled** is selected.
- **Publicly Accessible**: Choose if the ZPA Private Service Edge group with specific [trusted networks](/zscaler-client-connector/about-trusted-networks) mapping is also available publicly for all users outside of these trusted networks. It is important to ensure the ZPA Private Service Edge is reachable over a public IP address if you need remote users to be able to connect to it.
If the ZPA Private Service Edge has a public IP address or a published IP address set to a public IP address of a SNAT (i.e., firewall), you do not need to enable this field. It is already publicly accessible. If the ZPA Private Service Edge does not have either of those, set this to **Enabled**. You also need to specify a published domain for the ZPA Private Service Edge. For more information, see [Editing a Deployed ZPA Private Service Edge](/zpa/editing-deployed-service-edge).
When you disable **Publicly Accessible** without a trusted network, the IP address of the ZPA Private Service Edge is returned to the client for both on-premises and roaming users that are located closest to the ZPA Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this ZPA Private Service Edge, ensure it’s reachable over a public IP address.
- **Client Connector Trusted Networks**: Your organization's [trusted networks](/zscaler-client-connector/about-trusted-networks) that are mapped to the ZPA Private Service Edge group. This is used to prioritize ZPA Private Service Edges when users connect from those trusted networks. To learn more, see [About Trusted Networks](/zscaler-client-connector/about-trusted-networks).
- **Disaster Recovery**: Enable to designate the ZPA Private Service Edge group for disaster recovery. ZPA Private Service Edge groups that are designated for disaster recovery bypass the ZPA cloud to ensure business continuity in the event of a disaster scenario. Disaster recovery is disabled by default. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery) and [About Disaster Recovery Private Service Edge Groups](/zpa/about-disaster-recovery-service-edge-groups).
Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. To learn more, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
- **Private Cloud for Business Continuity**: Select a Private Cloud to associate with the ZPA Private Service Edge group for Business Continuity. In the event that the ZPA cloud isn't available, the ZPA Private Service Edges contact the Private Cloud Controllers associated with the Private Cloud for the Control channel, configuration updates, and logging. To learn more, see [Understanding Business Continuity](/zpa/understanding-business-continuity) and [About Private Clouds](/zpa/about-private-clouds).
- **Alternative Cloud Domain**: Select an Alternative Cloud Domain to override the default cloud domain for this ZPA Private Service Edge group. You can search for a specific cloud domain or click **Clear Selection** to remove a selection.
- **Persist Local Version Profile**: Enable if the Private Service Edge group should persist the local Version Profile. By default, **Disabled** is selected.
- **Version Profile**: Displays the current Version Profile. The default value is set to **Default**. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- **Private Service Edge Software Update Schedule**: Schedule the periodic software update for the group by selecting the day of the week and start time. You can search for a specific day of the week and start time or click **Clear Selection** to remove any selections.
- **Private Service Edge Location**: Enter the location where the ZPA Private Service Edges in the group are set up. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, and **Location Address** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
- **Public Service Edge Proximity Override**: Enable to allow ZPA Private Service Edge groups within the specified distance to be prioritized over a closer ZPA Public Service Edge.
-
**Distance**: Enter the maximum distance to ZPA Private Service Edge groups that would override a ZPA Public Service Edge (select either** Miles** or **Kms** (kilometers) in the drop-down menu). A valid positive number (maximum value is 25,000 miles or 40,233.6 kilometers) not exceeding two decimal places (e.g., 10.05) is required for distance and units must be selected.
If multiple ZPA Private Service Edge groups are configured with the same location (i.e., latitude and longitude), then the **Distance** from the ZPA Private Service Edge group that has the highest value is applied for all ZPA Private Service Edge groups.
[See image.](#createsegroup_pic)
- Click **Next**.
- []On the **Create Provisioning Key** tab:
- **View or Export Provisioning Key After Creation:** Select this** **option if you want to view, copy, or download the provisioning key after creation. This option is enabled by default. If disabled, you cannot enable this option at a later time.
- **Name**: Enter a name for the provisioning key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
This name is automatically assigned as a prefix for the name of each ZPA Private Service Edge enrolled with it. This means that all ZPA Private Service Edges in a given ZPA Private Service Edge group use the same prefix in its name.
To help distinguish between the different ZPA Private Service Edges in a group, each ZPA Private Service Edge also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth ZPA Private Service Edge to be enrolled with the key. For example, if you enter AWS Oregon as a provisioning key name in this step, the first ZPA Private Service Edge you enroll with this key is named AWS Oregon-1. The next ZPA Private Service Edge you enroll with the same key is named AWS Oregon-2, and so on.
- **Maximum Reuse of Provisioning Key**: Enter the maximum number of instances where this key can be used to enroll a ZPA Private Service Edge. Zscaler recommends setting this option to the number of App Connectors you plan to deploy immediately, to reduce the possibility of compromise. After adding the ZPA Private Service Edge, [this number can be modified](/zpa/edit-service-edge-provisioning-key).
The **Instances of Provisioning Key Reuse** field cannot be modified. ZPA tracks the number of ZPA Private Service Edges enrolled in this ZPA Private Service Edge group and automatically displays the number in this field. This helps ensure that keys are not being used improperly by unknown parties to enroll ZPA Private Service Edges.
[See image.](#provkey_pic)
- Click **Next**.
- []On the **Review** tab, review your configuration settings and any warnings.
[See image.](#review_pic)
- Click **Save**.
- []On the **Review Documentation** tab:
- **Copy Provisioning Key**: Copy the ZPA Private Service Edge provisioning key. You will need to enter this key when you deploy the ZPA Private Service Edge to a platform. You can click the **Copy** icon to copy the key to your clipboard.
- **Choose Platform**: Choose the platform you want to deploy your ZPA Private Service Edge on, and follow the instructions that appear. To learn more, see the [ZPA Private Service Edge Deployment Guide](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your supported platform.
[See image.](#reviewdoc_pic)
- Click **Done**.
[]![Add Private Service Edge Window within ZPA Admin Portal](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/Step%201.png)
[]![Enrollment Certificate tab in Add Private Service Edge Window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/Step%202.png)
[]![Private Service Edge Group tab in Add Private Service Edge Window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/Step%203%20Select%20PSE%20Group.png)
[]![Add Service Edge Group tab in Add Service Edge Window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/Add%20PSE_0.png)
[]![Create Provisioning Key tab in Add Private Service Edge window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/zpa-addserviceedge-createprovisioningkey_2.png)
[]![Review tab in Add Private Service Edge window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/zpa-pse-review-page_0.png)
[]![Review Documentation tab in Add Private Service Edge window](/downloads/zpa/private-service-edge-management/private-service-edge/configuring-service-edges/Step%206.png)