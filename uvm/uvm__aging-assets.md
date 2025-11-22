# Aging Assets
Source: https://help.zscaler.com/uvm/aging-assets
PDF: https://help.zscaler.com/pdf/com/en/1529950.pdf

The Asset Aging feature in the Zscaler Security Operations (SecOps) platform enables organizations to automatically transition outdated or irrelevant assets to an inactive state. This enhances asset inventory accuracy and significantly reduces noise for security teams, ultimately improving operational efficiency and risk prioritization.
Asset aging rules can be automated and configured using two primary criteria:
- Aging by time: Age assets based on the number of days since they were last detected by integrated tools or systems (using the Asset Last Seen field).
- Aging by value: Age assets based on updates from the source system indicating status changes or other relevant field data.
Inactive assets remain available for historical reporting but can be excluded from primary dashboard views. This ensures cleaner, more relevant inventory data without deleting the asset from the platform.
Configuring Asset Aging Rules
Asset aging includes a fallback rule that specifies a default value with no conditional logic. This ensures that there is always default aging logic in place, preventing potential data conflicts or loss. The fallback rule can be edited, but can’t be removed or deleted.
For access to Asset Aging, your assigned role must include the Read, Create, and Edit permissions under the Platform - Model Management resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users).
To configure an asset aging rule:
- Go to **Configure** > **Asset Aging**.
- Click **New Rule**.
The **Create Aging Rule** drawer appears.
- In the **Create Aging Rule** drawer:
- **Name**: Enter a unique name for the rule.
- **Category**: Select a rule category.
- [Aging by time](#aging-by-time)
- [Aging by value](#aging-by-value)
- Click **Add**.
Repeat the process to add as many rules as necessary. The rules' order of appearance doesn't affect the order of their application. Each data point is evaluated against all rules, even if one rule has already been satisfied.
[]Automatically age an asset when it has not been detected by the selected sources for a defined number of days.
- **Asset Population**: Define which assets the rule applies to.
-
**Aging Scenario**: Specify conditions, such as sources and duration.
Use reliable sources to ensure assets are aged based on trustworthy detection data, and to avoid incorrectly aging active assets. When multiple sources are selected, they all must report the asset as unseen for the specified duration for the asset to age.
[]Automatically age an asset when a specific value change is reported by a source system, such as status updates indicating inactivity.
- **Asset Population**: Define which assets the rule applies to.
-
**Aging Scenario**: Specify the condition based on changes in a relevant source field.
Choose a reliable source to ensure assets are aged based on accurate status signals, and to avoid incorrectly aging active assets. While each individual condition can reference only one source, you can add multiple conditions within the same rule.