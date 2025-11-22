# Adding an ICAP Receiver for DLP
Source: https://help.zscaler.com/zia/adding-icap-receiver-dlp
PDF: https://help.zscaler.com/pdf/com/en/1400101.pdf

You can forward information about transactions that violate the DLP policy to the [Internet Content Adaptation Protocol (ICAP) receivers](/zia/about-icap-receivers-dlp) you’ve defined in the ZIA Admin Portal.
To add a secure or unencrypted ICAP receiever, you must define them on the DLP Incident Receiver page by providing the public IP address of your DLP server with the port number on which your network firewall initially accepts the secure ICAP traffic sent by the Zscaler service. To learn more, see [][Enabling Secure ICAP](/zia/enabling-secure-icap) and [][Enabling Unencrypted ICAP](/zia/enabling-unencrypted-icap).
If you want to use ICAP receivers for web traffic filtering, see [Adding an ICAP Receiver](/zia/adding-icap-receiver).