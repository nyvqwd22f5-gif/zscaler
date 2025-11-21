# Understanding Zscaler Breach Predictor
Source: https://help.zscaler.com/breach-predictor/understanding-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1500436.pdf

Zscaler Breach Predictor represents a fundamental shift in approach, from a security posture focused on alerts and reactivity to one focused on proactively addressing threats based on predictability of attacks. Breach Predictor is designed to supplement, rather than replace, reactive security tools.
Reactive tools provide necessary urgency for imminent threats. But one of the main problems with a reactive approach is that you’re typically responding to multiple alerts from multiple products, all based on an event that’s already happened. By that point, the threat has already moved ahead to other stages. With Breach Predictor’s predictive intelligence, you can shore up your problem policies now so that threats don't move to the next stage.
Fundamentally, Breach Predictor is designed to give your organization more time to make informed decisions, instead of being pressured to act quickly based on an accumulation of alerts. Breach Predictor provides threat context and information about the specific policies that enabled the activity to occur, enabling Security Operations Center (SOC) teams to make changes based on policy visibility and recommendations.
Breach Predictor works by consuming and analyzing vast amounts of data from multiple sources and then using that analysis to provide visibility, recommendations, and reduced remediation time to improve your overall security posture. The following illustration provides a high-level overview of how Breach Predictor works:
[See image.](#how-breach-predictor-works)
At a high level, Breach Predictor uses the following basic workflow to identify and map threats:
- [1. Track substantial amounts of data from multiple sources.](#track-data)
- [2. Use generative AI to analyze data.](#use-gen-ai)
- [3. Draw conclusions to provide visibility and guidance.](#draw-conclusions)
Breach Predictor’s intuitive UI presents a large amount of data in an easy-to-understand format, from the Overall Breach Probability score to provide an immediate assessment of your organization’s threat landscape, to Sankey charts and MITRE ATT&CK  findings tables to provide specific information about user vulnerability and the malware families present in your organization.
To learn more about how to navigate the different areas of Breach Predictor, see [Accessing and Navigating Zscaler Breach Predictor](/breach-predictor/accessing-and-navigating-zscaler-breach-predictor).
[]To achieve its predictive intelligence, Breach Predictor examines a large amount of data from an array of sources:
- Logs from Zscaler Internet Access (ZIA), Zscaler Sandbox, and CrowdStrike
- Threat intelligence from [Zscaler ThreatLabz](https://threatlabz.zscaler.com/) that is focused on building attack indicators
- Existing policy recommendations based on peers and best practices
[]![Illustration of How Zscaler Breach Predictor Works](/downloads/breach-predictor/25.06/Diagram_Breach-Predictor_How-ZBP-Works.png)
[]Breach Predictor uses generative AI to analyze vast amounts of data to determine patterns and behaviors, recognizing new threats and Indicators of Compromise (IoCs) emerging in your environment. It also provides probability for where threats will move so that you can take meaningful action to stop threats and prevent future attacks.
[]Breach Predictor is designed to provide easy-to-understand visibility and guidance based on its analysis of disparate data sources, providing clarity at a level that might otherwise be missed.