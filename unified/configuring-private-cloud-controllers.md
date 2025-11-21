# Configuring Private Cloud Controllers
Source: https://help.zscaler.com/zpa/configuring-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1507131.pdf

Within the ZPA Admin Portal, you can create Private Cloud Controllers, Private Cloud Controller groups, and provisioning keys. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To add a new Private Cloud Controller:
- Go to **Configuration & Control** > **Business Continuity** > **Business Continuity Management** > **Private Cloud Controllers**.
-
Click **Add**.
Private Cloud Controllers that are managed by Zscaler are read only and cannot be configured, edited, or deleted. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
The **Add Private Cloud Controller** page appears.
- On the **Add Private Cloud Controller** page:
- [1. Choose Key](#ck)
- [2. Signing Certificate](#sc)
- [3. Private Cloud Controller Group](#cg)
- [4. Create Provisioning Key](#pk)
- [5. Review](#tab5)
- [6. Review Documentation](#vm)
[]Create a provisioning key or choose an existing one. The provisioning key is a secure random text string that you need to enter when you deploy the Private Cloud Controller on a platform. Each key is associated with a specific Private Cloud Controller group and functions like an ID for the Private Cloud Controller.
After deployment, the Private Cloud Controller launches and makes initial contact with the ZPA cloud. It presents a key as its ID, allowing the ZPA cloud to verify that this is an authentic Private Cloud Controller and to identify which Private Cloud Controller group it belongs to. ZPA then automatically completes the deployment process.
On the **Choose Key** page, choose one of the following options:
[See image.](#seeimage1)
- [Choose an Existing Provisioning Key](#choosekey)
- [Create a New Provisioning Key](#createkey)
[]![Choosing or Creating a Provisioning Key in the Add Private Cloud Controller Page](/downloads/zpa/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step1-choose-key.jpg)
-
[]Select an existing provisioning key from the drop-down menu. You can click **Clear **to remove any selections.
If you select an existing provisioning key, only keys that can be viewed or exported after creation appear in the drop-down menu.
[See image.](#seeimage8)
- Click **Next**.
- When the **Review Documentation** page appears, skip to [6. Review Documentation](/zpa/about-connectorprovisioningwizard#vm).
[]![Choosing an Existing Provisioning Key in the Add Private Cloud Controller Page](/downloads/zpa/business-continuity-management/private-cloud-controllers/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step1-choose-existing-pkey.png)
[]Click **Next**.
- []On the **Signing Certificate** page, select the certificate from the drop-down menu that ZPA uses to sign certificates it issues to the Private Cloud Controller. If you need to generate a new enrollment certificate, see [Generating an Enrollment Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates).
[See image.](#seeimage2)
- Click **Next**.
To learn more about certificates, see [Understanding Certificates](/zpa/understanding-certificates).
[]![Selecting a Signing Certificate in the Add Private Cloud Controller Page](/downloads/zpa/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step2-choose-cert.jpg)
[]On the **Private Cloud Controller Group** page, choose one of the following options:
[See image.](#seeimage9)
- [Select Private Cloud Controller Group](#selectpccgroup)
- [Add Private Cloud Controller Group](#createpccgroup)
[]![Selecting or Adding a Private Cloud Controller Group](/downloads/zpa/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step3-select-add-group.jpg)
- []Select an existing Private Cloud Controller group from the drop-down menu. You can search for a specific group, or click **Clear **to remove any selections. Private Cloud Controller groups can be associated with multiple provisioning keys. So, you can assign this Private Cloud Controller to an existing group that's already associated to a provisioning key.
- Click **Next**.
-
[]Click **Add Private Cloud Controller Group**:
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Ensure **Enabled** is selected.
- **Description**: (Optional) Enter a description for the group.
- **Private Cloud for Business Continuity**: Select the Private Cloud to which this Private Cloud Controller group should belong to.
- **Persist Local Version Profile**: Enable if the Private Cloud Controller group should persist the local Version Profile. By default, **Disabled **is selected.
- **Version Profile**: Displays the current Version Profile. The default value is set to **Default**. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- **Private Cloud Controller Software Update Schedule**: Schedule the periodic Private Cloud Controller software update for the group by selecting or searching for the day of the week and start time.
- **Private Cloud Controller Location**: Enter the location where the Private Cloud Controllers in the group are set up. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, and **Location Address** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country** **Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
[See image.](#seeimage4)
- Click **Next**.
[]![Adding a Private Cloud Controller Group within the Add Private Cloud Controller Page](/downloads/zpa/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step3-add-group.jpg)
- []On the **Create Provisioning Key **page:
- **View or Export Provisioning Key After Creation:** Select this** **option if you want to view, copy, or download the provisioning key after creation. This option is enabled by default. If disabled, you cannot enable this option at a later time.
-
**Name**: Enter a name for the provisioning key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
This name is automatically assigned as a prefix for the name of each Private Cloud Controller enrolled with it. Meaning that all Private Cloud Controllers in a given Private Cloud Controller group use the same prefix in its name.
To help distinguish between the different Private Cloud Controllers in a group, each Private Cloud Controller also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth Private Cloud Controller to be enrolled with the key. For example, if you enter `AWS Oregon` as a provisioning key name in this step, the first Private Cloud Controller you enroll with this key is named `AWS Oregon-1`. The next Private Cloud Controller you enroll with the same key is named `AWS Oregon-2`, and so on.
- **Maximum Reuse of Provisioning Key**: Enter the maximum number of instances where this key can be used to enroll a Private Cloud Controller. After adding the Private Cloud Controller, this number can be modified.
The **Instances of Provisioning Key Reuse** field cannot be modified. ZPA tracks the number of Private Cloud Controllers enrolled in this Private Cloud Controller group and automatically displays the number in this field. This helps ensure that keys are not being used improperly by unknown parties to enroll Private Cloud Controllers.
[See image](#seeimage5)
- Click **Next**.
[]![Creating a Provisioning Key in the Add Private Cloud Controller Page](/downloads/zpa/business-continuity-management/private-cloud-controllers/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step4-create-pkey.png)
- []On the **Review** page, review your configuration settings.
[See image.](#seeimage6)
- Click **Save**.
[]![Reviewing the Details in the Add Private Cloud Controller Page](/downloads/zpa/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-page-step5-review.jpg)
- []On the **Review Documentation** page:
- **Copy Provisioning Key**: Copy the Private Cloud Controller provisioning key. You need to enter this key when you deploy the Private Cloud Controller to a platform. You can click the **Copy** icon to copy the key to your clipboard.
- **Review Documentation**: Choose the platform you want to deploy your Private Cloud Controller on, and follow the instructions that appear.
[See image.](#seeimage7)
- Click **Done**.
[]![Reviewing the Documentation in the Add Private Cloud Controller Page of the ZPA Admin Portal](/downloads/zpa/business-continuity-management/private-cloud-controllers/configuring-private-cloud-controllers/zpa-add-private-cloud-controller-step6-review-docs.png)