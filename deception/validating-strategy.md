# Validating a Strategy
Source: https://help.zscaler.com/deception/validating-strategy
PDF: https://help.zscaler.com/pdf/com/en/1531466.pdf

You can [create a strategy](/deception/creating-deception-strategy) with landmine policies and personalities. These landmine personalities have browser, session, and memory credential lures that place decoys such as Network, Active Directory (AD), Threat Intelligence (TI) as breadcrumbs on the endpoint to lure adversaries. You can validate the strategy to ensure that the corresponding Network, AD, and TI decoys are available for the configured landmine lures.
To validate a Deception Strategy:
- Go to **Miragemaker **>** Strategy Builder **>** Deception Strategy**.
- Click the **Validate** icon for the strategy that you want to validate.
[See image.](#deception-strategy-validate-icon)
- The strategy is validated. You can see the total percentage of enabled landmine lures with available Network, AD, and TI decoys.
[See image.](#deception-validate-strategy-results)
- Click **Close**.
[]![The Deception Strategy page with an annotation around the Validate button](/downloads/deception/miragemaker/strategy-builder/deception-strategy/validating-strategy/zscaler-decption-validate-strategy-7.png)
[]![Decoy strategies sucessfully validated on the Strategy Validation page](/downloads/deception/deceive/deception-strategy/validating-deception-strategy/zscaler-deception-validate-strategy.png)