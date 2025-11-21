# Cloning DLP Engines
Source: https://help.zscaler.com/zia/cloning-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1450976.pdf

You can duplicate a predefined or custom engine if you need to easily copy the functionality of an existing engine for a different use. To duplicate an existing DLP engine:
- Go to **Administration** >** ****DLP Dictionaries & Engines**.
- In the **DLP Engines **tab, click the **Clone **icon for the DLP engine.
The **Clone DLP Engine** window appears.
- In the **Clone DLP Engine** window, specify a name for the new engine.
- For **Engine Builder**, add operators and DLP dictionaries to [build an expression](/zia/understanding-dlp-engines#building-expressions). You can see your expression in the **Expression Preview**.
[See image.](#DLP-engine-builder-image)
Under **Expression**:
- Select an operator to build your expression. The operators include **All** (AND), **Any** (OR), **Exclude **(AND NOT), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the DLP engine.
For the root expression, only the **All** (AND), **Any **(OR), and **Sum** operators are allowed.
- Click **Add** to add a **Dictionary** or a **Subexpression**. Click the **Remove** icon (![dlp-engine-remove-icon.png](/downloads/zia/policies/data-loss-prevention/adding-dictionaries-predefined-dlp-engine/dlp-engine-remove-icon.png)
) to delete dictionaries or subexpressions.
- If you use the **Sum** operator, select two or more predefined or custom DLP dictionaries. You must set a value for the [match count](/zia/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
- If you use the **All**, **Any**, or **Exclude** operators, you must select a predefined or custom DLP dictionary. Certain dictionaries require you to set a value for the [match count](/zia/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
[See image.](#DLP-match-count-image)
- If you click **Subexpression**, you must select an operator. The operators include **All** (AND), **Any** (OR), **Exclude **(AND NOT), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the subexpression.
You can use the **Sum** operator as part of a subexpression; however, you cannot add a subexpression to an expression or subexpression that uses the **Sum** operator.
[See image.](#DLP-subexpression-image)
- Continue adding dictionaries and operators to the expression as needed. At each level, you can create up to 4 subexpressions, use up to 4 operators, and add up to 16 dictionaries per operator.
- (Optional) For **Description**,** **enter any additional notes or information. The description cannot exceed 255 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The DLP Engine Expression Builder](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/cloning-dlp-engines/ZIA-Clone-DLP-Engine-Dialog.png?1680868114)
[]![The Match Count for DLP Dictionaries in the Engine](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/cloning-dlp-engines/ZIA-DLP-Engine-Builder-Match-Counts.png)
[]![Operators for the DLP Engine Expression](/downloads/zia/policies/data-loss-prevention/cloning-dlp-engines/ZIA-DLP-Predefined-Engine-Operators.png)