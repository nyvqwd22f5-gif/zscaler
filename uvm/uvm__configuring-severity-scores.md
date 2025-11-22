# Configuring Severity Scores
Source: https://help.zscaler.com/uvm/configuring-severity-scores
PDF: https://help.zscaler.com/pdf/com/en/1527921.pdf

Severity scores are numerical values assigned to security findings that are used to evaluate their associated risk. These scores help security teams effectively allocate resources and make informed decisions, ensuring accurate risk prioritization, streamlined remediation, and immediate attention to critical vulnerabilities.
Within Zscaler's Unified Vulnerability Management (UVM) app, you can customize how severity scores are calculated for findings. This customization uses external scores and configurable risk and mitigating factors, which provide additional context (e.g., information about the asset associated with the finding). To learn more about severity scores, see [Understanding Severity Scores](/uvm/understanding-severity-score).
Admins can configure UVM score settings. If you do not have admin access but require access to score settings, contact your Zscaler Account team or Zscaler Support.
Configuring the Severity Score
Setting up severity scores involves defining and customizing the base score and risk and mitigating factors to accurately assess the risk level of findings.
Zscaler recommends keeping a balance of 60% for the base score and 40% for the mitigating score.
Setting the Base Score
The base score is an initial value typically calculated from the external scores of a finding. It serves as the primary reference point for the overall severity calculation and carries the most weight in determining the final score. You can select the metrics to include in the base score and configure their weights.
The base score is most commonly configured to include a combination of the finding's CVSS and EPSS scores, which are typically a decimal value between zero and one. To standardize these scores, they are converted to a value on a scale from 1 to 10 by multiplying the decimal value by 10.
To set the base score:
-
In the **Vulnerabilities **app, go to **Settings **> **Score**.
If score settings is configured in the Data Model, you'll be prompted to Unlink & Override to configure score settings on the Score page.
- In the **Base Score** section:
- Select the relevant fields to be used for the base score. The default factors are **CVSS**, **EPSS**, and **Original Severity Score** received from a scanner.
- Assign a percentage to each base score factor to define its contribution to the total score.
To add a factor to the base score:
-
Click **Add Factor**.
The** Add New Factor **drawer appears.
- In the **Add New Factor **drawer:
- **Factor Name**: Enter a name for the factor.
-
**Field**: Select a field from the drop-down menu. Available fields are related to assets, vulnerabilities, or findings.
Zscaler recommends using fields with numerical values.
- **Share of total score**: Set the percentage of this new factor's weight from the total score.
- Click **Apply**.
If all base score factors are null, the severity score is also null. The weighted base score is calculated as the sum of each base factor multiplied by its dynamically adjusted weight, producing a standardized score on a 0 to 10 scale. This weighted base score serves as the anchor score, to which risk and mitigating factors add or subtract points subject to capping constraints.
Setting the Risk and Mitigating Factors
Risk and mitigating factors provide additional organizational context that can adjust a finding's score based on their assigned weights. Configuring risk and mitigating factors involves:
- Identifying the key risk and mitigating factors relevant to your organization. You can add as many risk or mitigating factors as needed.
- Risk Factors: These increase the severity score by accounting for additional vulnerability context. For example, if an asset contains Personally Identifiable Information (PII), the likelihood of it being targeted is higher, raising its severity.
- Mitigating Factors: These decrease the severity score by accounting for protective measures in place. For example, an asset with a firewall is less exposed to threats, reducing its severity score.
- Assigning a weight to each factor based on its significance to your organization. Factor weights can be adjusted to reflect the specific context and priorities of your environment. For example, if PII exposure is critical to your risk model, you can assign a higher weight to that risk factor.
To add risk and mitigating factors to the score:
-
In the **Risk & Mitigating Factors** section, click **Add Factor**.
The** Add New Factor **drawer appears.
- In the **Add New Factor **drawer:
- **Factor Type**: Select **Risk Factors** or **Mitigating Factors**.
- **Factor Name**: Enter a name for the factor.
-
**Field**: Select a field from the drop-down menu. Available fields are related to assets, vulnerabilities, or findings.
Zscaler recommends using fields with numerical values.
- **When **<Field Name>** Equals**: Configure the numerical value of each factor depending on the factor field type.
- For Boolean fields, enter the percentage weights for **True**, **False**, and **Else**.
- For string fields, enter the expected field values and enter a percentage weight for each.
- Click **Apply**.
The weight assigned to risk and mitigating factors is capped based on the percentage remaining after the base score's weight is set. For example, if the base score is assigned 60% of the total score, the combined weight of all risk and mitigating factors is capped at the remaining 40%. In the following image, the 170% represents the total contribution of risk and mitigating factors before capping, while the 40% reflects their adjusted share within the total score. This ensures the combined weight of the base score and the factors always adds up to 100%.
[See image.](#risk-mitigating-factors-170-40)
Using the Original Severity Score as Fallback
The Original Severity Score is a base score factor derived from external vendors, with each vendor employing its own unique method of calculation. These vendor-specific methods are not detailed or incorporated into the UVM score calculation.
- If the Original Severity Score is included in the base score as a factor and assigned a weight of 0%, it receives the full weight as a fallback when all other base score factors are null.
- If the Original Severity Score is not included in the base score and all other factors are null, no weights are reassigned to it.
Factor Field Type
Factors can be configured with either Boolean fields or string fields. The factor's field type dictates how a factor is configured and how it contributes to the overall risk calculation.
- [Boolean Factors](#boolean-factors)
- [String Factors](#string-factors)
[]Boolean factors represent entity attributes that are either true or false (e.g., Asset Has PII, Is Crown Jewel).
- Boolean risk factors increase the finding's score if true and reduce or leave the score unchanged otherwise (if false or null).
- Boolean mitigating factors reduce the finding's score if true and increase or leave the score unchanged otherwise (if false or null).
[]String factors represent entity attributes that can have a gradual effect (e.g., the User Prone to Phishing field with the values Low, Medium, High, Severe). For string factors, you can set the effect that each value has on the score (e.g., Low - don't change, Medium - increase by 5%, High - increase by 10%, Severe - increase by 20%).
When a string factor's returned value meets the Else condition, the weight of the factor is proportionally redistributed among the remaining factors. If no other factors are present, the weight of the factor is proportionally distributed to the base factors.
Using the Score Simulator
You can use the score simulator to validate severity scores by modeling the impact of different factors on the scoring system.
[See image.](#score-simulator)
To use the score simulator:
- In the **Vulnerabilities **app, go to **Settings **> **Score**.
- In the **Score Simulator** section on the left:
- **Base Score Factors**: Enter a numerical value for all factors.
- **Risk Factors**: Select a value for each drop-down menu (e.g., **True**, **False**, **Else**). If no value is selected, the factor is counted according to the Else condition.
- Click **Calculate Score**.
[]![risk and mitigating factors 170 to 40](/downloads/uvm/vulnerability-management/settings-uvm/understanding-severity-score/risk%20and%20mitigating%20factors%20170%20to%2040.png)
[]![c009f90d-9abb-4b2e-85cd-f3f84871054e.png](/downloads/uvm/vulnerability-management/settings/configuring-severity-score-formulas/c009f90d-9abb-4b2e-85cd-f3f84871054e.png)