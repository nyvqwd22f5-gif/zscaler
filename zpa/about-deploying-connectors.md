# About Deploying App Connectors
Source: https://help.zscaler.com/zpa/about-deploying-connectors
PDF: https://help.zscaler.com/pdf/com/en/1483721.pdf

After you [add an App Connector](/zpa/about-connectorprovisioningwizard), you must deploy it. Deployment consists of installing the App Connector and also enrolling the App Connector, which allows the App Connector to obtain a TLS client certificate that it must use to authenticate itself to the ZPA cloud. After deployment, the App Connector is ready to securely connect users to applications.
Understanding App Connector Enrollment
When an App Connector is installed for the first time, it does not yet have a key pair (i.e., a local private key and a corresponding TLS client certificate). Instead, the App Connector must first generate the local private key, which it encrypts using a hardware fingerprint. Then, the App Connector must obtain the TLS client certificate through enrollment, which consists of the following processes:
- The App Connector uses the local private key to generate a Certificate Signing Request (CSR).
- It uses the [provisioning key](/zpa/about-connectorprovisioning) to authenticate the CSR to the ZPA cloud. This is the provisioning key which you generated in the ZPA Admin Portal and provided to the App Connector during installation.
- It receives a signed TLS client certificate from the ZPA cloud.
- The signed TLS client certificate is pinned to the App Connector's hardware fingerprint.
Once the App Connector is enrolled, it is paired with a single customer account, and it cannot be enrolled again. App Connectors that are running in virtual machine (VM) environments should never be cloned, because the keys will no longer match the virtual hardware fingerprints.
Deploying an App Connector on a Supported Platform
Before you begin a deployment, read [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites), which provide detailed information on VM image sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
The deployment process differs depending on the platform used for the App Connector. Zscaler recommends that App Connectors be deployed in pairs, to ensure continuous availability during software upgrades. To learn more, see the [Deployment Guide](/knowledge-base-categories/supported-platforms-connectors) for the platform.