# Understanding Secure Sockets Layer (SSL)
Source: https://help.zscaler.com/zia/understanding-secure-sockets-layer-ssl
PDF: https://help.zscaler.com/pdf/com/en/1399176.pdf

Secure Sockets Layer (SSL) is a client-server protocol that creates a secure channel over the internet. SSL is used to validate the identity of the destination server and (optionally) the client and to encrypt information sent across the internet between the client and server.
When a client, such as a browser, first sends an HTTPS request to a web server, it starts a series of message exchanges called the SSL handshake. During the SSL handshake:
- The server sends its digital certificate to the client to authenticate itself.
- The client and server agree on the SSL protocol version and algorithms to use.
- The client and server generate the symmetric keys they will use to encrypt their messages.
The following is an illustration of the SSL handshake.
[See image.](#ssl-handshake)
After the SSL handshake is successfully completed, the browser and web server continue with the standard HTTP communications in a secure manner.
- The client sends its HTTPS request in the Client Hello. The entire HTTPS message is encrypted, including the headers and the request/response load. The actual hostname and domain name being accessed is not visible. How the Zscaler service determines the destination host name depends on whether it is operating in transparent mode or explicit mode.
- The server responds with its Hello message and its certificate. (A certificate is an electronic form that verifies the identity and public key of the subject of the certificate.) SSL uses the Public Key Infrastructure (PKI) to ensure the trustworthiness of the certificates.
- The client and server continue with the SSL negotiation.
- After the SSL tunnel is established, the application data is sent securely through the tunnel.
The following packet capture shows the SSL packets as they are exchanged between the browser, which is the client, and the web server.
[See image.](#packet-capture)
[]![Image of SSL handshake](/downloads/zpa/ssl_handshake_image.png)
[]![The SSL packet capture showing the SSL packets exchanged between the client and web server](/downloads/zpa/ssl_packet_capture_image.png)
Public Key Infrastructure (PKI)
SSL uses Public Key Infrastructure (PKI) to ensure the trustworthiness of the certificates. PKI uses a trusted third party, called a certificate authority (CA) to guarantee the identity of an entity. When a CA verifies an entity’s identity, it uses an algorithm, such as RSA, to generate a public and private key. It gives the private key to the requesting entity, and the public key is made available to the public. To authenticate itself to another party, the entity uses its private key to encrypt its certificate and the other party uses the corresponding public key to decrypt it.
A CA issues certificates in a tree structure, with the root certificate as the top-most certificate. The CA signs the root certificate, which is considered trustworthy in many software applications, such as web browsers. Web browsers have the root certificates of many CAs.
A root certificate can sign and designate a certificate as an intermediate CA certificate, which can sign and designate other certificates as intermediate certificates as well. A certificate chain refers to the list of certificates that complete the chain of trust, from the trusted root CA certificate to any intermediate certificates and the certificate of an entity. The following image is an example of a certificate chain:
[See image.](#PKI-1)
The certificate of mail.google.com was signed by Google Internet Authority G2.
[See image.](#PKI-2)
The certificate of Google Internet Authority G2 was signed by GeoTrust Global CA.
[See image.](#PKI-3)
The certificate of GeoTrust Global was signed by Equifax Secure Certificate Authority.
[See image.](#PKI-4)
The certificate of GeoTrust Global CA and Equifax Secure Certificate Authority are in the certificate store of the browser.
[See image.](#PKI-5)
Public Key Pinning (PKP)
Public Key Pinning (PKP), also known as certificate pinning, is the process of associating a host with its expected public key. This is typically seen only if a web service (or Web Application) provider owns both the server-side code and the client-side code. To learn more, see [Public Key Pinning (PKP) and Zscaler](/zia/public-key-pinning-and-zscaler).
[]Perfect Forward Secrecy (PFS)
Perfect Forward Secrecy (PFS) is a feature of secure communication protocols that prevents compromised session keys.
In the commonly used RSA key exchange, SSL sessions between the client and web server are encrypted with the public key and decrypted with the private key. If attackers access the server's private key, they can uncover the session keys and decrypt all your conversations from past and future sessions.
In contrast, PFS uses either the standard Diffie-Hellman ephemeral key exchange (DHE) or the Elliptic Curve Diffie-Hellman ephemeral key exchange (ECDHE). DHE uses public-key cryptography, which generates keys with modular arithmetic. In DHE, there isn't a link between the server's private key and session key, so the confidentiality of session keys aren't dependent on the private keys. If attackers access the server's private key, they are unable to uncover the session key and decrypt the conversation. Furthermore, the server generates different session keys for each conversation with the client. If attackers compromise the session key, they are only able to decrypt the conversation for that particular session. To decrypt all conversations, they must compromise the session keys for every session.
ECDHE is like DHE but uses elliptic-curve cryptography. Elliptic-curve cryptography generates keys using algebraic curves. It is significantly faster than DHE and provides better performance. Elliptic-curve cryptography achieves equivalent security as RSA with smaller keys.
For a list of the supported DHE and ECDHE cipher suites, see [Zscaler SSL Support](/zia/supported-cipher-suites-ssl-inspection).
To learn more about how the Zscaler service can protect your organization from the potential misuse of SSL by attackers for malicious activity, see [About SSL Inspection](/zia/about-ssl-inspection#how-zscaler-protects-ssl-traffic).
[]![The certificate chain of mail.google.com Windows](/downloads/zpa/certificate_chain_screenshot.png)
[]![The certificate is signed by Google Authority G2](/downloads/zpa/certificate_signed_by_google_internet_authority_g2_screenshot.png)
[]![The certificate is signed by GeoTrust Global CA](/downloads/zpa/certificate_signed_by_geotrust_global_ca_screenshot.png)
[]![The certificate is signed by Equifax Secure Certificate Authority](/downloads/zpa/certificate_signed_by_equifax_secure_certificate_authority.png)
[]![A list of trusted root certification authorities in Windows](/downloads/zpa/browser_certificate_store_screenshot.png)