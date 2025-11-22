# Configuring Microsegmentation Policies
Source: https://help.zscaler.com/zpa/configuring-microsegmentation-policies
PDF: https://help.zscaler.com/pdf/com/en/1531966.pdf

Admins can create Layer 3 and Layer 4 Microsegmentation enforcement policies to protect east-west traffic in both cloud and data center environments. Policies are applied between resource groups or between a resource group and any other [resource](/zpa/about-resources). Policies are evaluated from highest priority (lowest integer) to lowest priority (highest integer). No two policies can have the same priority.
The default policy is a rule you must configure when first enabling policy enforcement for your organization. To learn more, see [Configuring a Default Microsegmentation Policy](/zpa/configuring-default-microsegmentation-policy).
Prerequisites
Enable policy enforcement for your organization. To learn more, see [Enabling Microsegmentation Policy Settings](/zpa/enabling-microsegmentation-policy-settings).
Configuring a Microsegmentation Policy
To configure a Microsegmentation policy:
- Go to **Microsegmentation** > **Policy**.
- Click the **Resource Policy** tab.
- Click **Add Rule**.
The **Add Rule **window appears.
[See image.](#Policy-Resource-Policy_Add-Rule)
- In the **Add Rule** window:
- In the **General Information** section:
- **Name**: Enter a name for the new policy.
- **Description**: (Optional) Enter a description.
- Click **Next**.
[See image.](#Add_Rule_window)
- In the **Rule Configuration** section:
- **Priority**: Enter a value between 1 and 5000.
- **Action**: Select **Allow**, **Sim Block**, or **Block**.
- **Source**: Select **ANY** to allow any sources that apply to the traffic found, or select up to 10 sources total. You cannot select ANY for Source if it is selected for Destination.
- **Destination**: Select **ANY** to allow any destinations that apply to the traffic found, or select up to 10 destinations total. You cannot select ANY for Destination if it is selected for Source.
- **Default Port Ranges**: Select any or all of the default port ranges.
- **TCP Port Ranges**: Enter TCP port range information in the **From** and **To** fields. Click **Add TCP Port Range** to add up to 10 ranges.
- **UDP Port Ranges**: Enter UDP port range information in the **From** and **To** fields. Click **Add UDP Port Range** to add up to 10 ranges.
- **Include all AppZones**: Select the checkbox to **Include all AppZones**. If you deselect this option, a drop-down menu appears for you to choose which ones to include.
- Click **Next**.
[See image.](#Rule-Configuration)
- In the **Review** section, review your configurations. Click the **Edit** icon to edit any of the fields.
[See image.](#Review-Save)
- Click **Save**.
Your new policy rule appears in the list of rules on the [Resource Policy](/zpa/about-microsegmentation-policies) page.
[]![A view of the AppZone page and its actions.](/downloads/zpa/microsegmentation/policy/Policy_Resource-Policy_Add-Rule_squircles.png)
[]![The view of a new AppZone configuration.](/downloads/zpa/microsegmentation/policy/configuring-microsegmentation-policies/Add-Rule-window.png)
[]![The Rule Configuration section of the window.](/downloads/zpa/microsegmentation/policy/configuring-microsegmentation-policies/Rule-Configuration-filled.png)
[]![The Review section of the window.](/downloads/zpa/microsegmentation/policy/configuring-microsegmentation-policies/Review_Save.png)