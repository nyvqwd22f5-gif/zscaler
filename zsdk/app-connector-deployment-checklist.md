# App Connector Deployment Checklist
Source: https://help.zscaler.com/zsdk/app-connector-deployment-checklist
PDF: https://help.zscaler.com/pdf/com/en/1508971.pdf

The App Connector Deployment Checklist helps you understand what actions are mandatory and what Zscaler recommends.
[](/zsdk/app-connector-deployment-prerequisites)
-
-
| **Action** | **Notes** | **Priority** |
| ---------- | --------- | ------------ |
| Verify that all App Connectors meet the minimum CPU, memory, and disk-sizing requirements. | To learn more, see App Connector Deployment Prerequisites. | Mandatory |
| Change the App Connector password; do not leave the default password. | Use the command `$ passwd`. | Highly Recommended |
| Create a minimum of 2 App Connectors. Use the N+1 rule for redundancy. | For example, if you have:One 2 GbpsThree 500 MbpsThen using the N+1 rule indicates that you need a minimum of 4 App Connectors. | Highly Recommended |
| Deploy the App Connectors on an internal network segment: one App Connector without a public IP address and one with a default route to the internet. |  | Highly Recommended |
| Place the App Connectors as close as possible to the API gateway or servers that host your mobile application. |  | Recommended |
| App Connectors must have unrestricted access to the application, with no protocol or port limitations or restrictions, to include ICMP access. |  | Recommended |