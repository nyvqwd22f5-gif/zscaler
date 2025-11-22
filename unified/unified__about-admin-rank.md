# About Admin Rank
Source: https://help.zscaler.com/unified/about-admin-rank
PDF: https://help.zscaler.com/pdf/com/en/1491166.pdf

Admin rank is a feature you use when creating [roles](/unified/adding-admin-roles) for [role-based administration](/unified/about-administrators).
Admin rank enables you to create a hierarchy among admins and ensure that policies and settings configured by admins with higher rank cannot be overridden by admins with lower rank. For example, if the CISO, who has the highest rank, sets a rule for the organization blocking all access to pornography, no lower-ranked admin can create a pornography rule that overrides the one set by the CISO. The admin rank ranges from 0 (high) to 7 (low). The highest rank, 0, belongs to the super admin. For each additional role you create, you can assign an admin rank between 1 (high) and 7 (low).
By default, the admin ranking is disabled. To use this feature, you must enable admin rank in Advanced Settings. To learn more, see [Configuring Advanced Settings](/unified/configuring-advanced-settings#admin-ranking).
The admin rank affects admins in the following areas:
- [Rule-Based Policies](#rule-based-policies)
- [Role Management](#role-management)
- [Administrator Management](#administrator-management)
- [Specifying Users for Rules](#specifying-users-for-rules)
[]Rule-based policies in the Admin Portal include:
- Sandbox (requires Advanced Sandbox)
- URL & Cloud App Control
- File Type Control
- Bandwidth Control
- Data Loss Prevention
- Mobile App Control
- Firewall Control
- DNS Control
When creating rules for any of the above policies, admins must assign the rule an admin rank that is lower than their own rank. The rule’s admin rank in turn automatically determines the rule order, so that rules with a higher admin rank are always given precedence in the rule order. Rules with the same admin rank can be manually moved before or after another rule with the same rank.
Admins can edit a rule or change a rule’s place in the rule order only if the rule’s admin rank is equal to or lower than their own admin rank.
[]Admins who have permission to manage roles can only create or edit roles with lower rank.
[]Admins who have permission to manage other admin accounts can only create, edit, or view accounts with lower rank.
[]Admins are also users that can be specified in the criteria for a particular rule. For example, an admin can be chosen as a user to whom a URL filtering rule applies. Thus, if admins add another admin as a user for a rule, they can only select admins that have lower admin rank.