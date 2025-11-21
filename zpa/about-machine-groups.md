# About Machine Groups
Source: https://help.zscaler.com/zpa/about-machine-groups
PDF: https://help.zscaler.com/pdf/com/en/1484671.pdf

[Watch a video about machine groups.](https://fast.wistia.net/embed/iframe/11naj2mw13)
A machine group is a set of an organization’s internal, local machines that need to connect to ZPA. These local machines are internal directories, such as an Active Directory, that organizations want ZPA to connect to prior to logging into Windows. You can manage machine groups within the ZPA Admin Portal.
Machine groups provide the following benefits and allow you to:
- Associate the Zscaler Client Connector with a [machine group](/zpa/about-machine-groups).
- Enable [Machine Tunnels for Pre-Windows Login](/zpa/deploying-machine-tunnels-pre-windows-login) to gain access to internal applications even when the device's Zscaler Client Connector is not connected to ZPA.
You can create a new machine group whenever you [add a new machine key](/zpa/configuring-machine-provisioning-keys). Zscaler recommends deploying a new machine group for every machine provisioning key. Devices in a machine group can [use Machine Tunnels](/zpa/deploying-machine-tunnels-pre-windows-login) to provide access to internal applications even when the device's Zscaler Client Connector is not connected to ZPA. The machine provisioning key must be added to the Zscaler Client Connector profile rule for successful Machine Tunnel enrollment. To learn more, see [Configuring Zscaler Client Connector Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
About the Machine Groups Page
On the Machine Groups page (Authentication > Device Authentication > Machine Groups), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Machine Groups page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Expand all rows in the table to see more information about each machine group.
- View a list of all the machine groups that are configured for your organization. For each machine group, you can see the name of the machine group.
- [Edit a configured machine group.](/zpa/edit-machine-groups)
- Delete a machine group.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Machine Provisioning Keys](/zpa/about-machine-provisioning-keys) page to manage keys for your machines.
![Viewing and Managing Machine Groups ](/downloads/zpa/authentication/machine-authentication/about-machine-groups/zpa-machine-groups.png)