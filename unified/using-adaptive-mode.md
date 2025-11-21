# Using Adaptive Mode
Source: https://help.zscaler.com/zdx/using-adaptive-mode
PDF: https://help.zscaler.com/pdf/com/en/1379636.pdf

Adaptive mode selects the best protocol for the cloud path probe to reach the destination. Adaptive mode tries the TCP, UDP, and ICMP protocols for each run, and picks the best available protocol for the probe. The best protocol for each leg in the cloud path is selected via an auto-discovery process and results in a combination of more than one protocol for the cloud path.
Minimum versions of Zscaler Client Connector and ZDX Module are required. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
Adaptive Mode Process
You can select Adaptive mode when configuring a cloud path probe for either a predefined or custom application. To learn more, see [Configuring a Probe](/zdx/configuring-probe) and [Best Practices in Operationalizing ZDX](https://www.zscaler.com/resources/white-papers/best-practices-operationalizing-zdx.pdf).
[See image](#AdaptiveMode)
The following factors are considered for detecting the best protocol for each leg:
- Least latency to the destination (egress/server)
- Least loss to the destination (egress/server)
If Adaptive detection fails, ICMP is used for the leg to the egress router, and TCP is used for the path to the destination server.
Results in the Cloud Path
The protocol used is visible in the Cloud Path section on the user details page. To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[]![Adaptive Mode in Probe Configuration ](/downloads/zdx/about-adaptive-mode/zdx_Adaptive.png)