# Deleting Users in SCIM
Source: https://help.zscaler.com/unified/deleting-users-scim
PDF: https://help.zscaler.com/pdf/com/en/1491501.pdf

Using [SCIM](/unified/about-scim) for identity management allows for quick removal of users. When you delete users in your system, the same users are quickly removed from the Zscaler database. Users that are no longer in your organization will not have access to your private applications.
Deleting users in SCIM applies to users connected to the Private Applications service using Zscaler Client Connector. Users accessing applications via [Browser Access](/unified/about-browser-access) can not be removed from Private Applications using SCIM.
To start the removal process, delete the user from within your IdP. Following a SCIM update from the IdP to Private Applications, the user is automatically removed from the Private Applications service. You can verify that the user is no longer in Private Applications by going to the [SCIM Users page](/unified/about-scim-users) and checking the table for the user name.
If the IdP is Okta, users are not deleted. Instead, users are deactivated. Deactivated users can no longer access your private applications.