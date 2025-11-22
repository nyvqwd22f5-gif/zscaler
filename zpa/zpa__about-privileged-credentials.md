# About Privileged Credentials
Source: https://help.zscaler.com/zpa/about-privileged-credentials
PDF: https://help.zscaler.com/pdf/com/en/1485551.pdf

Privileged credentials can be used to streamline access to privileged consoles by mapping authentication details using a [privileged credentials policy](/zpa/about-privileged-credentials-policy). The user can then gain access to the privileged console that the privileged credentials were designated to. After you create a privileged credential, you can map it to a privileged console by creating a privileged credential policy using the SAML and SCIM policy criteria types.
Privileged credentials provide the following benefits and enable you to:
- Allow controlled access to users by using a privileged console with allocated credentials.
- Provide users access to the privileged console without having to manually log in.
- Allow users to start a privileged console session without needing to provide credentials.
If you want to use privileged credentials, you must first create the [privileged portals](/zpa/about-privileged-portals) and [privileged consoles](/zpa/about-privileged-consoles) that you want to assign the credentials to. You can create [privileged credential pools](/zpa/about-privileged-credential-pools) to group existing privileged credentials.
About the Privileged Credentials Page
On the Privileged Credentials page (Resource Management > Privileged Remote Access > Privileged Credentials > Credentials), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Privileged Credentials page.
-
Filter the information that appears in the table. By default, no filters are applied. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
If you are using a [Microtenant](/zpa/about-microtenants), then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the privileged credentials configured within that specific Microtenant. The options for the filter are based on access type (**Global **and **Configured within Microtenant**). The **Global** option filters the information in the table that is configured within the Default Microtenant. The only available operator for this filter type is **Equals**.
- [Add a new privileged credential.](/zpa/configuring-privileged-credentials)
- View a list of all privileged credentials that are configured. For each privileged credential, you can see:
- **Name**: The name of the privileged credential.
- **Type**: The protocol type that was designated for that particular privileged credential. The protocol type options are SSH, RDP, and VNC. Each protocol type has its own credential requirements.
After the type is selected and the privileged credential is saved, this option can’t be changed.
- **Username**: The username associated with the credentials you are using.
- **Updated Time**: The date, time, and time zone that the privileged credential was created.
Privileged credentials that are created in the Default Microtenant are inherited across Microtenants.
- [Edit an existing privileged credential.](/zpa/editing-privileged-credentials)
If the credentials are changed after you created and saved the privileged credential, you need to update the new credential details (e.g., Username, Password, Private Key) for the privileged credential to continue being used.
- [Move the privileged credential in a Microtenant](/zpa/moving-resources-microtenant#PrivilegedCredentials).
If privileged credential policies are associated with the privileged credential, then the policies must be deleted to move the privileged credential to a different Microtenant.
- Delete a privileged credential.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Credential Pools](/zpa/about-privileged-credential-pools) page to add new privileged credential pools or manage existing privileged credential pools.
- Go to the [Privileged Approvals](/zpa/about-privileged-approvals) page to add new approvals or manage existing approvals.
- Go to the [Privileged Consoles](/zpa/about-privileged-consoles) page to add new consoles or manage existing consoles.
- Go to the [Privileged Portals](/zpa/about-privileged-portals) page to add new privileged portals or manage existing privileged portals.
![Viewing the Privileged Credentials page](/downloads/zpa/privileged-remote-access-management/privileged-credentials/about-privileged-credentials/Privileged%20Credentials%20page%20w%20steps_0.png)