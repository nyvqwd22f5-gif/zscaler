# Evaluating Threat Detection Policies
Source: https://help.zscaler.com/itdr/evaluating-threat-detection-policies
PDF: https://help.zscaler.com/pdf/com/en/1531681.pdf

You can evaluate [threat detection policies](/itdr/about-threat-detection) and generate a threat detection policy report. This report consists of endpoint [ITDR attack detection modules](/itdr/configuring-itdr-active-directory) that are deployed on an endpoint based on system hostnames, logged-in users, [policy selection criteria](/itdr/specifying-selection-criterion), etc.
To evaluate threat detection policies:
- Go to **ITDR** > **Manage** > **Threat Detection**.
- Click **Evaluate Policies**.
[See image.](#zscaler-deception-evaluate-policy)
-
In the **Threat Detection Policy Evaluation** window:
- **User ID**: Enter the user ID that must be used to generate the sample policy.
- **Hostname**: Enter the hostname that must be used to generate the sample policy.
- **OS**: View the operating system for which the sample policy is generated.
- **Group**: (Optional) Enter the Active Directory (AD) group that must be used to generate the sample policy.
- **Computer OU**: (Optional) Enter the organizational unit (OU) of the endpoints that must be used to generate the sample policy.
- **User OU**: (Optional) Enter the organizational unit (OU) of the users that must be used to generate the sample policy.
- **Domain**: (Optional) Enter the domain name of the endpoint that must be used to generate the sample policy.
- **Display Name**: (Optional) Enter the display name of the user that must be used to generate the sample policy.
- **Dynamic Rules**: (Optional) Click **Add **to [configure a dynamic rule](/itdr/specifying-selection-criterion#dynamic-rule) that must be used in the sample policy.
[See image.](#zscaler-deception-landmine-policy-evaluation-window)
-
Click **Get Sample Policy**.
[See image.](#zscaler-deception-sample-landmine-policy)
A sample policy report is generated. If a user or system matches the [selection criterion](/itdr/specifying-selection-criterion) of two or more policies, the report shows the ITDR attack detection modules specified by all of the matching policies.
[]![Evaluate a threat detection policy](/downloads/itdr/threat-detection-policies/evaluating-threat-detection-policies/itdr-threat-detection-evaluate-policies.png)
[]![Generate sample threat detection policy report](/downloads/itdr/threat-detection/evaluating-endpoint-policies/itdr-evaluate-threat-detection-policy-window.png)
[]![Sample threat detection policy report](/downloads/itdr/threat-detection/evaluating-endpoint-policies/itdr-threat-detection-generated-policy.png)