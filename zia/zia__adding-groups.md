# Adding Groups
Source: https://help.zscaler.com/zia/adding-groups
PDF: https://help.zscaler.com/pdf/com/en/1398831.pdf

[Click to watch a video about User Management, including how to add a group](https://fast.wistia.net/embed/iframe/65aszz5npz)
Zscaler provides a number of ways to provision [users](/zia/about-users), groups, and [departments](/zia/about-departments) as described in [About Provisioning and Authentication Methods](/zia/choosing-provisioning-and-authentication-methods). You can also add groups when you configure policies. This article describes how to add groups on the Groups page in the ZIA Admin Portal.
You can use a [CSV file to add multiple groups](/zia/about-groups#import-multiple-groups) at once.
To add a new group:
- Go to **Administration **>** User Management**.
- Click the** Groups **tab.
- Click **Add Group**.
The **Add Group** window appears.
- In the **Add Group **window:
- **Name**: Enter a group name. The name can contain up to 128 characters.
- **Comments**: Optionally, enter additional notes or information. The content can't exceed 10,240 characters.
A company can have up to 140K groups. A user can be associated with maximum 127 groups via API and the Zscaler Admin Portal. However, when a user is created or updated via Directory Sync or SCIM, they can be associated with more than 127 groups.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
After creating the group, you can [add users](/zia/adding-users) to it.