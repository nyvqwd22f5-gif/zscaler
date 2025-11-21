# Adding Custom DLP Engines
Source: https://help.zscaler.com/unified/adding-custom-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1493146.pdf

Adding a custom DLP engine is one of the tasks you can complete when configuring [DLP policy rules](/unified/configuring-dlp-policy-rules-content-inspection). You can add a custom DLP engine on the Add DLP Engine window or through the Internet & SaaS API. To learn more about the ranges and limitations for custom DLP engines, see [Ranges & Limitations](/unified/ranges-limitations).
To add a custom DLP engine:
- Go to **Policies > Data Protection > Common Resources > Dictionaries & Engines > DLP Engines**.
-
Click **Add DLP Engine**.
The **Add DLP Engine** window appears.
- In the **Add DLP Engine** window, enter the **Name **for the custom DLP engine.
-
For **Engine Builder**: Add operators and DLP dictionaries to [build an expression](/unified/understanding-dlp-engines#building-expressions). You can see your expression in the **Expression Preview**.
[See image.](#DLP-engine-builder-image)
Under **Expression**:
-
Select an operator to build your expression. The operators include **All** (`AND`), **Any** (`OR`), **Exclude **(`AND NOT`), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the DLP engine.
For the root expression, only the **All** (`AND`), **Any **(`OR`), and **Sum** operators are allowed.
-
Select a dictionary from the drop-down menu, then specify a [match count](/unified/understanding-dlp-engines#match-count) as needed. If you use a parent dictionary to configure the engine, you have the option to select a sub-dictionary, as well. If the parent dictionary doesn't have patterns or phrases defined (i.e., it is being used simply as a container for sub-dictionaries), then you must select a sub-dictionary from the drop-down menu.
[See image.](#DLP-add-engine-parent-sub-dictionary)
When you use parent and sub-dictionaries as part of an engine, the Zscaler service evaluates them separately (i.e., parent and sub-dictionaries can match independently of one another). To learn more about configuring parent and sub-dictionaries, see [Adding Custom DLP Dictionaries](/unified/adding-custom-dlp-dictionaries).
- Click **Add** to add a **Dictionary** or a **Subexpression**. Click the **Remove** icon (![dlp-engine-remove-icon.png](/downloads/zia/policies/data-loss-prevention/adding-dictionaries-predefined-dlp-engine/dlp-engine-remove-icon.png)
) to delete dictionaries or subexpressions.
- If you use the **Sum** operator, select two or more predefined or custom DLP dictionaries. You must set a value for the [match count](/unified/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
- If you use the **All**, **Any**, or **Exclude** operators, you must select a predefined or custom DLP dictionary. Certain dictionaries require you to set a value for the [match count](/unified/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
[See image.](#DLP-match-count-image)
-
If you click **Subexpression**, you must select an operator. The operators include **All** (`AND`), **Any** (`OR`), **Exclude **(`AND NOT`), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the subexpression.
You can use the **Sum** operator as part of a subexpression; however, you cannot add a subexpression to an expression or subexpression that uses the **Sum** operator.
[See image.](#DLP-subexpression-image)
- Continue adding dictionaries and operators to the expression as needed. At each level, you can create up to 4 subexpressions, use up to 4 operators, and add up to 16 dictionaries per operator.
- (Optional) For **Description**,** **enter any additional notes or information. The description cannot exceed 255 characters.
- Click **Save** and activate the change.
You can also add a custom DLP engine through the Internet & SaaS API. If the expression sent for the DLP engine through the API is broken or not recognized, even though it is synthetically correct, the engine builder cannot parse the dictionary. In this case, you need to manually recreate the expression in the **Edit DLP Engine** window in the Admin Portal. In the **Edit DLP Engine** window, the expression that could not be parsed is displayed in the **Reference Expression** field and a blank **Engine Builder** section is displayed. You can then recreate the expression by adding it again in the **Engine Builder** section by referring to the expression in the **Reference Expression** field.
The following are some examples of expressions that cannot be parsed by the engine builder:
- `(D63.S > 0 AND NOT D39.S > 0)`
- `(D63.S > 0 OR NOT D39.S > 0 AND NOT D125.S > 0)`
- `(SUM(D63.S, D246.S) > 2)`
[See image.](#DLP-Expression-Not-Parsed)
[]![The DLP Engine Expression Builder Using a Parent and Sub-Dictionary](/downloads/zia/policies/data-loss-prevention/understanding-dlp-engines/ZIA-Engine-Builder-Parent-Sub-Dictionary.png)
[]![The DLP Engine Builder](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-engine/DLP-Engine-Builder-1.png)
[]![The Match Count for DLP Dictionaries in the Engine](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-engines/ZIA-DLP-Engine-Builder-Match-Counts.png)
[]![Operators for the DLP Engine Expression](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-engines/ZIA-DLP-Predefined-Engine-Operators.png)
[]![Viewing an expression that could not be parsed on the Edit DLP Engine window](/downloads/zia/policies/data-loss-prevention/adding-custom-dlp-engine/DLP-Not-Parsed-Expression.png)