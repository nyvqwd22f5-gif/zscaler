# Configuring SSL Inspection Policy
Source: https://help.zscaler.com/zia/configuring-ssl-inspection-policy
PDF: https://help.zscaler.com/pdf/com/en/1401851.pdf

You can configure Secure Sockets Layer (SSL) Inspection policies to perform scanning of the SSL traffic based on the source and destination of the traffic. Using these policies, you can simplify the deployment and ongoing operations of SSL Inspection and address the compliance and operational environmental requirements. To learn more, see [About SSL Inspection Policy](/zia/about-ssl-inspection-policy).
Policy Execution
The SSL Inspection rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
Source IP Groups (`AND`) [URL Categories (`OR`) Cloud Applications (`OR`) Destination Groups (`OR`) Forwarding Gateways] (`AND`) ZPA Application Segment (`AND`) [Location Groups (`OR`) Locations] (`AND`) [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Device Groups (`OR`) Devices (`OR`) Remote Users with Kerberos] (`AND`) Device Trust Level (`AND`) CONNECT User-Agent.
To configure an SSL Inspection rule:
- Go to **Policy** > **SSL Inspection**.
- Click **Add SSL Inspection Rule**. The** Add SSL Inspection Rule** window appears.
[See Image.](#add-ssl-inspection-policy)
- Under the **SSL Inspection Rule** section, configure the following rule attributes:
- **Rule Order**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [admin rank](/zia/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a user-friendly name for the rule. The maximum length is 31 characters.
- **Rule Status**: Enable this option to actively enforce the rule. Disabling this option does not actively enforce the rule, and the service skips it and moves to the next rule. However, the rule does not lose its place in the rule order.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
[See image.](#ssl-rule-image)
- Under the **Criteria** section, configure the appropriate rule attributes:
- **Source IP Groups**:** **Select any number of [source IP groups](/zia/about-source-ip-groups). You can also search for source IP groups or click the **Add** icon to add a new [source IP group](/zia/configuring-source-ip-groups). Selecting no value ignores the criterion in the policy evaluation.
- **URL Categories**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select any number of [URL super categories or categories](/zia/about-url-categories). Selecting no value ignores the criterion in the policy evaluation.
- **Cloud Applications**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select any number of [cloud applications or cloud application classes](/zia/about-cloud-app-control). Selecting no value ignores the criterion in the policy evaluation.
-
**Destination Groups**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select any number of [destination groups](/zia/about-destination-groups). Selecting no value ignores the criterion in the policy evaluation. The supported group types are IP, FQDN, and Wildcard FQDN. The countries and custom categories configured in the destination groups are ignored.
During policy evaluation, IP address-based destination groups in the rule criteria are ignored if an SNI value is present in HTTPS requests.
- **Forwarding Gateways**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select any number of [gateways](/zia/about-gateways-proxies) configured for third-party proxies. Selecting no value ignores the criterion in the policy evaluation.
- **ZPA Application Segment**:** **Select up to 255 [ZPA application segments](/zpa/configuring-application-segments). Selecting no value ignores the criterion in the policy evaluation.
The list displays only those Zscaler Private Access (ZPA) application segments that have the **Source IP Anchor** option enabled.
- **Locations**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select up to 32 [locations](/zia/about-locations). Selecting no value ignores the criterion in the policy evaluation.
- **Location Groups**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select up to 32 [location groups](/zia/about-location-groups). Selecting no value ignores the criterion in the policy evaluation.
- **Users**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select up to 32 general and/or special users. Select **General Users** for all authenticated users and **Special Users** for all [unauthenticated users](/zia/configuring-policies-for-unauthenticated-traffic). Selecting no value ignores the criterion in the policy evaluation.
- **Groups**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select up to 32 [groups](/zia/about-groups). Selecting no value ignores the criterion in the policy evaluation.
-
**Departments**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select up to 32 departments. If you've enabled the [unauthenticated users policy](/zia/configuring-policies-for-unauthenticated-traffic), you can select **Special Departments** for unauthenticated traffic. Selecting no value ignores the criterion in the policy evaluation.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- **Devices**: Select the [devices](/zia/about-devices) for which you want to apply the rule. Selecting no value ignores the criterion in the policy evaluation.
- **Device Groups**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the [device group](/zia/about-device-groups) for which you want to apply the rule. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or **No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or to traffic that is not tunneled through Zscaler Client Connector, respectively. Selecting no value ignores the criterion in the policy evaluation. Zscaler provides the [Unauthorized Traffic Bypass for IoT Classifications](/zia/about-ssl-inspection-policy#unauthorized-traffic) predefined rule for the SSL Inspection policy.
The **Cloud Browser Isolation** and **IoT** device groups are available if the Isolation and IoT features, respectively, are enabled for your organization.
- **Remote Users with Kerberos**:** **Select **Yes** to apply this policy to remote users using Kerberos authentication. This criterion applies only to remote user traffic with Kerberos authentication, which is forwarded via PAC files and not via Zscaler Client Connector. Selecting no value ignores the criterion in the policy evaluation.
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
- **CONNECT User-Agent**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select any number of user agents. This criterion applies only to SSL traffic forwarded in explicit proxy mode (PAC or PAC over tunnel) and not to traffic forwarded via a transparent proxy (tunnel) or Z-Tunnel 1.0 due to lack of user agent context. Selecting no value ignores the criterion in the policy evaluation.
[See image.](#criteria-image)
- From the **Action** section, choose the appropriate action (**Inspect**, **Do Not Inspect** or **Block**) for the SSL/TLS traffic that matches the defined criteria:
-
If you choose the **Inspect **action, configure the following settings:
- **Override Default Intermediate CA Certificate**:** **Select **Yes** to override the default intermediate Certificate Authority (CA) certificate.
- **Intermediate CA Certificate**:** **Choose an intermediate CA certificate from the list. This option is only available if you have selected **Yes** in the Override Default Intermediate CA Certificate field.
- **Untrusted Server Certificates**:** **Select how the service handles untrusted certificates (e.g., path validation failure, unknown issuer, certificate expired, common name does not match).
- **Allow**: The service allows access to sites with untrusted certificates. Certificate warnings are only displayed when users access sites with expired certificates.
- **Pass Through**: Certificate warnings are displayed to users, and they can decide to proceed to the site.
- **Block**: The service blocks access to sites with untrusted certificates.
- **Block No Server Name Indication (SNI)**: Enable this option to block any traffic that does not contain the SNI in the Client Hello message during SSL handshake. This option is disabled by default.
- **OCSP Revocation Check**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enable this option to include certificate revocation check in the untrusted server certificate validation. The service uses the Online Certificate Status Protocol (OCSP) to obtain the revocation status of a certificate. If the OCSP check fails, the action is determined by the **Untrusted Server Certificates** setting.
- **Block Undecryptable Traffic**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enable this option to block traffic from servers that use non-standard encryption methods or require mutual TLS authentication.
- **Minimum Client TLS Version**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the minimum TLS version required for your clients to establish a connection. The service blocks the connections for clients that do not meet the specified minimum TLS version requirement.
- **Minimum Server TLS Version**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the minimum TLS version required for your servers to establish a connection. The service blocks the connections for servers that do not meet the specified minimum TLS version requirement.
-
**Enable HTTP/2**: Enable to make HTTP/2 the web protocol used for accessing all applications.
The HTTP/2 feature is only available if it is enabled for your organization and does not work for a location's traffic if Bandwidth Control is enabled on that location. If Bandwidth Control is enabled on that location, the Zscaler service falls back to HTTP/1.1, even if HTTP/2 is enabled in the SSL inspection policy.
[See image.](#action-image)
-
If you choose the **Do Not Inspect **action, you can further choose to either **Evaluate Other Policies** or **Bypass Other Policies**. Choosing **Bypass Other Policies** bypasses web policies (URL Filtering and Cloud App Control) for the TLS traffic. If you choose to evaluate other policies for the traffic, you can configure the following settings:
- **Untrusted Server Certificates**:** **&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select how the service handles untrusted certificates (e.g., path validation failure, unknown issuer, certificate expired, Common Name does not match).
- **Allow**: The service allows access to sites with untrusted certificates. While the service does not reset the TCP connection, the browser displays an Invalid Certificate warning message.
- **Block**: The service blocks access to sites with untrusted certificates by resetting the TCP connection.
- **Block No Server Name Indication (SNI)**: Enable this option to block any traffic that does not contain the SNI in the Client Hello message during SSL handshake. This option is disabled by default.
- []**Show Notifications for Blocked Traffic**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enable this setting to display end user notifications to users if the traffic is blocked by other web policies. Ensure that you install the Zscaler root CA certificate or your enterprise root CA certificate in your clients' truststore, so the service can reply or redirect the user to the notification page. If no certificate is installed, the browser displays an Invalid Certificate warning message. If this setting is disabled, the service resets the connection with a generic failed connection message from the browser.
- **Show Notification for ATP Blocks**: Enable this setting to display Advanced Threat Protection (ATP) notifications to the users if the ATP traffic is blocked. This field is only available if you have enabled **Show Notifications for Blocked Traffic**.
- **Override Default Intermediate CA Certificate**:** **Select **Yes** to override the default intermediate CA certificate. This field is only available if you have enabled **Show Notifications for Blocked Traffic**.
- **Intermediate CA Certificate**:** **Choose an intermediate CA certificate from the list. This option is only available if you have selected **Yes** in the Override Default Intermediate CA Certificate field.
- **OCSP Revocation Check**: Enable this option to include certificate revocation check in the untrusted server certificate validation. The service uses OCSP stapling to obtain the revocation status of a certificate. If the OCSP check fails, the action is determined by the **Untrusted Server Certificates** setting.
- **Minimum TLS Version**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Select the minimum TLS version required for your connections. The service blocks connections that do not meet the specified minimum TLS version requirement.
[See image.](#do-not-inspect-image)
-
If you choose the **Block** action, you can choose to enable or disable end user notifications:
- **Show** **End User Notifications**: &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Enable this setting to display end user notifications. Ensure that you install the Zscaler root CA certificate or your enterprise root CA certificate in your clients' truststore, so the service can reply or redirect the user to the notification page. If no certificate is installed, the browser displays an invalid certificate warning message. If this setting is disabled, the service resets the connection with a generic failed connection message from the browser.
- **Override Default Intermediate CA Certificate**:** **Select **Yes** to override the default intermediate CA certificate. This field is only available if you have enabled **Show End User Notifications**.
- **Intermediate CA Certificate**:** **Choose an intermediate CA certificate from the list. This option is only available if you have selected **Yes** in the Override Default Intermediate CA Certificate field.
[See image.](#block-image)
- **Description**: (Optional) Enter a description for the rule. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![SSL Inspection Rule Configuration](/downloads/zia/policies/ssl-inspection/configuring-ssl-inspection-policy/SSL%20Inspection%201_0.png)
[]![SSL Inspection Rule Section](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-ssl-inspection-policy-draft-doc-55860/SSL%20Inspection%20Rule.png)
[]![Criteria Section](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-ssl-inspection-policy-draft-doc-55860/Criteria.png)
[]![ Action - Inspect Section](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-ssl-inspection-policy-draft-doc-55860/Action.png)
[]![Action - Do Not Inspect Section](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-ssl-inspection-policy-draft-doc-55860/Action1.png)
[]![Action - Block Section](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-ssl-inspection-policy-draft-doc-55860/Action2.png)