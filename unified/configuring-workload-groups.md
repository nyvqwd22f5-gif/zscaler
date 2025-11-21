# Configuring Workload Groups
Source: https://help.zscaler.com/zia/configuring-workload-groups
PDF: https://help.zscaler.com/pdf/com/en/1461746.pdf

You can configure workload groups to apply security policies to the workloads deployed on the Amazon Web Services (AWS) platform. You can view all the workloads and their respective tags in the [Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/about-partner-integrations). A maximum of 8 key-value pairs can be used to build the expression for the workload group. To learn more, see [About Workload Groups](/zia/about-workload-groups).
Only admins with full policy access can add or edit the workload groups.
To configure a workload group:
- Go to **Administration** > **Workload Groups**.
- Click **Add Workload Group**. The **Add Workload Group** window appears.
[See image.](#add-workload-groups-window)
- In the **Add Workload Group** window:
- **Name**: Enter a name for the workload group.
- **Description**: (Optional) Enter additional notes or information about the workload group.
- **Tag Type**: Select a tag type from the drop-down menu.
- Click **Add Tag** to build an expression using appropriate tag keys and tag values for the workload group.
[See image.](#add-tags-option-workload-group)
- Enter a tag key in the text box and press `Enter`. The tag key is added to a list and available for selection. Select a tag key from the list for the workload group expression.
For the **Attribute** tag type, you cannot add tag keys manually. The **Add Tag** field populates a set of [predefined tag keys.](#predefined-tag-keys) To learn more, see [Understanding Workload Groups](/zia/understanding-workload-groups#workload-resources).
- Enter a tag value for the selected tag key in the text box and press `Enter`. The tag value is added to a list and available for selection. Select a tag value from the list for the workload group expression.
[See image.](#add-tag-keys-values)
The added tag key and tag values are displayed in the list when you add new key-value pairs. When adding new tags, if the list doesn't contain your required key-value pair, enter the tag key and tag value in the text box and press `Enter`.
You can also add multiple key-value pairs for the same tag type and associate them with an AND or OR operation. Click on the operation sign to change the expression.
[See image.](#change-tags-operation-sign)
- Click **Add More** to configure multiple tag types for the workload group that can be connected through AND or OR operations. You can click on the operation sign to change the expression.
[See image.](#add-more-tag-types)
- Click **Show Expression** to verify the tag expression you created for the workload group. This field displays a two-dimensional expression table with a single operator in each row and column.
[See image.](#show-expression-image)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []GroupId
- GroupName
- IamInstanceProfile-Arn
- ImageId
- PlatformDetails
- Vpc-id
![Screenshot of Show Expression field for the workload group in Add Workload Groups window ](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-window-hide-expression-image.png)
[]
[]![Screenshot of the Add Workload Groups window in the Administration KB](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-window.png)
[![Screenshot of adding tags for the workload group in Add Workload Groups window ](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-window-add-tags.png)
][]
[]![Screenshot showing how to change tag operation sign for workload group](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-window-change-tags-operation-sign.png)
![Screenshot of adding new tag keys and tag values for the workload group in Add Workload Groups window ](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-window-add-tag-keys-values.png)
[]
![Screenshot of adding more tag types for the workload group in Add Workload Groups window ](/downloads/zia/policies/configuring-workload-groups/zia-add-workload-groups-add-more-tag-type-change-operation-sign.png)
[]