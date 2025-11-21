# Skipping IaC Policies
Source: https://help.zscaler.com/zpc/skipping-iac-policies
PDF: https://help.zscaler.com/pdf/com/en/1412996.pdf

You can add a rule to skip the required IaC policies while scanning. You need to specify the IaC policy ID in the configuration files and add a skip comment, if required.
The following sample code is provided for you:
#zpc-skip-policy: <Policy_ID>: <Comment or Reason for the Skip>
By default, the policies can be skipped. If the administrator has disabled the option to skip a specific policy on the IaC Policies page, then the skip rule is not effective for the specific policy ID. To learn more, see [About Security Policies](/zpc/about-security-policies).
You can add a skip rule to the following templates:
- ARM
"metadata": {
"zpc-skip-policy": "ZS-AZURE-004:comment"
},
[See image.](#arm)
- Terraform
#zpc-skip-policy: ZS-AWS-00030:testing
[See image.](#terraform)
- CloudFormation JSON
"Metadata": {"zpc-skip-policy": "ZS-AWS-00018,ZS-AWS-00025"},
[See image.](#json)
- CloudFormation YAML
Metadata:
zpc-skip-policy: "ZS-AWS-00021:new comment;"
[See image.](#cftyaml)
- Kubernetes
metadata:
annotations:
zpc-skip-policy: "ZS-K8S-00006:new comment"
[See image.](#kubernetes)
[![View the skip rule for CloudFormation YAML](/downloads/zpc/iac-integrations/skipping-iac-policies/CFTYAML.png)
]
[![View the skip rule for JSON](/downloads/zpc/iac-integrations/skipping-iac-policies/JSON.png)
]
[![View the skip rule for Kubernetes](/downloads/zpc/iac-integrations/skipping-iac-policies/KubernetesYAML.png)
]
[![View the skip rule for Terraform](/downloads/zpc/iac-integrations/skipping-iac-policies/Terraform.png)
]
[![View the skip rule for ARM template](/downloads/zpc/iac-integrations/skipping-iac-policies/ARM.png)
]