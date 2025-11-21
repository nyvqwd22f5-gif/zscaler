# Understanding Severity Scores
Source: https://help.zscaler.com/uvm/understanding-severity-scores
PDF: https://help.zscaler.com/pdf/com/en/1527926.pdf

In vulnerability management, vulnerabilities are given severity scores that are used to prioritize remediation efforts. Severity scores typically range from 0 to 10, where a higher score indicates greater criticality requiring immediate attention and resolution, and thus takes precedence over vulnerabilities with lower scores.
Standard severity scoring frameworks like CVSS and EPSS, as well as scanner-provided scores, often fall short in addressing an organization's unique context.
Zscaler Unified Vulnerability Management (UVM) calculates severity scores based on context and incorporates data from various industry tools and sources, providing more effective and accurate risk assessment. To learn more, see [Configuring Severity Score Formulas](/uvm/configuring-severity-score-formulas).
The score context is divided into two categories:
- Base Score: The initial numerical value derived from processing all score inputs gathered from a particular finding that serves as a foundational reference point. The base score is the main component that carries most of the weight in determining the overall score. It grounds the evaluation in the numerical values obtained from the input data.
- Risk and Mitigating Factors: Additional factors tailored to the unique context of the organization that can shift the score depending on their weight. Assigning more weight to risk and mitigating factors implies that they have a substantial impact on the final score, while less weight indicates that the base score remains the dominant one. For example, risks such as public access raise the severity score, while mitigating factors such as firewalls lower the severity score.
By taking into account specific risks and mitigating factors within an organization, UVM adjusts the initial score and provides an updated severity score. This allows for a more accurate assessment of the actual level of criticality associated with each finding.
When reviewing your tickets on the [Tickets](/uvm/tickets-view) page, each ticket displays both the original and updated severity scores for comparison purposes.
[See image.](#original-adjusted-ticket-score)
You can drill down into the details of the severity score by clicking a finding. Here you can see the initial score, score calculations, and adjustments made based on the configured risk and mitigating factors.
[See image.](#ticket-score-calculation)
[]![mceclip1.png](/downloads/uvm/vulnerability-management/settings/understanding-severity-score/mceclip1.png)
[]![mceclip2.png](/downloads/uvm/vulnerability-management/settings/understanding-severity-score/mceclip2.png)
How the Severity Score Is Calculated
The total severity score is composed of the base score and the risk and mitigating factors, and is calculated per finding. The total score must be 100% or higher to save the score setting. The score is calculated for each component (i.e., base score factors and risk and mitigating factors) separately. The two separate calculations are then summed to make up the final finding severity score.
The following example assumes a balance of 60% for the base score and 40% for the risk and mitigating factors score.
- [Calculating Each Component Separately](#calculating-each-component)
- [Summing the Total Score](#summing-components)
[]First, the base score is calculated and the risk and mitigating score is calculated.
Calculating the Base Score
Suppose you assign the base score a total weight of 60%. You then distribute this percentage between the CVSS score (40%) and the EPSS score (20%).
Base Score = Finding's CVSS score * 0.4 + Finding's EPSS score * 0.2
You can also add the Original Severity Score as part of the base factor. If you do, the original severity score serves as the fallback score when the CVSS and EPSS scores are missing. To learn more, see [Configuring Severity Score Formulas](/uvm/configuring-severity-score-formulas).
Calculating Risk and Mitigating Factors
Since the base score's contribution is 60% of the total score, the risk and mitigating factors receive a weight of 40% of the total score.
- Risk factors increase a finding's severity score, so the result is added to the finding's score.
- Mitigating factors decrease a finding's score, so the result is subtracted from the finding's score.
The formula for calculating a factor's contribution is Risk and Mitigating Factor = 10 (highest possible score) * weight given to the factor.
For example, you can configure risk factors that increase a finding's severity score if the asset it's found on is a crown jewel, if the asset it's found on has PII, or if the finding is a CISA known exploit.
| Risk Factor | Weight | Contribution |
| ----------- | ------ | ------------ |
| Asset Is Crown Jewel | 20% | + 10 * 0.2 |
| Asset Has PII | 12% | + 10 * 0.12 |
| CISA Known Exploited | 10% | + 10 * 0.1 |
| Total | 42% | + 4.2 |
Additionally, you can add mitigating factors that decrease the finding's severity score if the asset it's found on is behind a firewall or if it has EDR installed on it.
| Mitigating Factor | Weight | Contribution |
| ----------------- | ------ | ------------ |
| Asset Is Behind Firewall | 8% | - 10 * 0.08 |
| Asset Has EDR | 10% | - 10 * 0.1 |
| Total | 18% | - 1.8 |
The total contribution of the risk and mitigating factors is 4.2 - 1.8 = 2.4. The 2.4 score is then given a weighted contribution depending on the weight given to the base factor (in our example, 40% or 0.4).
[]For this calculation, the base score and the risk and mitigating factors are summed with their assigned relative weights. In our example, 0.6 * Base Score + 0.4 (completing the score to 100%) * 2.4 (factor contribution).
When the Total Score Exceeds 100%
If the total score exceeds 100%, the calculation caps the risk and mitigating share of the total score to bring it back to 100%. This process is always according to the base score percentage. For example, if the base score and risk and mitigating factors are set equally at 50% and 50%, and we change the base score to 70%, the percentage of the factors is reduced to 30%. To allow the risk and mitigating factors to have more influence, reduce the weight of the base score.
When the Total Score Is Below 100%
To ensure every finding's score always sums to a complete 100%, the score uses a dynamic weight allocation mechanism. If the risk and mitigating factors don't use their full allocated weight (e.g., if a factor is null or not applicable to a specific finding), the unused portion of their allocated weight is proportionally reallocated to the individual factors of the base score.
For example, consider the following score allocation:
Base score (60% of total score):
- CVSS 40%
- EPSS 20%
Risk and Mitigating Factors (60% > capped at 40%):
- Asset Is Crown Jewel - 20%
- Asset Has PII - 12%
- CISA Known Exploited - 10%
- Asset Is Behind Firewall - 8%
- Asset Has EDR - 10%
If the risk and mitigating factors contribute only 30% to a finding's score, leaving 10% unused from their 40% allocation, the unused 10% is added to the base score. This 10% increases the base score's total contribution from 60% to 70%, and is proportionally distributed to CVSS and EPSS based on their original shares within the base score (CVSS gains 6.67%, EPSS gains 3.33%).