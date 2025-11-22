# Web Probe Errors
Source: https://help.zscaler.com/unified/web-probe-errors
PDF: https://help.zscaler.com/pdf/com/en/1495051.pdf

At times, you might see error icons in the Web Probe Metrics section of the Users Dashboard. When you click the icon, you see related metrics information.
[See image.](#ZDX_WebProbeErrors)
The icons in the graph indicate the following:
- ![Caution Icon](/downloads/zdx/analytics/web-probe-errors/Caution-icon-error.png)
: This is a warning message. This indicates that action may be necessary to resolve an issue and achieve accurate results.
- ![Critical Error in ZDX ](/downloads/zdx/analytics/web-probe-error-messages/ZDX_CriticalIcon.png)
: This is a critical error. This indicates an issue that could affect the user experience.
- ![Image of icon for rate limiting](/downloads/zscaler-tech-pubs-style-guide/draft-articles/web-probe-errors-draft/zdx-rate-limiting-icon4.png)
: This indicates a Zscaler Private Access (ZPA) web probe is rate limited.
[][![Web Probe Errors in ZDX ](/downloads/zdx/analytics/web-probe-error-messages/ZDX_WebProbeErrors.png)
](https://ZDX_WebProbeErrors)
The following table provides a list of possible error messages and a description of the error.
[][][][][][][][][][][][][][][](/unified/configuring-probe)[][][][][][][]
-
-
-
-
[]
-
-
-
-
[][]
| Error Message | Error Description | Recommended Action |  |
| ------------- | ----------------- | ------------------ | --- |
| The domain is invalid or not resolvable. Verify your domain. | After redirection, DNS resolution failed. This could be an issue with the application or its domain. | Verify the domain configured in the application is still valid or that it exists. Also check the application redirection. |  |
| TCP connection was reset | The TCP connection was reset. This could be due to a firewall or security policies, lack of server resources, server error, or congestion. | Verify that the security policies allow traffic to this application, or that the server is listening on the config port, or that server resources are adequate. |  |
| TCP connection timed out | The TCP connection timed out while waiting for a response from the application. | Check that the application configured for the web probe is correct. Also check for any network devices that might be dropping SYN packets silently. |  |
| TCP connection aborted | The TCP connection was aborted, as a TCP connection reset message was received after the connection was established. | High numbers of aborted connections can point to network or server problems. |  |
| TCP connection refused | The TCP connection was refused. This means that no port is listening or that a firewall is blocking the port. | Check the configuration to verify that the right port was used and your server is listening on that port. Also verify that your security policies allow traffic to this port. |  |
| TCP connection error | There was a generic TCP connection error | Contact Zscaler Support. |  |
| The web probe HTTP method is not supported by the application | Zscaler does not currently support this HTTP request method. Only the GET method can currently be configured from the UI. | Check the web probe configuration. Consider adding a 40X/50X code to build a valid success code in the web probe configuration. |  |
| TCP connection was reset during HTTP CONNECT request | The Internet & SaaS Public Service Edge timed out the HTTP connection as no response was received from the destination server. | Check that you are authenticated to use the Zscaler service and there is a valid policy. |  |
| TCP connection timed out during HTTP CONNECT request | The Internet & SaaS Public Service Edge timed out the HTTP connection as no response was received from the destination server. | Check that the URL in the web probe configuration is correct. |  |
| TCP connection aborted during HTTP CONNECT request | The Internet & SaaS Public Service Edge aborted the HTTP connection after receiving a TCP reset from the destination server. | Check the configuration to verify that the URL is correct. |  |
| TCP connection refused during HTTP CONNECT request | The Internet & SaaS Public Service Edge refused the HTTP connection after receiving a TCP reset from the destination server. | Check the configuration to verify that the right port was used and the destination server is listening on that port. Also check the security policy. |  |
| Invalid HTTP response received during HTTP CONNECT request | The Internet & SaaS Public Service Edge HTTP response code had an error. | Contact Zscaler Support. |  |
| HTTP CONNECT request failed | There was a generic exception in sending the connection to the Internet & SaaS Public Service Edge. | Verify that the Internet & SaaS Public Service Edge is not blocked by the firewall. |  |
| HTTP response code xxx not a success code | The HTTP response code was a mismatch and is not in the configured list of successful HTTP codes. | The web probe is configured to consider successful HTTP connections in the range (100-199), (200-299), and (300-399). The response code received was not in this range. Consider reconfiguring the HTTP success code to include (400-499) client errors. If (500-599) server errors are also transiently received, you may consider adding them as an HTTP success code. To learn more, see Configuring a Probe. |  |
| TCP connection was reset during HTTP request to application. | The TCP connection was reset by the application server while the HTTP request was in progress. | The application server closed the TCP connection. This is probably due to a high load on the application. |  |
| TCP connection timed out during HTTP request to application | The TCP connection timed out while sending the HTTP request to the application server. | A response was not received from the server in the configured timeout (60 seconds by default). |  |
| TCP connection aborted during HTTP request to application | The TCP connection was aborted by the application server during the HTTP request. | The application server sent a TCP connection reset. This is probably due to a high load on the application. |  |
| TCP connection refused during HTTP request to application | The TCP connection was refused by the server during the HTTP request. | Verify that the configured port is open on the server. Also check if there is a firewall in the path that is blocking the connection. |  |
| TCP connection error during HTTP request to application | A generic application server error was received. | The TCP connection with the application could not be established. This is probably due to a high load on the application. |  |
| HTTPS connection failed due to invalid certificate | The certificate received from the application server is invalid. | Verify the validity of the certificate and that the certificate has not expired. |  |
| HTTPS connection failed due to SSL context exception | An SSL context exception error occurred. | The application server SSL handshake has a generic exception. Possible causes could be:Improperly formatted SSL certificateImproperly installed certificateWrong cipherProblem in the certificate’s chain of trust |  |
| HTTPS connection failed due to SSL error | A generic SSL exception occurred. This could be due to multiple possible causes. | The application server SSL handshake has a generic exception. Possible causes could be:Improperly formatted SSL certificateImproperly installed certificateWrong cipherProblem in the certificate’s chain of trust |  |
| Web probe request timed out | The probe timed out as there was no response. The web probe HTTP request exceeded the configured timeout value (60, by default) in the probe configuration. | Verify that the URL is correctly configured or change the default timeout value. |  |
| Web probe is rate limited | The probe failed due to Private Applications rate limiting to control the probe threshold. | When configuring web probes for internal applications through ZPA, configure probes only for users, user groups, and departments that use the application. |  |