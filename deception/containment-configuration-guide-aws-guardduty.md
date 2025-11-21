# Containment Configuration Guide for Amazon GuardDuty
Source: https://help.zscaler.com/deception/containment-configuration-guide-aws-guardduty
PDF: https://help.zscaler.com/pdf/com/en/1531615.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Amazon GuardDuty to contain and isolate detected attackers.
With this integration, Deception strengthens cloud security by automatically preventing known attacker IP addresses from accessing AWS resources. When Deception detects malicious activity, it sends the source IP address to the Amazon GuardDuty threat list. Amazon GuardDuty then uses this information to block or flag any traffic originating from these IP addresses, helping to reduce the risk of compromise and enhance threat response across your AWS environment.
Prerequisites
Before you configure Amazon GuardDuty, ensure that you have:
- AWS accounts with Amazon GuardDuty enabled.
- Obtained the Detector ID for each region within an AWS account that must be protected.
Configuring Containment Integration with Amazon GuardDuty
Follow these steps to integrate Amazon GuardDuty:
- [Step 1: Configure the Containment Integration Between Deception and Amazon GuardDuty](#containment-integration)
- [Step 2: Configure Orchestration Rule or Manually Contain Detected Attackers](#orchestration-and-manual-containment)
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-blocked-identities).
- []Sign in to the [AWS Management Console](https://aws.amazon.com/console/).
- Click your username in the top-right corner.
-
Copy the 12-digit account ID displayed in the drop-down menu.
[See image.](#aws-account-id-image)
- Ensure that the proper region is selected and go to the GuardDuty service.
-
In the left-side navigation, click **Settings **and copy the **Detector ID**.
[See image.](#aws-detector-id-image)
Ensure that you copy Detector IDs for all accounts and regions that must be protected from malicious IP addresses.
- In the Zscaler Deception Admin Portal, go to **Orchestrate **> **Containment**.
-
In the table, locate **AWS GuardDuty (Attacker IPs) **and click the **Edit **icon.
[See image.](#edit-icon-aws-guard-duty)
- In the **AWS GuardDuty (Attacker IPs) **configuration window:
- **Enabled**: Select to enable the containment integration.
-
Click **Add **to enter the following details of an AWS account:
- **Name**: Enter a name for the account.
- **AWS Account** **ID**: Enter the account ID copied from the AWS Management Console.
- **Region**: Select the region for the AWS account that you want to protect from malicious IP addresses.
- **Detector ID**: Enter the detector ID for the specific region copied from the AWS Management Console.
[See image.](#aws-guard-duty-configuration-window)
Ensure that you have configured all accounts and regions with the respective Detector IDs.
-
Click **Save.**
The message indicating GuardDuty is ready appears along with the **Show Commands** option.
-
Click **Show Commands**.
[See image.](#aws-guard-duty-show-commands)
-
Copy each command to create a role, an access permission for the role, an S3 bucket to store the threat IP address list, and a policy to allow the role to access the S3 bucket.
[See image.](#guard-duty-commands-list)
-
Go to AWS Management Console and launch AWS CloudShell for each region and run the commands.
The required role, access permissions, S3 bucket, and policies are created.
[]You can contain detected attackers automatically by creating an orchestration rule or manually from the [Investigate page](/deception/understanding-investigate-module).
- [Create a rule.](#containment-rule)
- [Take action from the Investigate page.](#containment-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#add-rule-button)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#general-rule-details)
-
Under **Respond > AWS GuardDuty**.
- Select **Enabled**.
- Select the name of the Amazon GuardDuty account.
[See image.](#respond-rule)
-
Click **Save**.
The attackers' IP addresses are added to the Amazon GuardDuty's Threat IP list, and any traffic originating from the IP address is blocked by AWS.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The event details pane opens.
-
Click **Actions**.
[See image.](#actions-button-investigate)
A list of actions that you can take to remediate the threat appears.
-
Click **Contain with AWS GuardDuty**.
[See image.](#contian-with-guard-duty-option)
-
In the **Contain with AWS GuardDuty** window, select the AWS account name from the **Name **drop-down menu, and click **Contain**.
[See image.](#contain-with-guard-duty-window)
The attackers' IP addresses are added to the Amazon GuardDuty's Threat IP list, and any traffic originating from the IP address is blocked by AWS.
[]![AWS Management Console with Account ID highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-itdr-aws-account-id.png)
[]![Amazon GuardDuty Settings with Detector ID highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-itdr-detector-id.png)
[]![A list of containment integrations with the Amazon GuardDuty highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-containment-list-aws-guardduty.png)
[]![Configuration window of Amazon GuardDuty Integration](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-aws-guardduty-details.png)
[]![Amazon GuardDuty Configuration Window with the option to list commands highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-aws-guardduty-details-show-commands.png)
[]![A list of AWS CloudShell commands for Amazon GuardDuty integration](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-itdr-commands.png)
[]![Orchestration Rules page with the Add Rule option highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-add-rule%20(1).jpg)
[]![Rule Details window with a typical General section configurations](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-itdr-aws-rule.png)
[]![Response section configuration for AWS GuardDuty in Rule Details window](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-rule-aws-guard-duty.png)
[]![Investigate page with the Actions menu highlighted](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/zscaler-deception-itdr-actions-button.png)
[]![Option to contain with AWS GuardDuty highlighted on the Investigate page](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-contian-with-guardduty-option.png)
[]![Containment window for AWS Guard Duty](/downloads/deception/orchestrate/containment-integrations/containment-configuration-guide-aws-guard-duty/deception-manual-containment-guardduty.png)