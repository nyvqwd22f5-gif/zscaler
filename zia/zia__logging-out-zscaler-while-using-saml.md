# Logging Out from Zscaler While Using SAML
Source: https://help.zscaler.com/zia/logging-out-zscaler-while-using-saml
PDF: https://help.zscaler.com/pdf/com/en/1402241.pdf

You can choose from a variety of methods to log out of Zscaler to trigger reauthentication for users who are using SAML with auto-provisioning or Hosted DB authentication. You should also choose one of the following methods if SCIM is not supported for the IdP server being used.
These methods only apply if you are forwarding traffic using PAC files and using cookie-based authentication. If you are using Zscaler Client Connector, see [Using Zscaler Client Connector](/zscaler-client-connector/using-zscaler-client-connector). To learn more about cookie-based authentication, see [About Zscaler Cookies](/zia/about-zscaler-cookies).
To log out from Zscaler, choose one of the following methods:
- [Log Out the User from Zscaler](#Triangle1)
- [Delete the Zscaler Cookies from the Browser](#triangle2)
- [Delete the User from the ZIA Admin Portal](#triangle3)
- [Use CSV Import to Delete the User from the Zscaler Database](#triangle4)
[]To trigger reauthentication for the user, see [ip.zscaler.com](http://ip.zscaler.com) and click **Logout**.
[See image.](#logout-image)
[]To learn more about Zscaler's cookies, see [About Zscaler Cookies](/zia/about-zscaler-cookies).
[]Complete the following steps:
- Go to **Administration** > **User Management**.
- In the **Users** section, select the user that you want to delete by clicking the **Edit** icon for the selected user.
[See image.](#Edit-Icon)
- Select **Delete** to delete the user.
[See image.](#Delete-User)
[]![Delete User Window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/how-logout-zscaler-while-using-saml-draft/Admin%20UI%20-%20Delete%20User.png)
[]To learn more about CSV Import, see [Importing User Information from a CSV File](/zia/importing-user-information-csv-file).
[]![Logout of Zscaler](/downloads/zscaler-tech-pubs-style-guide/draft-articles/how-logout-zscaler-while-using-saml-draft/ip-logout.png)
[]![Admin UI Edit Icon](/downloads/zscaler-tech-pubs-style-guide/draft-articles/how-logout-zscaler-while-using-saml-draft/Admin%20UI%20-%20Edit%20Icon.png)