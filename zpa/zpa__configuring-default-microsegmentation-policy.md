# Configuring the Default Microsegmentation Policy
Source: https://help.zscaler.com/zpa/configuring-default-microsegmentation-policy
PDF: https://help.zscaler.com/pdf/com/en/1531965.pdf

To create [Microsegmentation policies](/zpa/about-microsegmentation-policies) for yourself as an admin, you must first enable each of the [policy enforcement settings](/zpa/enabling-microsegmentation-policy-settings) as well as configure the default policy rule. This rule is what the system defaults to if other policies don’t apply to the traffic observed. The scope of this policy acts as a catch-all for the entirety of your organization's traffic.
Prerequisites
Enable policy enforcement for your organization. To learn more, see [Enabling Microsegmentation Policy Settings](/zpa/enabling-microsegmentation-policy-settings).
Enabling Policy Settings to Configure the Default Policy Rule
To enable and configure the default Microsegmentation policy:
- Go to **Microsegmentation** > **Policy**.
- Click **Settings**.
- Select **Enable** for **Policy Enforcement**.
- Select **Allow** for **Default Resource Policy Rule**.
[See image.](#Policy-Settings)
[]![Configuring-the-Default-Policy-Rule.png](/downloads/zpa/microsegmentation/policy/configuring-default-microsegmentation-policy/Configuring-the-Default-Policy-Rule.png)