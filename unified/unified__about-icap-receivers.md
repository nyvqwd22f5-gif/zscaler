# About ICAP Receivers
Source: https://help.zscaler.com/unified/about-icap-receivers
PDF: https://help.zscaler.com/pdf/com/en/1494001.pdf

Zscaler's ICAP Receiver feature allows you to forward the inbound and outbound traffic of all the sites of the selected URL categories in the URL Filtering policy rule to an ICAP server. It consists of two parts, adding ICAP receivers and associating them to a URL Filtering policy. You can configure secure or unencrypted Internet Content Adaptation Protocol (ICAP) servers. However, Zscaler recommends sending transaction information via secure ICAP.
This article is about ICAP receivers for the URL Filtering policy only. If you want to use the ICAP receiver for DLP, see [About ICAP Receivers for DLP](/unified/about-icap-receivers-dlp).
About the ICAP Receivers Page
On the ICAP Receivers page (Policies > Data Protection > Common Resources > ICAP Receivers), you can do the following:
- [Add an ICAP receiver](/unified/adding-icap-receiver).
-
Download the Mutual Transport Layer Security (MTLS) Certificate Authority (CA) Certificate that will be used when the ICAP server requests client authentication.
The use of this certificate is optional and is only required if the ICAP server is using mutual authentication. After you download the certificate, install the certificate in your ICAP server's tunnel configuration. To learn more, see [Configuring the ICAP Server with the Mutual Transport Layer Security (MTLS) CA Certificate](/unified/configuring-icap-server-mutual-transport-layer-security-mtls-ca-certificate).
- View a list of all ICAP receivers that were configured for your organization. For each ICAP receiver, you can see the following:
- **Name**: The name of the ICAP receiver. You can sort this column.
- **Status**: Displays whether the ICAP receiver is enabled or disabled.
- **URI**: The ICAP receiver URI. You can sort this column.
- Edit an ICAP server configuration.
- [Modify the table and its columns](/unified/using-tables).
- Search for an ICAP receiver.
![Screenshot of ICAP Receivers page and its features](/downloads/zia/policies/url-filtering/icap-receivers/about-icap-receivers/ZIA-ICAP-Receivers-Page.png)