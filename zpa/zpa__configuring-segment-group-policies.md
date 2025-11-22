# Migrating and Deleting Segment Group Policies
Source: https://help.zscaler.com/zpa/configuring-segment-group-policies
PDF: https://help.zscaler.com/pdf/com/en/1483506.pdf

Segment group policies are being phased out. You can no longer add a segment group policy using the Group Policy tab. To control application access based on segment group, you must use an access policy rule that includes the group within its Criteria. To learn more, see [Configuring Access Policies](/zpa/about-accesspolicy/new).
If you want to retain or modify an existing segment group policy, you must migrate it. The migration will convert all segment group policy rules formerly under the Group Policy tab into an access policy rule that appears on the [Access Policy](/zpa/about-accesspolicy) page. You can also [delete an existing segment group policy](#delete_seggrppolicy) without migrating its rules.
To migrate segment group policy rules to an access group policy rule:
- Go to **Resource Management **> **Application Management** > **Segment Groups**.
- On the **Segment Groups** page, locate the segment group you want to migrate policy rules for and click the **Migration icon** (![Migration Icon](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/segment-group-policy/about-applicationgrouppolicy-edit/zpa-migratepolicybutton.png)
).
The **Segment Groups** page only displays the icon for groups that contain an existing segment group policy that has not been migrated or deleted.
- In the **Edit Segment Group** window, review the policy rule information and click **Migrate All Rules**.
After the segment group policy rule is successfully migrated, it is automatically deleted and you are redirected to the Access Policy page.
![Edit Segment Group window with Group Policy tab displayed](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/segment-group-policy/about-applicationgrouppolicy-edit/zpa-editsegmentgrp-migratepolicy.png)
Be aware that ZPA evaluates access policy rules prior to any segment group policy rules that have not been migrated. You can use Diagnostics to verify that the rules you migrated to your access policy are taking effect.
[]Deleting a Segment Group Policy
If you decide to delete any segment group policy rules without migrating them, review the policy information to ensure that your organization does not require these rules, or that suitable access policy rules already exist that meet your needs.
To delete segment group policy rules without migrating them:
- Go to **Administration **> **Segment Groups**.
- On the **Segment Groups** page, locate the segment group you want to migrate policy rules for and click the **Migration icon** (![Migration Icon](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/segment-group-policy/about-applicationgrouppolicy-edit/zpa-migratepolicybutton.png)
).
- In the **Edit Segment Group** window, review the policy rule information and click **Delete All Rules**.