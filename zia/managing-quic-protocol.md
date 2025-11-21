# Managing the QUIC Protocol
Source: https://help.zscaler.com/zia/managing-quic-protocol
PDF: https://help.zscaler.com/pdf/com/en/1401086.pdf

Google developed the QUIC protocol to increase the performance of HTTPS and HTTP (TCP 443 and TCP 80) connections. Chrome browsers have had experimental support for it since 2014, and it's also used in Chromium and Android devices.
QUIC connections do not require TCP handshakes. However, SSL inspection requires TCP session information. Because of this, Zscaler cannot examine QUIC sessions when users have SSL inspection enabled. When using QUIC, users might also experience certificate errors.
Zscaler best practice is to block QUIC. When it's blocked, QUIC has a failsafe to fall back to TCP. This enables SSL inspection without negatively impacting user experience.
Blocking QUIC
Choose how to block QUIC based on how you are forwarding your traffic to Zscaler.
GRE or IPSec Tunnel and Zscaler Client Connector (Z-Tunnel 2.0)
If you are sending your outbound internet traffic to Zscaler through a GRE or IPSec tunnel, or Zscaler Client Connector using Zscaler Tunnel (Z-Tunnel) 2.0, you can effectively block QUIC by creating a [Firewall Filtering](/zia/configuring-firewall-filtering-policy) rule. This blocks QUIC UDP flows and forces the browser to default to TCP 80/443.
Normally, the [Default Firewall Filtering Rule](/zia/recommended-firewall-control-policy) (the lowest rank rule) blocks QUIC unless specifically allowed. However, admins often create more general connectivity rules or groups of rules (e.g., User X or Source IP Address Y to Destination Group IP Address Y is allowed) that are overly permissive and do not explicitly exclude the use of QUIC. For this reason, one or more QUIC block rules might be needed to precede admin-defined allow rules.
As configured in the following steps, the Firewall Filtering rule blocks QUIC at the network service level. [Network services](/zia/about-network-services) configured in Zscaler are identified at the first packet using port and protocol, leading to immediate policy action. When packets match the configured rule, the Zscaler service drops all packets that match the rule and sends the client an ICMP error message of Type 3 (Destination Unreachable) and Code 13 (Communication Administratively Prohibited).
[Block QUIC with a Firewall Filtering Rule](#zia)
In addition to UDP destination port 443, QUIC can use UDP destination port 80. To include port 80 in the network service definition of QUIC, you can modify the [predefined network service](/zia/about-network-services#list) or configure a custom network service. To learn more, see [Modifying Predefined Network Services](/zia/modifying-predefined-network-services) and [Configuring Network Services](/zia/configuring-network-services).
Additionally, you can manage QUIC using the DNS Control policy by blocking the HTTPS DNS resource record type. HTTPS records contain information about specific services and protocols hosted on a domain including preferred protocols such as HTTP/3 over QUIC. HTTPS records are increasingly used by web browsers and applications to leverage the use of HTTP/3 with QUIC, which the Zscaler web proxy currently does not support. Zscaler recommends configuring your DNS Control policy to block HTTPS resource records to suppress the use of HTTP/3 over QUIC, as shown in the following example rule.
[Block QUIC with a DNS Control Rule](#block-QUIC-dns-https-record)
To learn more about recommendations for using DNS Control, see [Best Practices for DNS Control Rules](/zia/best-practices-dns-control-rules).
Zscaler Client Connector (Z-Tunnel 1.0)
If you are only sending Zscaler Client Connector traffic that uses Z-Tunnel 1.0 to Zscaler (or leveraging remote users), create a block rule on your device firewall to block UDP 80 and 443. This is typically done by an IT admin and is different for every organization.
TCP 80/443 Only
If you are only sending TCP 80/443 over a tunnel to Zscaler, block QUIC on your branch firewall.
- [Block QUIC with a FortiGate Firewall](#fortigate)
- [Block QUIC with a Palo Alto Networks Firewall](#pan)
If your firewall is not listed, refer to your manufacturer's documentation for details on how to block QUIC.
Alternatives
As an alternate measure, you can also block QUIC in Chrome itself.
[Block QUIC in Google Chrome](#chrome)
- []In the ZIA Admin Portal, go to **Policy** > **Firewall Control**.
-
Click **Add Firewall Filtering Rule**.
The **Add Firewall Filtering Rule** window appears.
- In the **Add Firewall Filtering Rule** window:
-
Set the **Rule Order** to the highest possible rank, according to your organization's desired policies.
Zscaler recommends that you rank rules for [network services](/zia/about-network-services) higher than rules for [network applications](/zia/about-network-applications) to prevent packets from being allowed unnecessarily from traffic that would otherwise be blocked by rules using first-packet identification.
- Ensure the **Rule Status** is **Enabled**.
- Ensure **Any** is selected for **Users**, **Groups**, **Departments**, **Locations**, and **Location Groups**.
- Ensure **Always** is selected for **Time**.
-
Select **Block/ICMP **under **Network Traffic**.
[See image.](#block)
- Click the **Services** tab and select** QUIC** under **Network Services**.
[See image.](#quic)
- Click **Save** and [activate your changes](/zia/saving-and-activating-changes-admin-portal).
[]If you have administrator access to Google Apps, you can create a policy to block Chrome for all users. To learn more, refer to the [Google Chrome Enterprise Help](https://support.google.com/chrome/a/answer/2657289?hl=en). If you do not, you can still disable QUIC on individual machines.
To disable QUIC on individual machines:
- Open Chrome.
- Enter `chrome://flags` in the address bar.
[See image.](#chrome-ad)
- Enter `quic` in the search bar.
[See image.](#chrome-search)
- Click the drop-down menu and select **Disabled**.
[See image.](#chrome-disable)
When **Default** is selected, Chrome attempts to use QUIC.
- When prompted, click **Relaunch Now** to restart Chrome and apply your changes.
[See image.](#chrome-relaunch)
[]If you are using FortiGate firewall, you need to create a new service and then create a top-level policy to block the newly created service.
To create a service:
- In the FortiGate portal, go to **Policy and Objects** > **Services**.
- Click** Create new Service**.
-
Complete the following:
- **Name**: Enter `QUIC`.
- **Protocol Type**: Select **TCP/UDP/SCTP**.
-
**Destination Port**: To configure the destination ports:
- **Destination Port**: Select **UDP**.
- **Low**: Enter `443`.
- **High**: Leave blank.
- Click the **Add** icon to include an additional destination port.
- **Destination Port**: Select **UDP**.
- **Low**: Enter `80`.
- **High**: Leave blank.
Other fields should be left with their default values.
[See image.](#fortigate-service)
- Click **OK** to save your service.
To create a policy:
- In the FortiGate portal, go to **Policy and Objects** > **IPv4 Policy**.
- Click **Create New**.
-
Complete the following:
- **Name**: Enter a name for this policy (e.g., `ServiceDeny`).
- **Incoming Interface**: Select **Internal**.
- **Outgoing Interface**: Select **wan**.
- **Source**: Select **all**.
- **Destination**: Select **all**.
- **Schedule**: Select **always**.
- **Service**: Select the **QUIC** service you created.
- **Action**: Select **DENY**.
- **Log Violation Traffic**: Enable this option.
- **Enable this policy**: Enable this option.
[See image.](#fortigate-policy)
- Click **OK** to save your policy.
[]To block QUIC with Palo Alto Networks firewall, you need to create a new security policy.
To create a security policy:
- In the Palo Alto Networks portal, go to **Policies** > **Security**.
- Click **Add**.
- On the **General** tab, enter a **Name** for the rule.
[See image.](#pan-general)
- On the **Source **tab, select the **Source Zone** for your rule.
[See image.](#pan-source)
- On the **User** tab, select **any** as the value for users.
[See image.](#pan-user)
- On the **Destination** tab, select either **Untrust** or your internet facing as the **Destination Zone**.
[See image.](#pan-destination)
- On the **Application** tab:
- Select **Add.**
- Enter `quic` in the search bar.
- Select the **quic** application.
[See image.](#pan-application)
- On the** Service/URL Category** tab, leave all fields with their default values.
[See image.](#pan-service)
- On the **Actions** tab, select **Drop** as the action and configure other fields as desired.
[See image.](#pan-action)
- Click **OK** to save the policy.
[See image.](#pan-ok)
- []In the ZIA Admin Portal, go to **Policy** > **DNS Control**.
-
Click **Add DNS Filtering Rule**.
The **Add DNS Filtering Rule** window appears.
-
In the **Add DNS Filtering Rule** window:
- Set the **Rule Order** to the highest possible order (using a higher [admin rank](/zia/about-admin-rank)), according to your organization's desired policies.
- Ensure the **Rule Status** is **Enabled**.
-
On the **DNS Application** tab, select **HTTPS** for the **DNS Request Type** condition.
The other rule criteria can remain non-specific with values selected as **Any**, **Always**, or **None**, or left blank, whichever is contextually applicable.
-
Under **Action**:
- **Network Traffic**: Select **Block with Response Code**.
- **Response Code**: Select **2 - Server Failure**.
[See image.](#dns-block-https-QUIC)
This rule configuration blocks HTTPS resource records and sends a Server Failure response (i.e., ServFail DNS response code per [RFC 6895](https://datatracker.ietf.org/doc/html/rfc6895)) to the client.
- Click **Save** and [activate your changes](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of Firewall Filtering Rule blocking QUIC](/downloads/zia/troubleshooting/managing-quic-protocol/zia-fw-rule-block-quic.png)
[]![Screenshot of Firewall Filtering Rule blocking QUIC](/downloads/zia/troubleshooting/managing-quic-protocol/zia-fw-rule-block-quic-network-service.png)
[]![Screenshot of chrome://flags in the address bar](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/chrome-address-bar.png)
[]![Screenshot show quic being searched for](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/google-quic-search.png)
[]![Screenshot showing the options for the QUIC protocol](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/chrome-quic-disabled.png)
[]![Screenshot showing prompt after you have made changes](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/chrome-relaunch.png)
[]![Screenshot of the desired setting for QUIC service](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/fortigate-service.png)
[]![Screenshot of the desired settings for the Fortigate rule](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/fortigate-rule.png)
[]![Screenshot of the General tab](/downloads/zia/troubleshooting/managing-quic-protocol/pan-general.png)
[]![Screenshot of the Source tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-source.png)
[]![Screenshot of the User tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-user.png)
[]![Screenshot of the Destination tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-destination.png)
[]![Screenshot of the Application tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-application.png)
[]![Screenshot of the Service/URL Category tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-service.png)
[]![Screenshot of the Actions tab](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-action.png)
[]![Screenshot with the OK button highlighted](/downloads/zia/documentation-knowledgebase/troubleshooting/managing-quic-protocol/pan-ok.png)
[]![DNS filtering rule blocking HTTPS resource records to suppress HTTP/3 over QUIC](/downloads/zia/troubleshooting/managing-quic-protocol/DNS-rule-block-https-record.png)