# Deploying Interactive Gen AI Decoys
Source: https://help.zscaler.com/deception/deploying-interactive-gen-ai-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531593.pdf

[Watch a video on Deploying Interactive Gen AI Decoys.](https://fast.wistia.net/embed/iframe/hmy8a4j6dl)
Interactive generative AI (Gen AI) decoys mimic common Gen AI infrastructure such as Chatbots, LLM servers, open-source applications, APIs, etc. You can deploy Gen AI decoys on the internal network, Zero Trust Exchange, and the internet via ZPA, Internal, and Threat Intelligence (TI) using out-of-the-box Gen AI high-interaction or static application datasets.
The following application datasets are available to create interactive Gen AI decoys:
| Application | Type |
| ----------- | ---- |
| ChatBot | High-interaction |
| Apache Airflow | Static |
| Bento Frontend | Static |
| ClearML | Static |
| GitLab GenAI | Static |
| JupyterHub | Static |
| Metaflow | Static |
| MLflow | Static |
| Ray Serve | Static |
To learn more, see [About Static Application Datasets](/deception/about-static-application-datasets) and [About High-Interaction Containers](/deception/about-high-interaction-containers).
You can deploy up to three interactive Gen AI decoys using the high-interaction dataset with ZPA and Internal decoys combined. However, the number of Gen AI decoys you can create using static datasets depends on your organization's licensing agreement. To learn more, see [Ranges & Limitations](/deception/ranges-and-limitations).
Interactive Gen AI decoys that are deployed using high-interaction datasets don't support the TLS protocol. When configuring these decoys, don't use TLS ports (e.g., 443).
- [Deploying Gen AI Decoys on Internal Networks via Internal Decoys](#deception-gen-ai-deploy-internal-network)
- [Deploying Gen AI Decoys on the Zero Trust Exchange via Zero Trust Network (ZPA) Decoys](#deception-gen-ai-zpa)
- [Deploying Gen AI Decoys on the Internet via Threat Intelligence (TI) Decoys](#deception-gen-ai-deploy-ti)
[]When configuring the [Internal decoys](/deception/about-network-decoys), make sure you configure the [Gen AI service](/deception/configuring-services-network-decoy#deception-config-gen-ai-service-network-decoys), which uses preconfigured AI-based high-interaction or static application datasets. Before creating an Internal decoy, make sure that the [prerequisites](/deception/creating-internal-network-decoy#zd-deception-internal-decoy-prerequisite) are met.
To deploy a Gen AI decoy on internal networks via Internal decoys:
-
Create an [Internal decoy](/deception/creating-internal-network-decoy#zd-deception-create-internal-decoy) with the following **General** settings.
[See image.](#deception-gen-ai-internal-decoy-general-image)
-
On the **Services **tab, enable **GenAI **and then** **configure the [Gen AI** **service](/deception/configuring-services-network-decoy#deception-config-gen-ai-service-network-decoys) using the Gen AI static or high-interaction application dataset that the Internal decoy will host.
[See image.](#deception-gen-ai-config-service-internal)
The Gen AI decoy is deployed on the internal network via an Internal decoy.
[See image.](#deception-gen-ai-decoy-deployed-internal)
[]When configuring the [Zero Trust Network (ZPA) decoy](/deception/about-network-decoys), make sure you configure the [Gen AI** **service](/deception/configuring-services-network-decoy#deception-config-gen-ai-service-network-decoys), which uses preconfigured AI-based high-interaction or static application datasets. Before creating a Zero Trust Network decoy, make sure that the [prerequisites](/deception/creating-zero-trust-network-decoy#zd-deception-zpa-decoy-prerequisite) are met.
To deploy the Gen AI decoy on the Zero Trust Exchange via a Zero Trust Network decoy:
-
Create a [Zero Trust Network decoy](/deception/creating-zero-trust-network-decoy#zd-deception-create-zpa-decoy) with the following **General** settings.
[See image.](#deception-gen-ai-zpa-decoy-config)
-
On the **Services **tab, enable **GenAI** and then configure the [gen AI** **service](/deception/configuring-services-network-decoy#deception-config-gen-ai-service-network-decoys) using the Gen AI static or high-interaction application dataset that the Zero Trust Network decoy will host.
[See image.](#deception-config-gen-ai-ser-zpa)
The Gen AI decoy is successfully deployed on the Zero Trust Exchange via a Zero Trust Network decoy.
[See image.](#deception-gen-ai-decoy-deployed-zpa)
[]You can deploy internet-facing Gen AI decoys via [TI decoys](/deception/about-threat-intelligence-decoys) that heuristically detect threats that specifically target Gen AI infrastructure. When configuring the TI decoy, make sure to select a preconfigured Gen AI static dataset. Before creating a TI decoy, make sure that the [prerequisites](/deception/creating-threat-intelligence-decoy#zd-deception-ti-decoys-prerequisites) are met.
Out-of-the-box Gen AI high-interaction datasets are not supported for TI decoys.
To deploy internet-facing Gen AI decoys via TI decoys:
- Create a [TI decoy](/deception/creating-threat-intelligence-decoy#zd-deception-create-ti-decoy) with the following configuration:
-
Click **Add Decoy** > **Static Application**.
[See image.](#deception-gen-ai-ti-select-static-application)
-
On the **Static Application Decoy Details** page, for **Choose static application**, select a Gen AI static application dataset from the drop-down menu.
[See image.](#deception-gen-ai-ti-static-dataset)
- Click **Submit**.
The internet-facing Gen AI decoy is successfully deployed via a TI decoy.
[See image.](#deception-gen-ai-deployed-ti)
[]![Configure Internal decoy general settings](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-gen-ai-config-internal-decoy-general-settings-2.png)
[]![Configure the Gen AI service for Internal Decoys](/downloads/deception/deceive/generative-ai-decoys/deploying-interactive-generative-ai-decoys/zscaler-gen-ai-internal-decoy-zpa-service-hi-interaction-3.png)
[]![Gen AI decoy deployed via Internal network](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-gen-ai-internal-decoy-deployed-3.png)
[]![Configure a Zero Trust Network General settings](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-deception-gen-ai-config-zpa-general-settings.png)
[]![Configure the Gen AI service for ZPA decoys](/downloads/deception/deceive/generative-ai-decoys/deploying-interactive-generative-ai-decoys/zscaler-deception-gen-ai-zpa-decoy-service-hi-interaction-4.png)
[]![Gen AI decoy deployed via ZPA decoys](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-gen-ai-zpa-decoy-deployed-4.png)
[]![Select a static application](/downloads/deception/deceive/threat-intelligence-decoys/creating-threat-intelligence-decoy/zscaler-deception-gen-ai-ti-static-dataset.png)
[]![Configure TI decoy with Gen Ai static dataset](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-deception-gen-ai-ti-config-2.png)
[]![Gen AI decoy deployed via TI decoys](/downloads/deception/deceive/gen-ai-decoys/creating-and-deploying-web-gen-ai-decoys/zscaler-deception-gen-ai-ti-deployed-1.png)