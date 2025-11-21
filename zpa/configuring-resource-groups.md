# Configuring Resource Groups
Source: https://help.zscaler.com/zpa/configuring-resource-groups
PDF: https://help.zscaler.com/pdf/com/en/1531946.pdf

Resource groups are used to configure Microsegmentation policies so that the policy rule has a foundation of data. Therefore, admins must configure resource groups before configuring policies. To learn more, see [About Resource Groups](/zpa/about-resource-groups) and [About Microsegmentation Policies](/zpa/about-microsegmentation-policies).
Prerequisites
Enable policy enforcement for your organization. To learn more, see [Enabling Microsegmentation Policy Settings](/zpa/enabling-microsegmentation-policy-settings).
Configuring a Resource Group
To configure a resource group:
- Go to **Microsegmentation** > **Resource Management**.
- Click the **Resource Groups **tab.
- Click **Add Resource Group**.
The **Add Resource Group **window appears.
[See image.](#Policy-Resource-Policy_Add-Rule)
- In the **Add Resource Group **window:
- In the **General Information** section:
- **Name**: Enter a name for the new resource group.
- **Description**: (Optional) Enter a description.
- Click **Next**.
[See image.](#Add_Rule_window)
- In the **Criteria** section:
- **Resource Group Type**: Select one of the following options:
- **Managed**: The resources have agents and are actively protected.
- **Unmanaged**: The resources are not actively protected by agents. Unmanaged resource groups are defined as CIDR blocks or IP ranges.
- **Static Membership**: Select any or all resources.
-
**Dynamic Membership**: Select one of the following options:
- **Host**: Allows users to define criteria for **Host Name**, **Platform**, **Platform Distro**, **Platform Version**, and **CPU Architecture**.
- **Environment**: Allows users to define criteria for **AMI ID**, **Account/Subscription ID**, **Cloud Provider**, **Cloud Region**, **VPC/VNET ID**, **Subnet ID**, **Security Group ID**, and **ZMS **(i.e., agent groups).
- **Custom**: Allows the admin to define criteria based on user-defined cloud tags. To define custom criteria, the admin must first define the key part of the tag, and then define the value part of the tag.
[See image.](#Rule-Configuration)
The Static Membership and Dynamic Membership options are only for Managed resource groups.
- In the **Review** section, review your configurations. Click the **Edit** icon to edit any of the fields.
[See image.](#Review-Save)
- Click **Save**.
Your new resource group appears in the list.
[]![A view of the Resource Groups page and its actions.](/downloads/zpa/microsegmentation/policy/about-resource-groups/Add-Resource-Group_squircles.png)
[]![The view of a new Resource Group configuration.](/downloads/zpa/microsegmentation/policy/about-resource-groups/Add-Resource-Group_General-Info.png)
[]![The Rule Configuration section Resource Group options.](/downloads/zpa/microsegmentation/resource-management/configuring-resource-groups/Add-Resource-Group_Criteria.png)
[]![The Review section of the window.](/downloads/zpa/microsegmentation/resource-management/configuring-resource-groups/Add-Resource-Group_Review.png)