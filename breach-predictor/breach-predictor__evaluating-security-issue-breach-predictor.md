# Evaluating a Security Issue with Breach Predictor
Source: https://help.zscaler.com/breach-predictor/evaluating-security-issue-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1500466.pdf

By analyzing huge amounts of data, Zscaler Breach Predictor can eliminate blind spots and give you a clear picture of the threat landscape across your organization. More importantly, it’s designed to proactively anticipate potential threats, helping to eliminate the noise associated with reactive tools. With Breach Predictor’s early warnings, you can anticipate lateral threat movement before it happens. So it’s important to pay close attention to your organization’s placement on the [MITRE ATT&CK  matrix](/breach-predictor/what-zscaler-breach-predictor#enhanced-attack-visibility).
As you explore Breach Predictor findings, keep in mind that the idea is always the same: work from right to left on the MITRE ATT&CK  matrix. As a threat moves further to the right in the matrix, your organization is at a higher risk of a data breach. More specifically, as threats move to the Lateral Movement and Data Loss stages, quick action becomes more essential. You can easily determine whether a technique has actually been reached, or whether Breach Predictor is predicting its advancement. Some events are identified as "possible," meaning that they might have happened but were not captured as part of Breach Predictor's threat detection.
To better understand your company’s placement on the MITRE ATT&CK  matrix, see [Analyzing the MITRE ATT&CK  Mapping Findings](/breach-predictor/analyzing-mapping-findings).
The following sections provide general guidance on what to do when Breach Predictor identifies threats in your organization, as well as an overview for each of the major stages of the MITRE ATT&CK  framework:
- [Basic Steps When a Threat Is Identified at Any Stage](#basic-steps-for-threat)
- [Overview: Discover Attack](#overview-discover)
- [Overview: Compromise](#overview-compromise)
- [Overview: Lateral Movement](#overview-lateral)
- [Overview: Data Loss](#overview-data-loss)
[]
- Look at the Overall Breach Probability score. A higher Overall Breach Probability score indicates movement into critical stages by threat actors, as well as a high number of users who are affected.
-
Focus attention on the data on the **Attack path** tab on the **Findings** page. Instead of focusing on granular data from individual user logs, maintain a clear view of the bigger security picture by tracking the attack path of each malware family. Use the [Events page](/breach-predictor/about-events) to gain insight into how multiple threat families are affecting your organization.
- On the **MITRE ATT&CK  Mapping** page, look at where the malware family sits on the matrix. In the following example, the smashbrowser malware family shows activity at the **Initial Access** technique in the **Discover Attack** stage.
[See image.](#attack-path-data)
- Click the **Attack path** tab to determine whether the technique has been observed, or whether it's possible or predicted. In this example, Breach Predictor shows that the smashbrowser malware family has achieved the **Resource Development** and **Initial Access** techniques; however, Breach Predictor predicts the path the smashbrowser malware family is likely to take into other MITRE ATT&CK  techniques.
[See image.](#smashbrowser-example)
- In this scenario, click the name of the malware family, then click the **Users** tab to open a page that shows specific information about the users affected by the malware family.
[See image.](#show-affected-users)
- Click **Update Policy** to update your policies. With the recommendations that Breach Predictor provides, you can file [Jira Request tickets](/breach-predictor/requesting-updates-zscaler-breach-predictor) for policy updates.
[See image.](#copy-url)
[]![Attack Path Data in Zscaler Breach Predictor](/downloads/breach-predictor/25.04/ZBP-EvaluateSecurityIssue_MITREATTACK.png)
[]![Malware Family Affected Users in Zscaler Breach Predictor](/downloads/breach-predictor/25.04/ZBP-EvaluateSecurityIssue_AffectedUsers.png)
[]![Malware Family Example in Zscaler Breach Predictor](/downloads/breach-predictor/25.04/ZBP-EvaluateSecurityIssue_AttackPath.png)
[]![The Update Policy Option in Zscaler Breach Predictor](/downloads/breach-predictor/25.04/ZBP-EvaluateSecurityIssue_UpdatePolicyButton.png)
[]Placement in the Discover Attack stage indicates that threat actors are surveilling your system by gathering information, scanning systems, and developing resources to infiltrate your network.
The Discover Attack stage includes these MITRE ATT&CK  techniques:
- [Reconnaissance](https://attack.mitre.org/tactics/TA0043/)
- [Resource Development](https://attack.mitre.org/tactics/TA0042/)
[]Placement in the Compromise stage indicates that threat actors have gained an initial foothold within your network. From there, they can execute code, persist through attempted interruptions, gain root access, and use multiple methods to evade detection.
The Compromise stage includes these MITRE ATT&CK  techniques:
- [Initial Access](https://attack.mitre.org/tactics/TA0001/)
- [Execution](https://attack.mitre.org/tactics/TA0002/)
- [Persistence](https://attack.mitre.org/tactics/TA0003/)
- [Privilege Escalation](https://attack.mitre.org/tactics/TA0004/)
- [Defense Evasion](https://attack.mitre.org/tactics/TA0005/)
[]Placement in the Lateral Movement stage indicates that a threat actor is actively attempting to gain access to account names and passwords, is performing different types of discovery on your network, might start moving more rapidly laterally to later techniques, and has begun to collect data from your network and resources. When threat actors have achieved this stage, your organization is dangerously close to a full data breach.
The Lateral Movement stage includes these MITRE ATT&CK  techniques:
- [Credential Access](https://attack.mitre.org/tactics/TA0006/)
- [Discovery](https://attack.mitre.org/tactics/TA0007/)
- [Lateral Movement](https://attack.mitre.org/tactics/TA0008/)
- [Collection](https://attack.mitre.org/tactics/TA0009/)
[]When your organization is identified as being in the Data Loss stage, you are in danger of a data breach and must take action immediately. At this stage, threat actors are trying to communicate with compromised systems, steal data, and control or destroy your systems and data.
The Data Loss stage includes these MITRE ATT&CK  techniques:
- [Command and Control](https://attack.mitre.org/tactics/TA0011/)
- [Exfiltration](https://attack.mitre.org/tactics/TA0010/)
- [Impact](https://attack.mitre.org/tactics/TA0040/)