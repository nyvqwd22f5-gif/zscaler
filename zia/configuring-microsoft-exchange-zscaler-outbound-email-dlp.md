# Configuring Microsoft Exchange for Zscaler Outbound Email DLP
Source: https://help.zscaler.com/zia/configuring-microsoft-exchange-zscaler-outbound-email-dlp
PDF: https://help.zscaler.com/pdf/com/en/1492736.pdf

Zscaler Outbound Email Data Loss Prevention (DLP) allows you to establish a connection between your Exchange server and Zscaler's cutting-edge Data Loss Prevention (DLP) tools to prevent the exfiltration of sensitive data in outbound emails sent to external domains. To do so, you must configure connectors to allow bidirectional communication between your Exchange server and the Zscaler smart host, and you must configure mail flow rules (also known as transport rules) to determine how mail flows from your Exchange server to the Zscaler service, and vice versa.
This article explains how to configure your Exchange server to use a Zscaler smart host for a basic use case. To learn more about configuring your Exchange server for other use cases, refer to the [Microsoft technical documentation](https://learn.microsoft.com/en-us/exchange/mail-flow/mail-flow). To learn about configuring your Gmail server for Outbound email DLP, see [Configuring Gmail for Zscaler Outbound Email DLP](/zia/configuring-gmail-zscaler-outbound-email-dlp).
To configure the Exchange server to use a Zscaler smart host:
- [1. Configure a smart host send connector.](#send-connector)
- [2. Configure a smart host receive connector.](#receive-connector)
- [3. Configure a mail flow rule to send email to the Zscaler smart host.](#mail-flow-rule-outbound)
- [4. Configure a mail flow rule to act on email received from the Zscaler smart host.](#mail-flow-rule-inbound)
- [5. Set the rule mode to enforce the mail flow rule.](#enforce-mail-flow-rule)
With these settings configured, and with a Zscaler [outbound email policy rule configured](/zia/configuring-outbound-email-policy-rules) to detect and block sensitive information, users who try to send an email containing HIPAA information to an external domain receive a message from the Exchange server that their message was blocked.
[See image.](#blocked-message-exchange)
[]![A blocked email message from Microsoft Exchange](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Blocked-Message-generic.png)
[][]To create a connector so that outbound email sent to external domains is routed from Exchange to the Zscaler smart host:
- Sign in to the [Exchange Admin Center](https://admin.exchange.microsoft.com/).
- In the left-side navigation, go to **Mail flow > Connectors**.
[See image.](#send-mail-flow-connectors-option)
The **Connectors** page appears.
- On the **Connectors** page, click **Add a connector**.
The **Add a connector** panel opens.
- In the **Connection from** section select **Office 365**, and in the **Connection to** section, select **Partner organization**, then click **Next**.
[See image.](#send-add-a-connector-panel)
- Specify a name (i.e., `Office-to-Zscaler`) and an optional description, select the **Turn it on** checkbox, then click **Next**.
[See image.](#send-conn-name-turn-off)
Zscaler recommends disabling the connector that sends email from your Exchange server to the Zscaler smart host until all connectors and mail flow rules are configured.
- On the **Use of connector** page, select **Only when I have a transport rule set up that redirects messages to this connector**, then click **Next**.
[See image.](#send-use-of-connector)
- On the **Routing** page, select **Route email through these smart hosts**, specify the Smart Host FQDN, then click the **+** button to add the smart host server.
[See image.](#send-routing-page)
You can find the Smart Host FQDN on the [Edit Email Tenant page](/zia/editing-email-tenants#copied-values-for-exchange) in the ZIA Admin Portal.
- Click **Next**.
- On the **Security restrictions** page, select **Issued by a trusted certificate authority**, then select the **Add the subject name or subject alternative name (SAN) matches this domain name** checkbox. Enter the domain for the Zscaler cloud where your smart host is located (i.e., `*.zscloud.net`), then click **Next**.
[See image.](#send-security-restrictions-page)
- On the **Validation email** page, enter a validation email address for the smart host server, then click the **Add** icon to add the email address.
[See image.](#send-validation-email)
- Click **Validate** to validate the connection to the smart host server.
You receive a confirmation message. The validation for the email address might fail because mail flow rules aren't in place yet. Before you continue setting up the connector, however, ensure that the connectivity task is successful.
[See image.](#send-validation-fail)
- Click **Next**.
If you receive a confirmation message because the test email didn't send successfully, click **Yes, proceed**.
[See image.](#send-confirm-not-valid)
- Review the connector settings, then click **Create connector**.
[See image.](#send-review-connector-settings)
A confirmation page appears.
- Click **Done**.
You return to the **Connectors** page and the new connector appears in the list.
[]![The Connectors menu option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Connectors-01.png)
[]![The Add a Connector drawer in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-New-Connector-03.png)
[]![The Add a Connector Name drawer in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Connector-Name-Turn-Off.png)
[]![The Use of Connector page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Use-of-Connector-04.png)
[]![The Connector Routing page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Connector-Routing-05.png)
[]![The Connector Security Restrictions page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Connector-Security-Restrictions.png)
[]![The Connector Send Validation Email page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Connector-Security-Restrictions-Valid-Email-07.png)
[]![The Connector Send Validation Email page with a failure message in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Connector-Confirm.png)
[]![The Connector Send Validation Email confirmation page with a failure message in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Connector-Confirm-not-valid.png)
[]![The Review Connector page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Review-Connector-08-2.png)
[]To create a connector to receive processed email from the Zscaler smart host:
- Sign in to the [Exchange Admin Center](https://admin.exchange.microsoft.com/).
- In the left-side navigation, go to **Mail flow > Connectors**.
[See image.](#receive-mail-flow-connectors-option)
The **Connectors** page appears.
- On the **Connectors** page, click **Add a connector**.
The **Add a connector** panel opens.
- In the **Connection from** section select **Your organization's email server**, then click **Next**.
[See image.](#receive-add-a-connector-panel)
- Specify a name (i.e., `Zscaler-to-Office`) and an optional description, then click **Next**.
- On the **Authenticating sent email** page, select **By verifying that the sender domain matches one of the following domains**, enter the domain for the Zscaler cloud where your smart host is located (i.e., `*.zscloud.net`), click the **Add** icon, then click **Next**.
[See image.](#send-auth-email)
- Review the connector settings, then click **Create connector**.
[See image.](#receive-review-connector-settings)
A confirmation page appears.
- Click **Done**.
You return to the **Connectors** page and the new connector appears in the list.
[]![The Connectors menu option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Connectors-receive.png)
[]![The Add a Connector drawer in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-New-Connector-receive-your-org.png)
[]![The Authenticating Sent Email Connector drawer in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Receive-Connector-Authenticate.png)
[]![The Review Connector page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Receive-Connector-Review.png)
[]After setting up the connector for the Zscaler smart host, you must configure a mail flow rule to forward email to the Zscaler service. You add a header with information from your configured Zscaler smart host so that the Zscaler service can properly receive and process email content from your Exchange server.
To configure a mail flow rule to forward email to the Zscaler service:
- Sign in to the [Exchange Admin Center](https://admin.exchange.microsoft.com/).
- In the left-side navigation, go to **Mail flow > Rules**.
[See image.](#mail-flow-rules-option)
The **Rules** page appears.
- On the **Rules** page, click **Add a rule > Create a new rule**.
The **New transport rule** panel opens on the **Set rule conditions** page.
- On the **Set rule conditions** page:
- **Name**: Enter a name for the transport rule.
- **Apply this rule if**: Select **The recipient** in the first drop-down menu, then **is external/internal** from the second drop-down menu. In the **select recipient location** drawer that opens, select **Outside the organization** from the drop-down menu, then click **Save**.
[See image.](#outbound-select-recipient-location)
- **Do the following**: Select **Redirect the message to**, then select **The following connector** from the second drop-down menu. In the **select connector** drawer that opens, select the send connector you created earlier, then click **Save**.
[See image.](#outbound-select-connector)
- Click the **Add** icon to add a condition to set a header for the Zscaler smart host you configured. This condition helps the Zscaler smart host identify the mail it receives from your Exchange server.
- In the **And** drop-down menu, select **Modify the message properties**, then in the **Select one** drop-down menu, select **set a message header**.
- Click the first instance of **Enter text**.
[See image.](#send-rule-enter-text-01)
The **message header** drawer appears.
- For the **message header** value, enter `X-Zscaler-TenantId`, then click **Save**.
[See image.](#send-rule-msg-header-text)
- Click the second instance of **Enter text**.
[See image.](#send-rule-enter-text-02)
The **message header** drawer appears.
- For the **message header** value, paste the **Key for Transport Rules** value from the ZIA Admin Portal. You copied the **Key for Transport Rules** value when you [configured the email tenant](/zia/adding-email-tenants#copied-values-for-exchange) in the ZIA Admin Portal. You can also find the value on the [Edit Email Tenant page](/zia/editing-email-tenants#copied-values-for-exchange) in the ZIA Admin Portal.
[See image.](#send-rule-msg-header-value)
- **Except if**: To ensure that mail flow rules are configured correctly and that already-inspected email is not returned to the Zscaler smart host for inspection, you need to add an exception that includes the default Allow and Block Zscaler header values. To add the exception:
- In the **Except if** drop-down menu, select **The message headers...**, then select **includes any of these words**.
- Click **Enter text** to specify the name for the header.
[See image.](#send-rule-enter-text-zsheader)
The **specify header name** drawer appears.
- For the **specify header name** value, enter `X-Zscaler-Block`, then click **Save**.
- Click **Enter words** to specify the value for the header.
[See image.](#send-rule-enter-words-zsheader)
The **specify words or phrases** drawer appears.
- For the **specify words or phrases** value, enter `1` to indicate the Block action and click **Add**, then enter `0` to indicate the Allow action and click **Add**, then click **Save**.
The configured exception appears.
[See image.](#send-rule-except-if-condition)
- (Optional) Click the **Add** icon and follow the prompts to specify any necessary exceptions to the rule (i.e., if you want to exempt specific members of your organization from email content inspection).
[See image.](#outbound-rule-set-conditions)
- Click **Next**.
- On the **Set rule settings** page, ensure that **Rule mode** is set to **Test without Policy Tips**, specify other settings for the rule as needed (i.e., severity, activation dates, etc.), then click **Next**.
- Review the rule settings, then click **Finish**.
[See image.](#outbound-rule-settings-review)
A confirmation page appears.
- Click **Done**.
You return to the **Rules** page and the new rule appears in the list.
[]![The Except if condition drop-down menu for mail flow rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Outbound-ZS-Header-text.png)
[]![The Except if condition drop-down menu for mail flow rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Outbound-ZS-Header-words.png)
[]![The Except if condition drop-down menu for mail flow rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Outbound-ZS-Header-exceptif.png)
[]![The Rules menu option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Rules-option-outbound.png)
[]![The select recipient location drawer in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Select-Recipient-Location-outbound.png)
[]![The select connector window in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Select-Connector-Office-to-Zscaler.png)
[]![The set rule conditions page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Set-Rule-Conditions-outbound-no-next.png)
[]![The Review Rule page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Rule-Review-and-Finish.png)
[]![The Enter text option for mail flow rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Rule-EnterText-01.png)
[]![The message header drawer on the New transport rule panel](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Rule-MsgHeader-Text.png)
[]![The Enter text option for mail flow rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Rule-EnterText-02.png)
[]![The message header drawer for a new transport rule in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Send-Rule-MsgHeader-Value.png)
[]After the Zscaler service inspects and processes email content, it sends the content back to the Exchange server (to the next hop address [configured on the email tenant](/zia/adding-email-tenants)). The following example shows how to configure a mail flow rule to use the default block header added by the Zscaler service to emails that trigger outbound email policy.
To learn more about how Zscaler applies headers to emails that trigger outbound email policy rules, see [Configuring Outbound Email Policy Rules](/zia/configuring-outbound-email-policy-rules).
To configure an incoming mail flow rule on Exchange to use the default Zscaler block header:
- Sign in to the [Exchange Admin Center](https://admin.exchange.microsoft.com/).
- In the left-side navigation, go to **Mail flow > Rules**.
[See image.](#mail-flow-rules-option-inbound)
The **Rules** page appears.
- On the **Rules** page, click **Add a rule > Create a new rule**.
The **New transport rule** panel opens on the **Set rule conditions** page.
-
On the **Set rule conditions** page:
- In the **Name** field, enter a name for the transport rule (i.e., `Zscaler-to-Office-Block`).
- In the **Apply this rule if** drop-down menu, select **The recipient** in the first drop-down menu, then **is external/internal** from the second drop-down menu. In the **select recipient location** drawer that opens, select **Outside the organization** from the drop-down menu, then click **Save**.
[See image.](#inbound-not-in-org)
- Also in the **Apply this rule if** section, click the **Add** icon to add a condition to the rule that specifies the name:value pair for the Zscaler block header.
The **And** drop-down menu appears.
- To specify the name:value pair for the Zscaler block header, in the **And** drop-down menu, select **The message headers...**, then select **includes any of these words**.
- Click **Enter text** to specify the name for the header.
[See image.](#receive-rule-enter-text-01)
The **specify header name** drawer appears.
- For the **specify header name** value, enter `X-Zscaler-Block`, then click **Save**.
[See image.](#receive-rule-specify-header-name)
- Click **Enter words** to specify the value for the header.
[See image.](#receive-rule-enter-words)
The **specify words or phrases** drawer appears.
- For the **specify words or phrases** value, enter `1` to indicate that the message is blocked, click **Add**, select the value, then click **Save**.
You can use the same basic process to map a custom header to an action in Exchange. For example, you can [configure an outbound email policy rule](/zia/configuring-outbound-email-policy-rules) in the ZIA Admin Portal to attach a custom header (e.g., `X-Zscaler-Encrypt:1`) to emails that trigger the policy. You can then map the custom header to the appropriate action in Exchange. To learn more, refer to the [Microsoft technical documentation](https://learn.microsoft.com/en-us/exchange/mail-flow/mail-flow).
- In the **Do the following** drop-down menu, select **Block the message**.
- In the **Select one** drop-down menu, select **reject the message and include an explanation**.
The **specify rejection reason** panel opens.
- In the **specify rejection reason** field, a message sent to recipients whose emails contain sensitive information, then click **Save**.
[See image.](#inbound-message-text)
- For the **Except if** option, specify any necessary exceptions to the rule (i.e., if you want to exempt specific members of your organization from email content inspection).
- Click **Next**.
[See image.](#inbound-rule-set-conditions)
- On the **Set rule settings** page, ensure that **Rule mode** is set to **Enforce**, specify other settings for the rule as needed (i.e., severity, activation dates, etc.), then click **Next**.
- Review the rule settings, then click **Finish**.
[See image.](#inbound-rule-settings-review)
A confirmation page appears.
- Click **Done**.
You return to the **Rules** page and the new rule appears in the list.
[]![The Rules menu option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Rules-option-inbound.png)
[]![Specify Domain Page on Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-data-loss-prevention/configuring-microsoft-exchange-zscaler-outbound-email-dlp/ZIA-Outbound-Email-Policy-Receive-Rule-Not-In-Org2.png)
[]![The Provide message text page in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Message-Text-inbound-rejection.png)
[]![Review Rule Page on Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-data-loss-prevention/configuring-microsoft-exchange-zscaler-outbound-email-dlp/ZIA-Outbound-Email-Policy-Review-Receive-Rule-Pattern2.png)
[]![The Rules option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Receive-Rule-EnterText.png)
[]![The Rules option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Receive-Rule-EnterWords.png)
[]![Rules Conditions Option on Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-data-loss-prevention/configuring-microsoft-exchange-zscaler-outbound-email-dlp/ZIA-Outbound-Email-Policy-Receive-Set-Rule-Conditions2.png)
[]![The specify header name page for rules in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Receive-Rule-Specify-Header-Name.png)
[]With connectors and mail flow rules in place, you can safely set the rule mode for [the mail flow rule you created earlier](#mail-flow-rule-outbound) that sends email to the Zscaler smart host.
To set the rule mode for the mail flow rule:
- Sign in to the [Exchange Admin Center](https://admin.exchange.microsoft.com/).
- In the left-side navigation, go to **Mail flow > Rules**.
[See image.](#mail-flow-rules-option-rule-mode)
The **Rules** page appears.
- On the **Rules** page, click the name of the mail flow rule in the list, then click **Edit**.
The information panel for the mail flow rule appears.
- On the **Rules** page, click the name of the mail flow rule in the list.
The information panel for the send connector appears.
- Click **Settings**, then click **Enforce** in the **Rule mode** section.
[See image.](#rule-mode-enforce)
- Click **Save**.
- Click **Done** to close the information panel for the mail flow rule. You return to the **Rules** page, and the rule is now enforced.
[]![The Rules menu option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Exchange-Rules-option-inbound.png)
[]![The Rule mode option in the Microsoft Exchange Admin Center](/downloads/zia/policies/outbound-email-policy/ZIA-Outbound-Email-Policy-Enforce-Mail-Flow-Rule.png)