# About Deploying ZPA Private Service Edges
Source: https://help.zscaler.com/zpa/about-deploying-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1484476.pdf

After you [add a ZPA Private Service Edge](/zpa/configuring-service-edges), you must deploy it. Deployment consists of installing and enrolling the ZPA Private Service Edge, which allows it to obtain a TLS client certificate that it must use to authenticate itself to the ZPA cloud. After deployment, the ZPA Private Service Edge is ready to securely connect users to App Connectors and applications.
Understanding ZPA Private Service Edge Enrollment
When a ZPA Private Service Edge is installed for the first time, it does not yet have a key pair (i.e., a local private key and a corresponding TLS client certificate). Instead, the ZPA Private Service Edge must first generate the local private key, which it encrypts using a hardware fingerprint. Then, the ZPA Private Service Edge must obtain the TLS client certificate through enrollment, which consists of the following processes:
- The ZPA Private Service Edge uses the local private key to generate a Certificate Signing Request (CSR).
- It uses the provisioning key to authenticate the CSR to the ZPA cloud. This is the [provisioning key](/zpa/about-zpa-service-edge-provisioning-keys) that you generated in the ZPA Admin Portal and provided to the ZPA Private Service Edge during installation.
- It receives a signed TLS client certificate from the ZPA cloud.
- The signed TLS client certificate is pinned to the ZPA Private Service Edge's hardware fingerprint.
Once the ZPA Private Service Edge is enrolled, it is paired with a single customer account and it cannot be enrolled again. ZPA Private Service Edges that are running in virtual machine (VM) environments should never be cloned, because the keys will no longer match the virtual hardware fingerprints.
Deploying a ZPA Private Service Edge on a Supported Platform
Before you begin a deployment, read [ZPA Private Service Edge Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites), which provides detailed information on VM image sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
The deployment process differs depending on the platform used for the ZPA Private Service Edge. Zscaler recommends that ZPA Private Service Edges be deployed in pairs, to ensure continuous availability during software upgrades. To learn more, see the [Deployment Guide for the platform](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).