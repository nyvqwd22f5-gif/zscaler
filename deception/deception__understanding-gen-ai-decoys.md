# Understanding Gen AI Decoys
Source: https://help.zscaler.com/deception/understanding-gen-ai-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531592.pdf

Generative AI (Gen AI) is an emerging attack vector. Organizations are increasingly adopting Gen AI technologies, such as large language models (LLMs) in their products, services, and internal operations. Adversaries target Gen AI infrastructure for data exfiltration, asset compromise, organizational intelligence gathering, etc. Attackers target datasets for data poisoning and data exfiltration. They also use interactive attacks such as prompt injection to target AI systems and extract valuable data.
To address these emerging risks, Zscaler Deception provides high-interaction Gen AI decoys that mimic infrastructure like chatbots, LLM servers, open-source platforms, APIs, etc., to swiftly detect attacks and deflect the attacker from compromising the real assets. By simulating realistic interactions, Gen AI decoys collect critical intelligence on attack patterns and methodologies, and provide valuable insights into malicious tactics, thereby enhancing the organization’s threat intelligence.
Deception supports the following types of Gen AI decoys:
-
**Interactive Gen AI Decoys**: Mimics common interactive Gen AI infrastructure such as chatbots, LLM servers, open-source platforms, etc. You can deploy these decoys by configuring the Gen AI service using out-of-the-box AI-based high-interaction or static applications datasets. You can configure these decoys according to your organization’s use case to generate responses based on the attacker’s intent. You can deploy interactive Gen AI decoys on:
- [Internal Networks via Internal Decoy](/deception/deploying-interactive-generative-ai-decoys#deception-gen-ai-deploy-internal-network)
- [Zero Trust Exchange via Zero Trust Network (ZPA) Decoys](/deception/deploying-interactive-generative-ai-decoys#deception-gen-ai-zpa)
- [Internet via Threat Intelligence (TI) Decoys](/deception/deploying-interactive-generative-ai-decoys#deception-gen-ai-deploy-ti)
To learn more, see [Deploying Interactive Gen AI Decoys](/deception/deploying-interactive-generative-ai-decoys).
-
**File-Based Gen AI Decoys**: Mimics resources that are used to set up local LLMs. You can create these decoys by configuring the Gen AI file datasets provided by Deception using one of the following assets:
- Endpoints via [landmine policies](/deception/about-policies)
- Azure Cloud via [storage account container decoy](/deception/creating-storage-account-container-decoy-azure) or [storage account file share decoy](/deception/creating-storage-account-file-share-decoy-azure)
- Amazon Web Services (AWS) Cloud via [S3 decoys](/deception/creating-s3-decoy-aws)
- [Network decoys](/deception/about-network-decoys) via [FTP](/deception/configuring-services-network-decoy#configuring-ftp-service) or [Share](/deception/configuring-services-network-decoy#configuring-shares-service) service
To learn more, see [Deploying File-Based Gen AI Decoys](/deception/deploying-file-based-generative-ai-decoys).
Gen AI Network Personality
Deception provides a [Gen AI decoy personality](/deception/about-network-decoy-personalities) that serves as templates to deploy Gen AI decoys via network decoys. You can use this personality when configuring [network decoys manually](/deception/about-network-decoys), or use them in a [deception strategy](/deception/about-deploy-strategy) to create decoys. To learn more, see [About Network Decoy Personalities](/deception/about-network-decoy-personalities).
[See image.](#deception-gen-ai-network-personality)
The **GenAI** icon is used across the Zscaler Deception Admin Portal to indicate Gen AI use cases and capabilities.
ThreatParse Details and Event Logs
When an adversary compromises an endpoint and attempts a data exfiltration technique to find credentials for an internally hosted LLM application (which is a Gen AI decoy), Deception detects the attack and generates event logs. It also captures the prompt and automatically categorizes it as malicious, etc. for further investigation using the Gen AI Malicious Input Prompt ThreatParse rule. In the Gen AI Malicious Input Prompt ThreatParse rule, the classification of whether the prompt is malicious and the categorization of the prompt are determined by enriching data using Deception AI. Hence, the values for the **gen ai malicious** and **gen ai malicious category** fields might be inaccurate. Verify the details for accuracy or completeness before making any decisions.
[See image.](#deception-gen-ai-threatparse)
After the threat is detected, the configured [orchestration rules](/deception/about-orchestration-rules) automatically contain the attack and block the compromised user from accessing any private applications in the environment.
To learn more, see [Viewing ThreatParse Details](/deception/viewing-threatparse-details) and [About Event Logs](/deception/about-event-logs).
The responses or content generated by the Deception AI is for informational purposes only. The content is prone to inaccuracy and AI hallucinations. Verify the details for accuracy or completeness before making any decisions.
[]![View Gen AI network decoy personality](/downloads/deception/deceive/gen-ai-decoys/understanding-gen-ai-decoys/zscaler-deception-network-personality-gen-ai.png)
[]![View ThreatParse details](/downloads/deception/deceive/gen-ai-decoys/understanding-gen-ai-decoys/zd-rn-auto-generated.png)