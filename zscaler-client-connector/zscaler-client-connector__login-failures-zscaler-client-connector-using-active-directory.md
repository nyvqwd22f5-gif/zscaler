# Login Failures with Zscaler Client Connector Using Active Directory
Source: https://help.zscaler.com/zscaler-client-connector/login-failures-zscaler-client-connector-using-active-directory
PDF: https://help.zscaler.com/pdf/com/en/1361626.pdf

Some users may experience issues with logging into Zscaler Client Connector when in combination of the following scenarios:
- Users have updated to the recent Microsoft patches
- Users are facing connectivity issues with Active Directory (AD)
This issue occurs due to the failure in Microsoft cryptography API that tries to reach out to the AD for verification. This issue is also observed with Outlook even when Zscaler Client Connector is not installed on the systems. In some scenarios, ensuring connectivity with AD resolves the issue.
Microsoft provides certain recommendations to address most of the scenarios. To learn more, see [Microsoft Documentation.](https://support.microsoft.com/en-ca/help/3205778/dpapi-masterkey-backup-failures-when-rwdc-isn-t-available)
Zscaler is also working on a solution to this Microsoft limitation in an upcoming patch release.
Zscaler recommends you to upgrade to Zscaler Client Connector 2.1.2.112 or later versions for Windows (released after September 10, 2020) to reduce the impact of this issue.