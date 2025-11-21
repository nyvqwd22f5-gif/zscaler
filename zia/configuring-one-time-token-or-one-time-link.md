# Configuring a One-Time Token or One-Time Link
Source: https://help.zscaler.com/zia/configuring-one-time-token-or-one-time-link
PDF: https://help.zscaler.com/pdf/com/en/1399626.pdf

You can configure the Zscaler service to email users a link or temporary password that they can use to log in to the service once. This is useful when creating new users or resetting forgotten passwords. The service allows a user to request a new temporary password only once every 24 hours. Both the unique link and unique password are valid for 24 hours.
The Zscaler Central Authority (CA) authenticates users according to the method configured for the organization. When a one-time token is used for authentication, after a user enters the temporary password and successfully logs in to the service, the user is required to enter a new password. The CA stores this password and sets the gateway cookie.
You can use this feature when users are hosted by the service or synchronized from a directory server, as long as the service has the users' valid email addresses. When you enable authentication through a one-time token for users synchronized from a directory server, the passwords are stored in the Zscaler database and not in the directory server. Therefore when users log in to the service and try to authenticate, the service matches their password with the one in its database, not the password in the directory server.
This feature doesn't apply to users with Zscaler Client Connector.
Prerequisites
Ensure that the [user](/zia/adding-user-account) has an email address entered in the **Temporary Authentication Email** field. This is the email address the Zscaler service sends the email with the link or password to. This email address doesn't need to belong to the organization's domain. If this field is empty, the service sends the link or password to the **User ID **instead. If the users are [synchronized from an Active Directory (AD) or OpenLDAP](/zia/configuring-zscaler-service-synchronize-data), use the email addresses that were synchronized from the directory server.
Configuring a One-Time Token or One-Time Link
To configure a one-time token or one-time link as a temporary authentication method:
- Go to **Administration **>** Authentication Settings**.
- Under** Temporary Authentication**, choose one of the following options:
- **One-Time Token**: Sends the user a temporary password to log in.
- **One-Time Link**: Sends the user a temporary hyperlink to log in.
- Click **Save**.
- Under **Temporary Authentication**, click **Send Authentication E-mail**.
The **Send Authentication Email** window appears.
- In the **Send Authentication Email** window:
- **Send To**: Choose whether the Zscaler service sends the authentication email to users or groups.
- **Users**: Select the users to which the service sends the authentication email.
- **Groups**: Select the groups to which the service sends the authentication email.
- Click **Send Credentials**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
Logging In With a One-Time Token or One-Time Link
After your users receive the email, they can then log in to the Zscaler service with the temporary authentication method:
- [Logging in with a One-Time Token](#onetimetoken)
- [Logging in with a One-Time Link](#onetimelink)
[]
The Zscaler service sends an email with the one-time temporary password.
To log in with a one-time token:
- Log in to the Zscaler service with the temporary password.
- After logging in, enter a new password.
[]
The Zscaler service sends an email with the one-time link.
To log in with a one-time link, click the link in the email to log in to the Zscaler service.