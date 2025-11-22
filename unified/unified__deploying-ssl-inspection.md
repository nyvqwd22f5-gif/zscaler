# Deploying SSL Inspection
Source: https://help.zscaler.com/unified/deploying-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1493786.pdf

To deploy SSL inspection:
- [1. Review Best Practices for SSL Inspection](#A)
- [2. Choose the CA and Configure the Appropriate Root Certificate](/unified/choosing-ca-certificate-ssl-inspection)
- [3. Install the Certificate to an Application-Specific Trusted Store](/unified/adding-custom-certificate-application-specific-trust-store)
- [4. Configure the SSL Inspection Policy](/unified/configuring-ssl-inspection-policy)
[]Before deploying SSL inspection for your organization, consider the following best practices:
- Enable SSL inspection on a small location or test lab before enabling it on all locations in your organization to understand how this feature works.
- If you are using the Zscaler intermediate certificate, ensure that the Zscaler root certificate is distributed to all users and that it is installed in their browsers before enabling SSL in a location.
- You might also update your end user [notification](/unified/configuring-end-user-notifications) to inform users of your organization's SSL Inspection policy.
- When you define SSL Inspection policy, you can create a list of URLs/[URL categories](/unified/about-url-categories) and cloud apps/[cloud app categories](/unified/understanding-cloud-app-categories) for which SSL transactions are not to be decrypted.
- Start by enabling SSL inspection for risky URL categories only, such as Privacy Risk and Legal Liability categories such as Adult Themes and Gambling. Include all other categories in the list of URL categories for which SSL transactions are not to be decrypted. Then, when your organization is ready, enable SSL inspection for all URL categories except Finance and Health, to allay privacy concerns within the organization.
- The list of URL categories and cloud apps for which SSL transactions will not be decrypted does not apply to road warriors who configure their browsers or[ PAC files ](/unified/understanding-pac-files)to send traffic to port 9443. To use this feature, your organization must subscribe to a dedicated proxy port.
- Ensure to update the global bypass list to bypass TLS sessions using Client Certificate Authentication. Zscaler does not support the decryption of mutually authenticated TLS sessions.
Mutual TLS authentication, or two-way TLS, is a digital security protocol where both the client and the server verify each other's identities before initiating communication. This protocol enhances security by ensuring that the data is shared only between authenticated and trusted entities. This reduces the risk of impersonation or man-in-the-middle attacks.
In this authentication process, the client and server exchange digital certificates, essentially digital IDs issued by trusted authorities known as Certificate Authorities (CAs). The certificates contain public keys and other identifying information that helps verify the identity of the entities involved in the communication.
In general, client certificate authentication is part of the mutual TLS authentication process. It is a step where the server asks the client to present its digital certificate for validation. The server allows the client to access its resources when the certificate is valid and trusted. It provides an additional layer of security compared to standard TLS, where only the server is authenticated.
- Firefox browsers do not accept SSL certificates installed in Internet Explorer browsers. You must [install SSL certificates on Firefox browsers](/unified/adding-custom-certificate-application-specific-trust-store#firefox) separately if your organization allows Firefox browsers. Google Chrome, however, uses the same certificate store as Internet Explorer.
- Certain client applications, like Dropbox, use a technique called [certificate pinning](/unified/certificate-pinning-and-ssl-inspection), where the client application is hard coded to accept only one specific client certificate. Apps that use certificate pinning might not work with SSL inspection. They should be included in the list of URL categories for which SSL transactions will not be decrypted.
- Enable user authentication as well, to allow the service to apply user policies.
- To see how SSL inspection impacts what policies are enforced by the service, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).