# Evaluating Landmine Policies
Source: https://help.zscaler.com/deception/evaluating-landmine-policies
PDF: https://help.zscaler.com/pdf/com/en/1531296.pdf

You can evaluate landmine policies and generate a policy report. This report consists of landmine deception modules that are deployed on an endpoint based on system hostnames, logged-in users, policy selection criteria, etc.
To evaluate landmine policies:
- Log in to the Zscaler Deception Admin Portal.
- In the left-side navigation, go to **Deceive** > **Landmine** > **Policies**.
- Click **Evaluate Policies**.
[See image.](#zscaler-deception-evaluate-policy)
-
In the **Landmine Policy Evaluation** window:
- **User ID**: Enter the user ID that must be used to generate the sample policy.
- **Hostname**: Enter the hostname that must be used to generate the sample policy.
- **OS**: Select the operating system for which the sample policy must be generated.
- **Agentless**: Enable to generate sample policy for agentless environments.
- **Group**: (Optional) Enter the active directory group that must be used to generate the sample policy.
- **Computer OU**: (Optional) Enter the organizational unit (OU) of the endpoints that must be used to generate the sample policy.
- **User OU**: (Optional) Enter the organizational unit (OU) of the users that must be used to generate the sample policy.
- **Domain**: (Optional) Enter the domain name of the endpoint that must be used to generate the sample policy.
- **Display Name**: (Optional) Enter the display name of the user that must be used to generate the sample policy.
- **Dynamic Rules**: (Optional) Click **Add **to configure a dynamic rule that must be used in the sample policy.
[See image.](#zscaler-deception-landmine-policy-evaluation-window)
-
Click **Get Sample Policy**.
[See image.](#zscaler-deception-sample-landmine-policy)
A sample policy report is generated. If a user or system matches the selection criterion of two or more policies, the report shows the deception modules specified by all of the matching policies.
[]![Evaluate a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/policy-management/evaluating-landmine-policies/deception-landmine-evaluate-policy.png)
[]![Generate sample landmine policy report](/downloads/deception/deceive/landmine-decoys/policies/policy-management/evaluating-landmine-policies/zscaler-deception-landmine-policy-evaluation-new.png)
[]![Sample landmine policy report](/downloads/deception/product-documentation/deceive/endpoint-decoys/policies/evaluating-landmine-policies/zscaler-deception-landmine-sample-policy-results.png)