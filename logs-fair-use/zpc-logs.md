# ZPC Logs
Source: https://help.zscaler.com/logs-fair-use/zpc-logs
PDF: https://help.zscaler.com/pdf/com/en/1403221.pdf

Cloud configuration data, Cloud Service Provider (CSP) activity audit logs, cloud network logs, and cloud user directory information are processed by Zscaler in connection with your organization's use of Zscaler Posture Control (ZPC).
Depending on the acquired subscription and permissions granted by the customer, the following logs are also processed:
- For customers opting for the vulnerability scanning subscription (ZPC Vulnerability or ZPC Advanced), Zscaler further analyzes the content of CSP-hosted virtual machines operating system drive and container images. (subject to customer configuration and enablement)
- For customers opting for the Infrastructure as Code (ZPC IaC or ZPC Advanced) subscription, Zscaler further analyzes the content of IaC scripts in the user code repositories or CI/CD tools. (subject to customer configuration and enablement)
All logs that describe active cloud resources or issues are retained by Zscaler for the duration of the subscription. Once the resources are no longer present in the CSP, ZPC maintains the logs for a rolling period of 180 days during the term of the subscription. When the subscription term ends or expires, Zscaler deletes the logs after the 180-day retention cycle. By accessing the ZPC service, you provide Zscaler the right to process, use, reproduce, store, modify, and display the information from logs.
During the deployment process, you can choose to have the logs stored in either the United States or the European Union.