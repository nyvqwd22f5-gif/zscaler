# End-of-Support for 3DES on IPSec
Source: https://help.zscaler.com/eos-eol/end-support-3des-ipsec
PDF: https://help.zscaler.com/pdf/com/en/1269836.pdf

Zscaler no longer supports 3DES for IPSec encryption (IKE Phase 2 only), as documented in the 5.4 Late-July Patch Release Notes.
Zscaler recommends that you use null encryption for your IPSec tunnels to the Zscaler service. Traffic sent to the internet does not require additional encryption. Sensitive content is currently encrypted using TLS between the client and the destination server.
If you must encrypt traffic using IPSec (for regulatory or compliance reasons), and you have the appropriate entitlement, use AES encryption.
If you need help changing your configuration or if you have additional questions or concerns, contact Zscaler Support via the Support link in the Admin Portal.
Announcement date: August 25, 2017