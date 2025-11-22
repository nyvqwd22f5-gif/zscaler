# About ICAP Receivers for DLP
Source: https://help.zscaler.com/unified/about-icap-receivers-dlp
PDF: https://help.zscaler.com/pdf/com/en/1493381.pdf

You can forward information about transactions that violate the DLP policy to the Internet Content Adaptation Protocol (ICAP) receivers you’ve defined in the Admin Portal.
You can configure secure or unencrypted ICAP receivers on the DLP Incident Receiver page. Zscaler recommends sending transaction information via secure ICAP.
If you want to use ICAP receivers for web traffic filtering, see [About ICAP Receivers](/unified/about-icap-receivers).
About the ICAP Settings Page
On the ICAP Settings page (Policies > Data Protection > Common Resources > DLP Incident Receiver), you can do the following:
- [Add an ICAP receiver](/unified/adding-icap-receiver-dlp).
- Download the Mutual Transport Layer Security (MTLS) Certificate Authority (CA) Certificate that will be used when the ICAP server requests client authentication.
The use of this certificate is optional and is only required if the ICAP server is using mutual authentication. After you download the certificate, install the certificate in your ICAP server's tunnel configuration. To learn more, see [Configuring the ICAP Server with the Mutual Transport Layer Security (MTLS) CA Certificate](/unified/configuring-icap-server-mutual-transport-layer-security-mtls-ca-certificate).
- View a list of all ICAP receivers that were configured for your organization. For ICAP receivers, you can see the following:
- **Name**: The name of the ICAP receiver. You can sort this column.
- **Status**: Displays whether the ICAP receiver is enabled or disabled. You can sort this column.
- **URI**: The DLP server URI. You can sort this column.
- [Modify the table and its columns](/unified/using-tables).
- Edit an ICAP receiver configuration.
- View the Zscaler Incident Receiver page. To learn more, see [About Zscaler Incident Receiver](/unified/about-zscaler-incident-receiver).
- View the Cloud-to-Cloud Incident Forwarding page. To learn more, see [About Cloud-to-Cloud Incident Forwarding](/unified/about-cloud-cloud-incident-forwarding).
![Screenshot of the ICAP Settings page and its features](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/about-icap-receivers-dlp/ZIA-DLP-Incident-Receiver-Page-ICAP-Settings-Tab-C2C.png)