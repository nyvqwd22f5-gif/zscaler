# About Privileged Credential Pools
Source: https://help.zscaler.com/unified/about-privileged-credential-pools
PDF: https://help.zscaler.com/pdf/com/en/1524971.pdf

Privileged credential pools can be used to streamline access to privileged consoles by mapping authentication details using a privileged credentials policy. Multiple users can gain access to the privileged console that the privileged credential pools are designated to. After you create a privileged credential pool, you can map it to a privileged console by creating a privileged credential policy using the SAML and SCIM policy criteria types.
Privileged credential pools provide the following benefits and enable you to:
- Allow controlled access to multiple users by using a privileged console with allocated credential pooling.
- Provide users access to the privileged console without having to manually log in.
- Allow users to start a privileged console session without needing to provide credentials.
- Prevent users from accessing the privileged console if all privileged credentials from the privileged credentials pool are exhausted or in use.
If you want to use privileged credential pools, you must first [create privileged credentials](/unified/configuring-privileged-credentials) and the [privileged portals](/unified/about-privileged-portals) and [privileged consoles](/unified/about-privileged-consoles) that you want to assign the credentials to.
About the Privileged Credential Pools Page
On the Privileged Credential Pools page (Policies > Access Control > Clientless > Privileged Credentials > Credentials Pools), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
If you are using a [Microtenant](/unified/about-private-app-microtenants), then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the privileged credentials configured within that specific Microtenant. The options for the filter are based on access type (**Global **and **Configured within Microtenant**). The **Global** option filters the information in the table that is configured within the Default Microtenant. The only available operator for this filter type is **Equals**.
- Refresh the Credential Pools page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables).
- [Add a new privileged credential pool.](/unified/configuring-privileged-credential-pools)
- Expand all the displayed rows in the table to see more information about each privileged credential pool.
- View a list of all privileged credential pools that are configured. For each privileged credential pool, you can see:
- **Name**: The name of the privileged credential pool. To view credentials, enter the name of the credentials in the search field that you want to copy.
- **Credential Type**: The protocol type that was designated for that particular privileged credential. The protocol type options are **SSH**, **RDP**, **VNC**, and **RealVNC**. Each protocol type has its own credential requirements.
After the type is selected and the privileged credential is saved, this option can’t be changed.
- **Privileged Credentials**: The number of privileged credentials that are assigned to the privileged credential pool.
- **Updated Time**: The date, time, and time zone that the privileged credential pool was created.
Privileged credentials that are created in the Default Microtenant are inherited across Microtenants.
- [Edit an existing privileged credential pool.](/unified/editing-privileged-credential-pools)
You can only update the name of the privileged credential pool and change the selection of the privileged credentials. You can't change the protocol type.
- Delete a privileged credential.
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
- Go to the [Credentials](/unified/about-privileged-credentials) page to manage your privileged credentials.
![Viewing the Privileged Credential Pools page](/downloads/unified/policies/private-applications/access-control/about-privileged-credential-pools/experience-center-credential-pools-page1.png)