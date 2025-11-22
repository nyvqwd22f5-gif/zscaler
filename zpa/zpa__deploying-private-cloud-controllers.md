# Deploying Private Cloud Controllers
Source: https://help.zscaler.com/zpa/deploying-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1507431.pdf

After you [add a Private Cloud Controller](/zpa/configuring-private-cloud-controllers), you must deploy it. Deployment consists of installing and enrolling the Private Cloud Controller, which allows it to obtain a TLS client certificate that it must use to authenticate itself to the ZPA cloud. After deployment, the Private Cloud Controller is ready to act as a per-tenant controller for users, ZPA Private Service Edges, and App Connectors to leverage when the ZPA cloud is not available or reachable.
Understanding Private Cloud Controller Enrollment
When a Private Cloud Controller is installed for the first time, it does not yet have a key pair (i.e., a local private key and a corresponding TLS client certificate). Instead, the Private Cloud Controller must first generate the local private key, which it encrypts using a hardware fingerprint. Then, the Private Cloud Controller must obtain the TLS client certificate through enrollment, which consists of the following processes:
- The Private Cloud Controller uses the local private key to generate a Certificate Signing Request (CSR).
- It uses the provisioning key to authenticate the CSR to the ZPA cloud. This is the [provisioning key](/zpa/about-private-cloud-controller-provisioning-keys) that is generated in the ZPA Admin Portal and provided to the Private Cloud Controller during installation.
- It receives a signed TLS client certificate from the ZPA cloud.
- The signed TLS client certificate is pinned to the Private Cloud Controller's hardware fingerprint.
After the Private Cloud Controller is enrolled, it is paired with a single customer account and cannot be enrolled again.
Deploying a Private Cloud Controller on a Supported Platform
Before you begin a deployment, see [Private Cloud Controller Deployment Prerequisites](/zpa/private-cloud-controller-deployment-prerequisites) which provides detailed information on Private Cloud Controller sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
The deployment process differs depending on the platform used for the Private Cloud Controller. Zscaler recommends that Private Cloud Controllers be deployed in pairs to ensure continuous availability during software upgrades. To learn more, see the [Private Cloud Controller Deployment Guide for Linux](/zpa/private-cloud-controller-deployment-guide-linux).