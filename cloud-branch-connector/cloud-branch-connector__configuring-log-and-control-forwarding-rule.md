# Configuring the Log and Control Forwarding Rule
Source: https://help.zscaler.com/cloud-branch-connector/configuring-log-and-control-forwarding-rule
PDF: https://help.zscaler.com/pdf/com/en/1420506.pdf

[Watch a video about Log and Control Forwarding.](https://fast.wistia.net/embed/iframe/a7m0d6dlg8)
You can configure a Log and Control Forwarding rule to control how the traffic logs and the operational messages are forwarded to the Zscaler cloud.
Adding a Log and Control Forwarding Rule
A default log and control forwarding rule with a default gateway forwarding action is automatically created. To configure a log and control forwarding rule:
- Go to **Forwarding **>** Log and Control Forwarding**.
-
Click **Add Log and Control Forwarding Rule**.
[See image.](#AddLogandControl)
The **Add Log and Control Forwarding Rule** window appears.
- In the **Add Log Control and Forwarding Rule** window:
- In the **Forwarding Rule** section, enter the rule attributes:
- **Rule Order**:** **Enter the order of the rule. Forwarding rules are evaluated in ascending numerical order (Rule 1 before Rule 2), and the Rule Order reflects this rule's place in the order. You can change the value based on your requirements.
- **Rule Name**: Enter a user-friendly name for the rule. The log and forwarding control automatically creates a rule name, which you can change. The maximum length is 31 characters.
- **Rule Status**:** **Select **Enabled** to actively enforce the rule. When you select **Disabled**, the service skips it and moves to the next rule. However, the rule does not lose its place in the Rule Order.
- In the **Source **section, configure the following rule attributes:
- **Location**: Select **Any** to apply the rule to all locations, or select up to 8 locations. You can also search for and select a location.
- **Cloud & Branch Connector Groups**: Select **Any** to apply the rule to all groups, or select specific groups to apply the rule. You can also search for groups and select them.
- From the **Gateway** drop-down menu, choose an appropriate [Log and Control Gateway​​​](/cloud-branch-connector/configuring-log-and-control-gateway).
-
In the **Description** field, enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#LogandControlWindow)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![The Add Log and Control Forwarding Rule button in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-log-and-control-forwarding-rule-draft-doc-46113/Add%20Log%20and%20Control%20forwarding%20rule%20brnch.jpg)
[]![The Add Log and Control Forwarding Rule window in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-log-and-control-forwarding-rule-draft-doc-46113/Add%20Log%20and%20Control%20Forwarding%20rule%20update.png)