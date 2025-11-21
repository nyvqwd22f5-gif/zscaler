# SSL Inspection Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/ssl-inspection-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417371.pdf

This guide describes the benefits of using SSL inspection and the steps necessary for configuring Zscaler Internet Access (ZIA) to add SSL inspection to your security posture.
Much of the data traveling via the internet is confidential and sensitive. To protect this data in transport across the internet, browsers and cloud apps use encryption.
SSL encryption protects this data from unauthorized access while in transit between locations over the internet. However, malicious traffic can also hide in SSL encryption. SSL inspection decrypts SSL-encrypted data in transit and checks it for malicious traffic.
Zscaler ThreatLabZ observed a more than 400 percent increase in phishing attacks delivered over the SSL channel in 2018 compared to 2017. Decrypting SSL traffic is an important aspect of an organization's security, and most companies should inspect as much of their SSL traffic as possible.
To learn more, see [About SSL Inspection](/zia/about-ssl-inspection).
Value of Deploying SSL Inspection
Using SSL Inspection provides the following benefits:
- Visibility into traffic that isn’t scannable by dedicated engines.
- Prevents data breaches by finding hidden malware and stopping hackers from sneaking past defenses.
- Identifies what data employees are sending outside the organization, intentionally or accidentally, and responds accordingly.
- Meets regulatory compliance requirements by ensuring employees aren’t putting confidential data at risk.
- Supports a multilayered defense strategy that keeps the entire organization secure.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, configure ZIA SSL Inspection to meet the needs of your infrastructure. The following sections discuss steps to deploy ZIA SSL Inspection.
Deployment Steps
The following steps explain how to deploy ZIA SSL Inspection:
- [Decide which certificate to use](/zia/choosing-ca-certificate-ssl-inspection). If you use the default Zscaler intermediate certificate, ensure all clients have installed the Zscaler root certificate. Failure to install the Zscaler root certificate results in warnings from browsers and applications or the inability to inspect the traffic properly.
- If using Firefox, make sure to update its root certificate store.
- Follow the [SSL deployment best practices](/zia/deploying-ssl-inspection) and start small. Begin SSL Inspection in a test lab or a small office for a subset of users and applications.
- When enlarging the user base, issue the proper communications as dictated by the local laws concerning privacy. You can never inspect some traffic due to regulations (e.g., personal medical data and financial services). However, depending on the industry and the risks, you might decide to apply inspection to commonly skipped categories.
- Remember that mobile applications often use [certificate pinning](/zia/deploying-ssl-inspection), which prevents SSL Inspection from working correctly. Instead of inspecting data in transit, you might consider leveraging SaaS Security functionality to inspect data at rest.
- [Be aware of the different scenarios](/zia/deployment-scenarios-ssl-inspection) related to the different types of traffic forwarding. Are you going to apply SSL Inspection to known locations, remote users, or both?
- Remote users might leverage different types of traffic forwarding, although the Zscaler Client Connector is recommended.
- [Test a small list of websites and applications](/zia/best-practices-testing-and-rolling-out-ssl-inspection), and then proceed with the entire URL categories you want to inspect.
Considerations
Review the following considerations:
- Make sure you’re not breaching any laws or contractual agreements concerning users' privacy.
- Consider leveraging SaaS Security-type control for data-at-rest instead of (or combined with) SSL Inspection.
- Prepare a list of critical business applications and add them to your [SSL bypass list](/zia/configuring-ssl-inspection-policy) before deploying SSL Inspection.
- Consider building a Non_SSL_inspection location for the server sub-location.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA SSL Inspection during the operations phase to meet your infrastructure needs.
Prerequisites
For SSL Inspection operation, complete the following prerequisites:
- Make sure all clients have the proper root certificates in the correct stores and remember that web applications and their desktop counterparts might behave differently (the latter are more prone to certificate pinning). The same is valid for mobile apps.
- Depending on the type of deployment of ZIA services, you might have to configure SSL Inspection for Zscaler Client Connector.
- Test corner cases as much as possible, including:
- Untrusted server certificates.
- Undecryptable traffic.
- Make sure your business-critical applications are not reliant on the cases mentioned earlier.
Common Troubleshooting Items
The following list describes common issues related to deploying SSL Inspection:
- Non-browser applications are getting SSL errors: Check if the Zscaler Root certificate is installed in the proper repository for these applications.
- The app or website behaves differently in Android than iOS and desktop OS: Each OS can behave differently, especially when dealing with SSL certificates. Inside each OS, different browsers can exhibit different behaviors. Ensure as much consistency as possible among different platforms: If necessary, disable SSL Inspection for a particular site and move to SaaS Security-type protection.
- The app is not working properly. Check if the app uses certificate pinning: [Many well-known applications use pinning](/zia/certificate-pinning-and-ssl-inspection). If certificate pinning is in place, exempt the applications from [SSL Inspection](/zia/about-ssl-inspection) by removing the cloud application from SSL Inspection or the individual domains from SSL Inspection, using the [custom URL categories](/zia/adding-custom-url-categories).
- Unable to configure SSL Inspection on the ZIA Admin Portal: Make sure you have the proper license for SSL inspection and that your [admin account has the correct permissions and access](/zia/configuring-role-based-administration).
- A legitimate site is blocked: Make sure you don't configure policies that are too restrictive regarding the [minimum Transport Layer Security (TLS) version](/zia/configuring-ssl-inspection-policy).
- My legal department is concerned about Zscaler handling its data: Web transaction content inspection takes place in memory and is never written to disk. Refer to your Zscaler Account team for further details.
- I’m not willing to upload my own intermediate certificate to Zscaler nodes: Zscaler supports private keys in cloud hardware security modules (HSM).
Deployment and Operations Checklist
Zscaler recommends downloading the [SSL Inspection Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/ssl-inspection-deployment-and-operations-guide/SSL-Inspection-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA SSL Inspection: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/ssl-inspection-deployment-and-operations-guide/SSL-Inspection-Deployment-Operations-Checklist.pdf)
Additional Information
For more SSL Inspection information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).