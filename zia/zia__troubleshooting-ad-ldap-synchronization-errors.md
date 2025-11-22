# Troubleshooting AD & LDAP Synchronization Errors
Source: https://help.zscaler.com/zia/troubleshooting-ad-ldap-synchronization-errors
PDF: https://help.zscaler.com/pdf/com/en/1399616.pdf

The following troubleshooting guidelines and tips are for the Active Directory (AD) and Lightweight Directory Access Protocol (LDAP) synchronization errors.
Unable to Synchronize with a Directory Server
If you're unable to synchronize with a directory server:
- Verify the connectivity between the Zscaler Central Authority (CA) server and the directory server
- Verify that the BIND password is correct
A User Is Unable to Authenticate
If a user's password is changed on the AD or LDAP server but the user is still using the old password, you can do the following to resolve this issue:
- Reset the password on the AD or LDAP server
- Check the error code
The following table lists the error codes that the Zscaler service displays when it can't authenticate a user:
| Error Code | Description | When It Occurs | What to Do |
| ---------- | ----------- | -------------- | ---------- |
| 100 | The ldapsearch couldn't be done against the directory. | Invalid LDAP filter. | Check the LDAP search filter in the Zscaler service portal and ensure the syntax is correct. Verify if the same filter works with the ldapsearch. |
| 101 | Incorrect password. | Incorrect login password. | Correct the password. |
| 102 | The LDAP connection closed. | The server closed the connection unexpectedly. | Retry. This should only be a transient error. |
| 103 | The user wasn't found on the LDAP servers (search failed). | The ldapsearch for the user failed. The search may be done using "email" or "username" based on advanced search status. | Check if a manual ldapsearch returns the user with the same query as the one configured in the ZIA Admin Portal. |
| 104 | The user's DN couldn't be found. | The user's DN couldn't be read due to LDAP library issues. | Consult your LDAP admin. |
| 105 | Error performing a BIND with the user's credentials. | The DN may be invalid. | Check if a manual BIND works with the same user credentials. |
| 106 | Internal error. | A deleted user tried to log in. | Check if the user is in the list of synchronized users. Synchronize the users. |
| 108 | The LDAP context wasn't found. | A user in a second directory tried to log in when there was no secondary LDAP configuration. | Zscaler must "unset" flags in the DB for secondary users or do a sync-preview sync once for your organization. |
| 109 | The synchronization is in progress. Users are not allowed to log in. | A user tried to log in during the synchronization. | Wait until the synchronization is completed. |
| 110 | The LDAP bind failed. | The admin's LDAP bind password may be wrong. | Check the password. |
| 111 | Internal error. | Internal error. | Retry or contact Zscaler Support. |
| 112 | The advanced search query couldn't be sent. | Your organization is using an advanced search query for logins, and there's a problem with the advanced search filter used. | Check the advanced search filter. Ensure that ldapsearch returns users with the same filter. |
| 113 | The user wasn't found in the list of synchronized users. | The user is not in the list of synchronized users. | Synchronize the user data and retry. |
| 114 | Login failed. The connection to the directory server was reset. | The connection to the directory server was reset. | Retry. |
| 115 | Login failed. The configuration changed. | An admin activated new configuration settings in the ZIA Admin Portal. | Retry. |
| 116 | Login failed. The user was deleted. | A deleted user tried to log in. | Check if the user is in the list of synchronized users. Synchronize the user data and retry. |