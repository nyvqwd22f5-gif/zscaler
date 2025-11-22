# About SSL Inspection
Source: https://help.zscaler.com/unified/about-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1493731.pdf

[]HTTPS is an aggregate of HTTP and the Secure Sockets Layer (SSL)/Transport Layer Security (TLS) protocol, wherein the authentication and encryption capabilities of SSL/TLS protect HTTP communications. This is vital because the information that you send on the internet is passed along from one device to another before it reaches the destination server. Therefore sensitive information, such as credit card numbers, usernames, and passwords, may be seen by intermediate devices if the information is sent in clear text over HTTP. When the information is encrypted and protected by the SSL protocol, only the intended recipient can read the information. For more general information about SSL, see [About Secure Sockets Layer (SSL)](/unified/about-secure-sockets-layer-ssl).
Unfortunately, the security provided by SSL is also being misused in a number of ways:
- SSL encryption is used to hide dangerous content such as viruses, spyware, and other malware.
- Attackers build their own websites with SSL encryption.
- Attackers inject their malicious content into well-known and trusted SSL-enabled sites.
- SSL can be used to hide data leakage; for example, the transmission of sensitive financial documents from an organization.
- SSL can be used to hide the browsing of websites that belong to legal-liability classes.
As more and more websites use HTTPS, including social media such as Facebook and Twitter, the ability to control and inspect traffic to and from these sites has become an important piece of the security posture of an organization.
The Zscaler service can inspect HTTPS traffic from your organization. The service can scan data transactions and apply policies to it. It functions as a full SSL proxy, or SSL man-in-the-middle (MITM) proxy.
Protecting SSL Traffic
When you enable SSL inspection, the Zscaler service establishes a separate SSL tunnel with the user’s browser and with the destination server. The diagram below shows the Zscaler SSL inspection process:
- A user opens a browser and sends an HTTPS request.
- The Zscaler service intercepts the HTTPS request. Through a separate SSL tunnel, the service sends its own HTTPS request to the destination server and conducts SSL negotiations.
- The destination server sends the Zscaler service its certificate with its public key.
- The Zscaler service and destination server complete the SSL handshake. The application data and subsequent messages are sent through the SSL tunnel.
- The Zscaler service conducts SSL negotiations with the user’s browser. It sends the browser the Zscaler intermediate certificate or your organization’s custom intermediate root as well as a server certificate signed by the Zscaler intermediate CA. The browser validates the certificate chain in the browser's certificate store.
Zscaler issued certificates (leaf or short-lived issuing CA) contain a CRL Distribution Point (CRLDP) hosted by Zscaler that provides a mechanism for certification revocation.
- The Zscaler service and the browser complete the SSL handshake. The application data and subsequent messages are sent through the SSL tunnel.
![Diagram of the Zscaler SSL inspection process](/downloads/zia/policies/ssl-inspection/about-ssl-inspection/ZIA-SSL-Inspection-Diagram.png?1618598493)