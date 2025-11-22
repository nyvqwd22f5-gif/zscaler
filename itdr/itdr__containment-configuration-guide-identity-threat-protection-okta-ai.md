# Containment Configuration Guide for Identity Threat Protection with Okta AI
Source: https://help.zscaler.com/itdr/containment-configuration-guide-identity-threat-protection-okta-ai
PDF: https://help.zscaler.com/pdf/com/en/1531736.pdf

This guide provides prerequisites and instructions on configuring a containment integration for [Identity Threat Protection with Okta AI](https://help.okta.com/oie/en-us/content/topics/itp/overview.htm). Identity Threat Protection with Okta AI is a risk assessment and response solution from Okta that continuously analyzes the risk signals that are native to Okta, the risk signals from integrated security partner vendors, and your policy conditions to safeguard your organization against identity attacks.
With this integration, ITDR pushes user risk scores to Okta for Zscaler Client Connector users based on threat detection events. Based on the risk score and Okta policies, Okta can end the user’s sessions, prompt a Multi-Factor Authentication (MFA) challenge, or invoke a workflow to restore your organization's security posture. The risk score is pushed to Okta via SSF using the orchestration rules configured in the Zscaler ITDR Admin Portal.
Prerequisites
Before you configure the containment integration, make sure you have:
-
64-bit Windows 10 endpoints with a 64-bit version of Zscaler Client Connector installed. You must upgrade Zscaler Client Connector to one of the supported versions:
- 4.2.1.212 or later
- 4.3.0.202 or later
- 4.4.0.285 or later
For Zscaler-recommended best practices to deploy Zscaler Client Connector, see [Best Practices for Zscaler Client Connector Deployment](/client-connector/best-practices-zscaler-client-connector-deployment).
- An Okta account with admin privileges.
-
An Okta tenant URL obtained from the Okta Admin Console.
To obtain the Okta tenant URL, log in to the Okta Admin Console, and click the username on the top-right corner. The tenant URL is shown in the drop-down menu. To learn more, refer to the [Okta documentation](https://developer.okta.com/docs/guides/find-your-domain/main/#find-your-okta-domain).
[See image.](#okta-tenant-url-image)
Configuring Containment for Identity Threat Protection with Okta AI
Follow these steps to configure containment for Identity Threat Protection with Okta AI:
- [Step 1: Create a Security Events Provider in Okta](#create-security-events-provider-okta)
- [Step 2: Configure the Containment Integration between ITDR and Okta](#integrate-with-okta)
- [Step 3: Configure an Orchestration Rule](#orchestration-rules-okta-ssf)
[]Before setting up the integration between ITDR and Okta, a Security Events Provider must be created in Okta to receive and process the security event information shared from the ITDR Admin Portal.
To create a Security Events Provider in Okta:
- Log in to the Okta Admin Console.
- Go to **Security **> **Device Integrations **>** Receive shared signals**.
-
Click **Create stream**.
[See image.](#create-stream-button-image)
-
In the stream creation window:
- **Integration name**: Enter a name for the integration.
- **Set up integration with**: Select **Well-known URL**.
-
**Well-known URL**: Enter the following well-known URL for ITDR:
`https://zscaler.ssf.transmitter.smokescreen.io/.well-known/sse-configuration`
[See image.](#create-stream-window-image)
-
Click **Create**.
The Security Events Provider is created in Okta.
[]To configure containment integration with Okta in the ITDR Admin Portal:
- Log in to the ITDR Admin Portal.
- Go to **Orchestrate **> **Containment**.
-
Locate the **Okta (SSF)** entry in the table and click the **Edit **icon.
[See image.](#itdr-edit-icon-image)
-
In the **Okta (SSF)** window:
- Select **Enabled**.
- **Base URL**: Enter the Okta tenant URL.
[See image.](#okta-ssf-window-image)
- Click **Save**.
[]To push the user risk score to Okta based on events generated in ITDR, an orchestration rule must be created.
Manual containment from the ITDR Dashboard is not supported for Okta (SSF) containment.
To create an orchestration rule:
- Go to **Orchestrate **>** Rules**.
-
Click **Add Rule**.
[See image.](#add-rule-option-itdr)
- In the **Rule Details **window:
- **Name**: Enter a name for the orchestration rule.
- Select **Enabled**.
-
Create a rule using queries and conditions to automate the containment of users. To learn how to write queries, see [Understanding and Building Queries](/deception/v4_22/understanding-and-building-queries)[.]
[See image.](#orchestration-rule-window-general)
-
Under **Respond **> **Okta (SSF)**:
- Select **Enabled**.
- **User** **Risk Level**: Select a risk score level (**Low**, **Medium**, or **High**) that you want to be updated in Okta for a user when an event matching the configured rule condition occurs. This information is shared with Okta.
- **Risk Change Reason**: Enter the reason describing why the risk score is changed. This information is shared with Okta.
[See image.](#orchestration-rule-window-respond)
- Click **Save**.
[]
![A screenshot of Okta Admin Console highlighting the Tenant URL](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-deception-tenant-URL.png)
[]
![A screenshot of Device Integrations window wiht Create Stream button highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-deception-create-stream-button.png)
[]
![A screenshot of stream creation window](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-itdr-stream-creation.png)
[]
![A screenshot highligting the Edit icon for Okta SSF](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-identity-threat-protection-okta-ai/zscaler-itdr-containment-edit-new.png)
[]
![A screenshot of Okta (SSF) window in Zscaler Deception Admin Portal](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-deception-okta-base-url.png)
[]
![A screenshot highlighting in the Add Rule button](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-itdr-add-rule.png)
[]
![A screenshot capturing the General Section in Rule Details window](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-okta/zscaler-itdr-general-details-rule.png)
[]
![A screenshot capturing the Respond section in Rule Detials window](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-identity-threat-protection-okta-ai/zscaler-deception-okta-rule.jpg)