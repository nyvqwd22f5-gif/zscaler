# Adding an ICAP Receiver
Source: https://help.zscaler.com/unified/adding-icap-receiver
PDF: https://help.zscaler.com/pdf/com/en/1494006.pdf

Zscaler's [ICAP Receiver](/unified/about-icap-receivers) feature allows you to forward the inbound and outbound traffic of all the sites of the selected URL categories in the URL Filtering policy rule to an ICAP receiver. It consists of two parts, adding ICAP receivers and associating them to a URL Filtering policy.
To add an ICAP receiver:
- Go to **Policies > Data Protection > Common Resources > ICAP Receiver**.
-
Click **Add ICAP Receiver**.
The **Add ICAP Receiver** window appears.
-
In the **Add ICAP Receiver** window:
- **Name**: Enter a name for the ICAP receiver.
- **Status**: Select **Enabled** to allow the service to send communications to the ICAP receiver. If **Disabled**, the service will not send information to that receiver.
- **Receiver URI**: Enter the ICAP receiver URI.** **The URI must follow the format: `icap://<FQDN or IP address>:<port number>/<servicepath>`.
- By default, the Receiver URI field is prepopulated with `icaps://`** **because Zscaler recommends sending transaction information via secure ICAP. For scenarios where it is preferable to send unencrypted ICAP over plain text (for example, for debugging purposes), you can use `icap://`.
- The `<FQDN or IP address>` of ICAP receivers and load balancers are accepted.
- A `<port number>` must be included and must match the port on which you’ve configured your network firewall to accept ICAP traffic from the service. Zscaler recommends using port number 1344 for ICAP, per standard practice.
- The `<servicepath>` specifies whether the ICAP receiver monitors outgoing traffic or incoming traffic. For example, if you are using Vontu, you would use the servicepath reqmod (for Request Mode) to indicate that the receiver monitors outgoing traffic. An example of a correctly formatted unencrypted ICAP receiver URI for Vontu would be: `icap://metascan.corp.safemarch.com:1344/reqmod`.
[See Image.](#add-ICAP-receiver)
- Click **Save** and activate the change.
[]![Screenshot of the Add ICAP Receiver page.](/downloads/zia/policies/url-filtering/icap-receivers/adding-icap-receiver/ZIA-Add%20ICAP%20Receiver%20page.png)