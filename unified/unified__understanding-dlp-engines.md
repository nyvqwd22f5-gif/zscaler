# Understanding DLP Engines
Source: https://help.zscaler.com/unified/understanding-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1493136.pdf

A [Data Loss Prevention (DLP) engine](/unified/about-dlp-engines) is a collection of one or more DLP dictionaries. The Zscaler service provides predefined DLP engines and supports custom DLP engines:
-
Predefined DLP Engines: The Zscaler service provides 5 predefined engines (HIPAA, GLBA, PCI, Offensive Language, and Self-Harm & Cyberbullying). These engines contain default DLP dictionaries. For example, the PCI engine contains the Credit Cards and Social Security Number dictionaries. You can also edit predefined engines. To learn more, see [Editing Predefined DLP Engines](/unified/editing-predefined-dlp-engines).
The Self-Harm & Cyberbullying engine is intended for use by K-12 educators. If you’re an educator, contact your Zscaler Account team to enable this feature.
- Custom DLP Engines: You can create custom DLP engines to detect content that is relevant to your organization on the DLP Engines page or through the Internet & SaaS API. You can create a maximum of 512 [custom DLP engines](/unified/adding-custom-dlp-engines).
-
If you use a parent dictionary to configure the engine, you have the option to select a sub-dictionary, as well. If the parent dictionary doesn't have patterns or phrases defined (i.e., it is being used simply as a container for sub-dictionaries), then you must select a sub-dictionary from the drop-down menu.
[See image.](#DLP-parent-sub-dictionary)
When you use parent and sub-dictionaries as part of an engine, the Zscaler service evaluates them separately (i.e., parent and sub-dictionaries can match independently of one another). To learn more about configuring parent and sub-dictionaries, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
[]Building Expressions for DLP Engines
When configuring a predefined or custom DLP engine, you can combine DLP dictionaries with operators to create a logical expression. The operators include All (`AND`), Any (`OR`), Exclude (`AND NOT`), and Sum. The Sum operator allows you to specify the sum total of [matches](#match-count-sum-operator) that trigger a group of dictionaries specified in the DLP engine.
[See image.](#DLP-engine-expression-builder-op-images)
To build a DLP engine expression, create subexpressions with operators and dictionaries. Subexpressions determine the logic for how the engine’s dictionaries must trigger in order for the engine to trigger. You can use the Sum operator as part of a subexpression; however, you cannot add a subexpression to an expression or subexpression that uses the Sum operator.
[See image.](#DLP-engine-subexpressions-image)
For example, the following expressions use the same dictionaries. However, because the subexpressions are applied differently, the logic for each expression is different.
- `((ABA Bank Routing Numbers > 0) AND (Credit Cards > 0)) OR (Financial Statements > 0)`
- `(ABA Bank Routing Numbers > 0) AND ((Credit Cards > 0) OR (Financial Statements > 0))`
The following expression uses sub-dictionaries, which appear in brackets within the expression:
`((Parent Container (Canada) [Canadian Driver License] > 0) AND ((Parent Container (Canada) [Canadian Passport Pattern] > 0)))`
[][]Configuring the Match Count
Depending on the operator and the dictionary you select, you must also configure the match count value for a dictionary or group of dictionaries when adding them to a DLP engine. The match count is the threshold that triggers a dictionary or group of dictionaries.
[See image.](#match-count-value-image)
The dictionary or dictionaries trigger only if they find more matches than the number specified. For example:
- If you use the Sum operator in your expression with 3 dictionaries, and you enter a match count of 6, then the policy triggers only if there are 7 or more matches across the 3 dictionaries.
- Similarly, if you use any of the other operators (All, Any, or Exclude) with a dictionary that requires a match count, and you enter a match count of 6, the dictionary triggers only upon finding 7 or more matches in that dictionary. If you select multiple dictionaries with individual match counts, the dictionary is triggered only when the threshold is reached for an individual dictionary.
You can add a dictionary to multiple engines and specify a different match count value each time you add a dictionary to an engine. For example, consider that you want to create a DLP policy rule to block all file uploads containing 5 or more instances of personally identifiable information (PII), and another policy rule to send an email notification whenever a file upload contains at least one instance of PII. In this scenario, you can:
- For your block policy rule, create one DLP engine with PII dictionaries that each have a match count value of 4. You must also ensure that this rule’s order number is before the notification policy rule.
- For your notification policy rule, create a second DLP engine with PII dictionaries that each have a match count value of 0.
To modify the Confidence Score Threshold of a predefined dictionary, you must configure this setting in the dictionary itself. To learn more, see [Configuring the Confidence Score Threshold](/unified/editing-predefined-dlp-dictionaries#confidence).
[]![The DLP Engine Expression Builder Using a Parent and Sub-Dictionary](/downloads/zia/policies/data-loss-prevention/understanding-dlp-engines/ZIA-Engine-Builder-Parent-Sub-Dictionary.png)
[]![The DLP Engine Expression Builder Using a Logical Operator](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-dlp-engines/ZIA-DLP-Engine-Builder-Logical-Operator.png)
[]![The DLP Engine Expression Builder Using a Sum Operator](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-dlp-engines/ZIA-DLP-Engine-Builder-Sum-Operator.png)
[]![Subexpressions for the DLP Engine Expression](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-dlp-engines/ZIA-DLP-engine-subexpressions.png)
[]![The Match Count for the DLP Dictionary in the Engine](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-dlp-engines/ZIA-DLP-Engine-Builder-Match-Counts.png)