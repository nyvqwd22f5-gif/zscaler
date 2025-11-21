# Configuring the ICAP Server with the Mutual Transport Layer Security (MTLS) CA Certificate
Source: https://help.zscaler.com/unified/configuring-icap-server-mutual-transport-layer-security-mtls-ca-certificate
PDF: https://help.zscaler.com/pdf/com/en/1493406.pdf

ICAP servers can be configured for mutual client authentication using the MTLS Certificate Authority (CA) Certificate that you can download from the Admin Portal.
To configure the ICAP server with the MTLS Certificate:
- In the Admin Portal, go to **Policies** > **Data Protection** > **Common Resources** > **DLP Incident Receiver**.
- Click the **Download MTLS CA Certificate** icon to download the root CA certificate.
- If client certification verification is required for additional security of ICAPS traffic, then configure your ICAPS server or SSL tunnel in front of the ICAP server to use the root CA certificate that you downloaded to verify the Zscaler client certificate when the ICAPS connection is initiated from the Zscaler cloud.
This root CA certificate is not a server certificate used for the SSL server.
The client certification verification is optional and is part of the SSL server configuration on your side. If the SSL server does not request the verification, then the Zscaler SSL client will not send it.
A client certificate is sent from Zscaler during the SSL handshake, and it is anchored on the root CA certificate downloaded from the Admin Portal. This client certificate is signed with an intermediate CA certificate which is signed with the downloaded root CA certificate. This intermediate CA certificate is also sent with the client certificate during the SSL handshake and verified through the SSL CA chain.
The SSL server must also use the root CA certificate to send the acceptable CA names to the Zscaler SSL ICAP client so that the client can send back the proper client certification.
It is also recommended that you create a minimal set of root CA certificates for the ICAP SSL server so that the SSL connection is only established if the client is verified with the expected set of root CA certificates.