# Understanding ZDX Copilot with Use Cases
Source: https://help.zscaler.com/zdx/understanding-zdx-copilot-use-cases
PDF: https://help.zscaler.com/pdf/com/en/1479076.pdf

ZDX Copilot engages with you as if it were a conversational partner. It can be your teacher, ZDX expert, or assistant to enhance your digital experience by creating in-depth and knowledge-based conversations powered by AI/ML. These insights empower you with the knowledge and expertise to navigate through digital experience issues within your organization.
The following use case examples show how you can engage in conversation with ZDX Copilot:
- [Analytics](#Analytics)
- [Troubleshooting](#Troubleshooting)
- [Configuration](#Configuration)
- [Learning](#Learning)
- [Optimization](#Optimization)
[]ZDX Copilot's analytics, powered by AI/ML, creates a deep dive into granular details and overview of users and their impacted devices.
The following are examples of questions or commands for analytics:
- What is John Doe's ZDX Score for the Zoom application in the last 4 hours?
- Show me John Doe's page fetch time for SharePoint in the last 4 hours.
- Analyze John Doe's Microsoft Teams call quality issue.
- Show me the Incidents in the last 48 hours.
- Show me the Wi-Fi signal quality for John Doe.
- Analyze John Doe's Wi-Fi issue.
- Show me the number of ongoing alerts.
- Show me the number of applications impacted by alerts.
[Wi-Fi Analysis Scenario](#Wi-Fianalysis)
[]You can use ZDX Copilot to find root causes that can impact multiple users. ZDX Copilot is an expert with in-depth knowledge of finding complex correlations and patterns that require remediation.
The following are examples of questions or commands for troubleshooting:
- What can I do when I see a blackout incident with an ISP?
- For the impacted users with a low ZDX Score, what is the recommended course of action to resolve their issues?
- Why is John Doe's packet loss low?
- Troubleshoot John Doe's ZDX Score for SharePoint in the last 4 hours.
[ISP-Related Issues Scenario](#ISP-RelatedIssues)
[]ZDX Copilot provides guidance on how to create configurations within the ZDX Admin Portal. These can include alerts, probes, administration, or webhook configurations.
The following are examples of questions or commands for configuration:
- How do I onboard ZDX for my organization?
- How do I configure a webhook for OpsGenie?
- What are the steps to adding a ZDX Admin?
- Configure a Web probe for Box.
[]ZDX Copilot is an expert on ZDX and can provide answers to your knowledge-based questions to enhance your learning of ZDX.
The following are examples of questions for learning:
- What is the ZDX Score?
- How is the ZDX Score calculated?
- What is Dynamic Alerting?
- Where is my data stored?
[]You can ask ZDX Copilot for best practices and areas of focus to optimize your digital experience.
The following are examples of questions for optimization:
- What are the best practices for latency to a Private Service Edge?
- Can you find the impacted users that have a ZDX Score below 50 and propose a method of alerting?
- What probe type should I configure for Microsoft Teams?
[]
The following conversation example is a scenario where users are impacted by an ISP that is reducing their access to their organization's resources:
Admin: What is the issue with high latency on devices in the Dallas office?
ZDX Copilot: Analyzing Cloud Paths...The issue is with an ISP outage.
Admin: Do you have any recommendations?
ZDX Copilot: I suggest notifying the ISP for a resolution or rerouting traffic through an alternate ISP.
Admin: Can you compile Cloud Path data for an impacted user? I will be using this data to contact the ISP.
ZDX Copilot: Certainly. Compiling the Cloud Path data.
[]
The following conversation example is a scenario where users are impacted by their Wi-Fi instability:
Admin: There are several users reporting Wi-Fi drops. Can you identify the cause?
ZDX Copilot: Checking device telemetry...There's interference in Wi-Fi channels 6 and 11.
Admin: Which channels are currently less congested?
ZDX Copilot: Channels 1 and 13 are less congested.