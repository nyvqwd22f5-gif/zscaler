# DLP Policy Configuration Example: Match Only
Source: https://help.zscaler.com/unified/dlp-policy-configuration-example-match-only
PDF: https://help.zscaler.com/pdf/com/en/1493081.pdf

Using rules with the Match Only option selected or unselected affects how the Data Loss Prevention (DLP) policy evaluates its rules when inspecting transactions. A rule with Match Only selected only triggers when transactions match the rule’s specified DLP engines and no other engines from different rules. This allows you to prevent users from leaking sensitive data when sending out non-sensitive data.
The following example illustrates how the Match Only option affects how the DLP policy evaluates its rules.
In this scenario, your organization’s DLP policy includes the following rules:
![An example of a Zscaler Data Loss Prevention (DLP) policy](/downloads/zia/policies/data-loss-prevention/dlp-policy-configuration-example-match-only/ZIA-Example-DLP-Policy-Rules.png)
- Rule 1 allows your organization’s finance team to send out credit card numbers.
- Rule 2 allows your organization’s human resources team to send out social security numbers.
- Rule 3 blocks the rest of your organization from sending out credit card numbers and social security numbers.
A member of the finance team sends out a document that includes both credit card numbers and social security numbers. Your DLP policy's action for this transaction depends on whether your Allow rules (i.e., Rule 1 and Rule 2) have the Match Only option selected or unselected.
For example, you have selected Match Only for Rule 1 and Rule 2.
- The document does not match Rule 1, despite belonging to a finance team member. This is because Rule 1 only triggers if a document only contains credit card numbers and no additional content that triggers other engines from different rules.
- The document does not match Rule 2, because the document’s owner is not a human resources team member.
- The document matches Rule 3, because the document contains both credit card numbers and social security numbers. This results in the DLP policy blocking the transaction, and the finance team member is unsuccessful in sending out the social security numbers.
If you did not select Match Only for both rules, the DLP policy will take a different action instead.
For example, you have not selected Match Only for Rule 1 and Rule 2. The document matches Rule 1, despite containing social security numbers. This is because Rule 1 triggers if a document contains credit card numbers and any additional content. This results in the DLP policy allowing the transaction, and the finance team member succeeds in sending out the social security numbers.