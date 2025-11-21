# Viewing Orchestrator Status
Source: https://help.zscaler.com/dspm/viewing-orchestrator-status
PDF: https://help.zscaler.com/pdf/com/en/1487776.pdf

DSPM regularly scans the data stores (databases, virtual machines, etc.) within your target accounts by leveraging the [orchestrator ](/dspm/understanding-orchestrator)that is deployed in your account during the onboarding process. The orchestrator instance launches [scanner instances](/dspm/understanding-scanner-instances) in the regions where the target account data stores exist and scans the data.
On the **Overview** tab, you can view the following status types for the orchestrator connection and configuration:
- **DSPM Connection Status**: The connection status between the orchestrator and DSPM.
- **Successful**: The orchestrator instance is connected to DSPM successfully.
- **Failed**: The orchestrator instance is unable to establish a connection with DSPM.
- **Waiting for connection**: The orchestrator template is not yet deployed in the cloud service provider (CSP).
- **Configuration Status**:** **Indicates whether all resources are available and permissions are configured in the orchestrator account. The configuration status can be one of the following:
- **Successful**: All resources are successfully deployed and permissions are configured in the orchestrator account.
- **Warning**: Some resources or permissions are unavailable, tampered with, or not visible.
- **Failed**: The orchestrator instance cannot launch scanner instances, or some roles and permissions are missing in the orchestrator account.
- **Pending**: The orchestrator account has changed or the template is yet to be deployed in the CSP.
- **Last Connected**: The last time the orchestrator instance was successfully connected with DSPM.
![Viewing the Orchestrator Status](/downloads/dspm/administration/cloud-account-management/viewing-orchestrator-status/dspm-orchestrator-status.png)