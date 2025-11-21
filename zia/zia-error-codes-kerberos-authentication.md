# ZIA Error Codes for Kerberos Authentication
Source: https://help.zscaler.com/zia/zia-error-codes-kerberos-authentication
PDF: https://help.zscaler.com/pdf/com/en/1399596.pdf

If Kerberos authentication fails, the Zscaler service displays a page with an error code. The following table lists the information on the Kerberos authentication error codes. For instructions on how to troubleshoot Kerberos, see [Troubleshooting Kerberos](/zia/troubleshooting-kerberos).
[](/zia/what-my-cloud-name-zia)
[](/zia/kerberos-configuration-example-trust-relationship-windows-server-2012-and-gpo-push#create-new-trust)
| Error Code | Description | When It Occurs | What to Do |
| ---------- | ----------- | -------------- | ---------- |
| 391000 | The page cannot load. | Generic error code. | Contact Zscaler Support. |
| 441000, 461000 | The user cannot be found. | The user was deleted or cannot be found in the registered domain. | Add the user. |
| 451000 | The domain does not exist. | The realm is not a registered domain on the Zscaler service. | Contact Zscaler support to add the realm as a registered domain. |
| 471000
(Occurrence 1) | The proxy authorization header does not contain the encoded Kerberos ticket. In almost all cases, this means that NTLM was used. | The traffic was sent to the ZIA Public Service Edge IP address. The default Zscaler PAC file was used instead of the Kerberos PAC file.
**Symptoms**: klist does not show either the ZIA Public Service Edge or KDC tickets. | Change the PAC file. Ensure that you use the Kerberos PAC file. |
| 471000
(Occurrence 2) |  | The user's computer does not have the GPO updates, the GPO updates are not on the domain controller, or the user is not logged in to the domain.
**Symptoms**: A traffic capture from the user's computer does not show any query to the domain controller for the Zscaler ticket. | Verify the registry settings to ensure the user's computer has the Zscaler Kerberos settings. If they are not on the computer, verify that the domain controller has the GPO configurations.
Verify that the user is logged in to the domain. |
| 471000
(Occurrence 3) |  | AES encryption is not enabled in the realm trust on the domain controller.
**Symptoms**: klist does not show either the ZIA Public Service Edge or KDC tickets.
A traffic capture shows the domain controller returning ETYPE_NOSUPP errors. | Modify the realm trust relationship and ensure that the AES encryption option is selected. |
| 471000
(Occurrence 4) |  | The realm trust relationship is not configured on the domain controller or the realm trust was configured with an incorrect password.
**Symptoms**: klist does not show the Zscaler KDC or ZIA Public Service Edge tickets.
A traffic capture shows the domain controller returning PRINCIPAL_UNKNOWN error. | Verify the realm trust configuration. Ensure that the realm name is in upper case and that the Zscaler cloud name is correct. To learn how you can find your cloud name, see What is my cloud name for ZIA?
If they are both correct, then the passwords in the organization's realm and the Zscaler realm might not match. Log in to the ZIA Admin Portal, regenerate the trust password, and copy it. On the domain controller, delete the trust configuration and create a new one as described in Kerberos Trust Relationship Configuration Guide for Windows Server 2012 and GPO Push. Ensure that you use the newly generated password that you copied from the ZIA Admin Portal. |
| 471000
(Occurrence 5) |  | The user's computer cannot connect to the domain controller.
**Symptoms**: When you run klist purge to clear the tickets, refresh the browser, and then run klist again, Kerberos tickets are not displayed, including those of the domain controller. | Verify that the computer can contact the domain controller.
If the user is using DirectAccess, run netsh name show effectivepolicy to determine if the DirectAccess client considers the workstation as being in the intranet or outside |
| 48100 | Invalid encoding of Kerberos credentials. | Possible header corruption. Ensure that there is no intermediate proxy or L7 device that may be corrupting the header. | Contact Zscaler Support. |
| 491000, 501000
(Occurrence 1) | Invalid Kerberos token or username. | The computer time is incorrect. | Kerberos is very sensitive to clocks being in sync. Ensure that computer time is correct and it synchronizes with an NTP server. |
| 491000, 501000
(Occurrence 2) |  | Other issues. | Contact Zscaler Support. |
| 510000 | The user name is too long. | The user's login name exceeds the maximum allowed characters. | Contact Zscaler Support. |