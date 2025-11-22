# NSS Feed Output Format: Tunnel Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-tunnel-logs
PDF: https://help.zscaler.com/pdf/com/en/1497811.pdf

This article includes table pagination. Use the Search function in the tables to find your desired field.
The tunnel Nanolog Streaming Service (NSS) feed specifies the data from the tunnel logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample tunnel log.](#nss-feed-output-tunnel-example)
The following tables display information about the tunnel log fields and possible values for those fields.
Fields that support obfuscation are documented in the following tables with the prefix `o` (e.g., `%s{olocation}`). To obfuscate a field, manually add the prefix `o` before the field name in the Feed Output Format in the Admin Portal.
IKE Phase 1
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datetime} | The date and time of the event. | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunnelactionname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Equals WL_TUNNEL_IPSECPHASE1 for this record type |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{vpncredentialname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The VPN credential name for the IPSec tunnel | jdoe@safemarch.com |
| %s{ovpncredentialname} | The obfuscated version of the VPN credential name for the IPSec tunnel | 4094304256 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{locationname} | The location name | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Headquarters |
| %s{olocationname} | The obfuscated version of the location name | 2168890624 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destvip} | The tunnel destination VIP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
165.225.104.35 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{sourceip} | The tunnel source IP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
116.113.61.135 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{lifetime} | The lifetime of IKE Phase 1 (seconds) | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
86400 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%lu{spi_in} | The initiator cookie |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%lu{spi_out} | The responder cookie |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{srcport} | The tunnel source port | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
500 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{dstport} | The tunnel destination port | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
500 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{algo} | The encryption algorithm | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
DES_CBCIDEA_CBCBLOWFISH_CBCRC5_R16_B64_CBCTHREE_DES_CBCCAST_CBCAES_CBC |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{authentication} | The authentication algorithm | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
HMAC_MD5HMAC_SHAHMAC_SHA256HMAC_SHA384HMAC_SHA512DES_MACKPDK |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{authtype} | The authentication type | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
PSKEYDSSSIGRSASIGRSAENCRSAREVEGENCEGREV |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{vendorname} | The vendor name of the edge device | CISCOJUNIPERSTRONGSWANSHREWSOFTARUBACHECKPOINTQUICKSECSONICWALL |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{ikeversion} | The IKE version (1 or 2) |  |
| %d{recordid} | The unique record identifier for each log |  |
IKE Phase 2
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datetime} | The date and time of the event | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunnelactionname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Equals WL_TUNNEL_IPSECPHASE2 for this record type |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{vpncredentialname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The VPN credential name for the IPSec tunnel | jdoe@safemarch.com |
| %s{ovpncredentialname} | The obfuscated version of the VPN credential name for the IPSec tunnel | 4094304256 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{locationname} | The location name | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Headquarters |
| %s{olocationname} | The obfuscated version of the location name | 2168890624 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destvip} | The tunnel destination VIP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
165.225.104.35 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{sourceip} | The tunnel source IP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
116.113.61.135 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{lifetime} | The lifetime of IKE Phase 2 (seconds) | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
28800 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{spi} | The Security Parameter Index (SPI) |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{algo} | The encryption algorithm | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
DES_CBCIDEA_CBCBLOWFISH_CBCRC5_R16_B64_CBCTHREE_DES_CBCCAST_CBCAES_CBC |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{authentication} | The authentication algorithm | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
NoneHMAC-MD5HMAC-SHAHMAC-SHA256HMAC-SHA384HMAC-SHA512DES-MACKPDK |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{authtype} | The authentication type | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
NonePSKEYDSSSIGRSASIGRSAENCRSAREVEGENCEGREV |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destipstart} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Destination IP start |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destipend} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Destination IP end |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{srcipstart} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Source IP start |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{srcipend} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Source IP end |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{srcportstart} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Source port start |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{destportstart} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Destination port start |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{lifebytes} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Life bytes. The amount of traffic to be transacted through a tunnel before renegotiation. |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunnelprotocol} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The IPSec tunnel protocol type. Zscaler only supports ESP. | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
NoneISAKMPAHESPIPCOMP |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{protocol} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Phase 2 policy proposal - Protocol | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
AnyTCPICMPUDP |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{ikeversion} | The IKE version (1 or 2) |  |
| %d{recordid} | The unique record identifier for each log |  |
Tunnel Events
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datetime} | The date and time of the event | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunnelactionname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Equals WL_TUNNEL_EVENT for this record type |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{vpncredentialname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The VPN credential name for the IPSec tunnel | jdoe@safemarch.com |
| %s{ovpncredentialname} | The obfuscated version of the VPN credential name for the IPSec tunnel | 4094304256 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{locationname} | The location name | Headquarters |
| %s{olocationname} | The obfuscated version of the location name | 2168890624 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destvip} | The destination VIP address | 165.225.104.35 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{sourceip} | The source IP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
116.113.61.135 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunneltype} | The tunnel type | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
GREIPSEC_IKEV1IPSEC_IKEV2 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{event} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The tunnel status | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
UPDOWNREKEYPHASE1_DOWNPHASE2_DOWNPHASE1_ERRORPHASE2_ERROR |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{eventreason} | The reason for the tunnel status change | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
NoneEXPIREDPSKEY_NOTFOUNDPSKEY_MISMATCHINVALID_PROPOSALDPD_TIMEOUTTIMEOUTORG_EXCLUDED |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{srcport} | The source port |  |
| %d{recordid} | The unique record identifier for each log |  |
Tunnel Samples
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datetime} | The date and time of the event | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunnelactionname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Equals WL_TUNNEL_SAMPLES for this record type |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{vpncredentialname} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The VPN credential name for the IPSec tunnel | jdoe@safemarch.com |
| %s{ovpncredentialname} | The obfuscated version of the VPN credential name for the IPSec tunnel | 4094304256 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{locationname} | The location name | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
Headquarters |
| %s{olocationname} | The obfuscated version of the location name | 2168890624 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{destvip} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The destination VIP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
165.225.104.35 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{sourceip} | The source IP address | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
116.113.61.135 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%s{tunneltype} | The tunnel type | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
GREIPSEC_IKEV1IPSEC_IKEV2 |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%lu{txbytes} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The bytes transmitted in a 60-second sample window from Zscaler to the customer |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%lu{rxbytes} | The bytes received in a 60-second sample window by Zscaler from the customer |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{txpackets} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The packets transmitted in a 60-second sample window from Zscaler to the customer |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{rxpackets} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The packets received in a 60-second sample window by Zscaler from the customer |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{dpdrec} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The number of DPD packets received in a 60-second sample window. Only for IPSec tunnels, empty for GRE. |  |
| &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
&amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
%d{srcport} | &amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;gt;
The source port |  |
| %d{recordid} | The unique record identifier for each log |  |
[]"Thu Jun 23 16:24:59 2022","Tunnel Samples","GRE","NA(GRE Tunnel)","new-gre","10.66.89.115","10.66.68.68","0","2","3","160","753","0","7112472280601133057"