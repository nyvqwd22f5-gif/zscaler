# Understanding the Post-Quantum Cryptography Visibility Report
Source: https://help.zscaler.com/zia/understanding-post-quantum-cryptography-visibility-report
PDF: https://help.zscaler.com/pdf/com/en/1532146.pdf

Quantum computers pose a significant future threat to current cryptographic systems used in TLS, SSH, and IPSec, enabling adversaries to store encrypted data today and decrypt it later. This is driving a global push for Post-Quantum Cryptography (PQC). PQC is a new class of cryptographic algorithms designed to protect data and communications against potential attacks from advanced, large-scale quantum computers. Organizations require visibility into traffic flows to determine PQC compliance and readiness.
To mitigate threats from quantum computing, the National Institute of Standards and Technology (NIST) has approved and standardized the following key PQC algorithms:
- Module Lattice-Based Key Encapsulation Mechanism (ML-KEM) for key exchange
- Module Lattice-Based Digital Signature Algorithm (ML-DSA)/Stateless Hash-based Digital Signature Standard (SLH-DSA) for digital signatures
A TLS handshake involves both key exchange for symmetric encryption to establish a shared secret and authentication for identity verification between the client and server. The cryptographic algorithms used in TLS handshakes are no longer considered secure in the post-quantum era. PQC addresses this by offering new key exchange and certificate signature algorithms designed to resist quantum attacks. This information is crucial for IT departments to make informed decisions regarding software and hardware upgrades and to prepare for future PQC mandates, thereby ensuring business continuity and maintaining a competitive edge.
TLS version 1.3 can be extended to offer support for various key exchange methods, including Elliptic Curve Cryptography (ECC), PQC, and Hybrid PQC.
PQC key exchange is already supported in major browsers such as Chromium-based, Firefox, and Safari, and services.
Key Features of PQC Logging in Zscaler
As organizations prepare for the transition to PQC, it is critical to have logging and visibility into PQC-related security events. PQC logging Zscaler Internet Access (ZIA) ensures security teams can monitor and analyze PQC-related traffic and threats. The following are the key features of PQC logging:
- **Comprehensive Logging**: Logs the TLS server's chosen cryptographic parameters (key exchange and signature algorithms) and client proposals (supported groups and signature algorithms) for both SSL-intercepted and bypassed traffic as the following:
- Client Digital Signature Proposal
- Client Key Exchange Proposal
- Client-Side Key Exchange Algorithm
- Server-Side Key Exchange Algorithm
- Client-Side Digital Signature Algorithm
- Server-Side Digital Signature Algorithm
- **Algorithm Classification**: Client key exchange and signature algorithm offers are classified as PQC, Non-PQC, Hybrid (PQC combined with classical algorithms like ECC), or Unknown to both Zscaler-inspected and bypass traffic to provide visibility into your organization's PQC readiness.
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters), [Web Insights Logs: Columns](/zia/web-insights-logs-columns), and [Web Data Types and Filters](/zia/web-data-types-and-filters).
Key Benefits
The Post-Quantum Cryptography Visibility Report provides the following benefits and enables customers to:
- Capture logs and generate reports for all sessions that are negotiated using PQC, Classical, and Hybrid algorithms, and facilitates real-time and historical search capabilities through the ZIA Admin Portal.
- Gain clear visibility into the cryptographic algorithms used within their TLS traffic, specifically highlighting PQC usage with visibility into their networks' PQC readiness.
- Analyze PQC adoption trends within enterprises by offering insights into traffic patterns, comparing PQC and classical encryption methods.
To learn more about how to view and analyze the Post-Quantum Visibility Report, see [Viewing the Post-Quantum Cryptography Visibility Report](/zia/viewing-post-quantum-cryptography-visibility-report).