# About Machine Groups
Source: https://help.zscaler.com/unified/about-machine-groups
PDF: https://help.zscaler.com/pdf/com/en/1491376.pdf

A Machine Group is a set of an organization’s internal, local machines that need to connect to Private Applications. These local machines are internal directories, such as an Active Directory, that organizations want to connect to prior to logging into Windows. You can manage Machine Groups within the Admin Portal.
Machine Groups provide the following benefits and allow you to:
- Associate the Zscaler Client Connector with a Machine Group.
- Enable [Machine Tunnels for Pre-Windows Login](/unified/deploying-machine-tunnels-pre-windows-login) to gain access to internal applications even when the device's Zscaler Client Connector is not connected to Private Applications.
You can create a new Machine Group whenever you [add a new machine key](/unified/configuring-machine-provisioning-keys). Zscaler recommends deploying a new Machine Group for every Machine Provisioning Key. Devices in a Machine Group can [use Machine Tunnels](/unified/deploying-machine-tunnels-pre-windows-login) to provide access to internal applications even when the device's Zscaler Client Connector is not connected to Private Applications. The Machine Provisioning Key must be added to the Zscaler Client Connector profile rule for successful Machine Tunnel enrollment. To learn more, see [Configuring Zscaler Client Connector Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
About the Machine Groups Page
On the Machine Groups page (Administration > Identity > Private Access > Machine Groups), you can do the following:
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all the Machine groups that are configured for your organization. For each Machine group, you can see the name of the Machine group.
- [Edit a configured Machine group.](/unified/editing-machine-groups)
- Delete a Machine group.
- Expand all of the rows in the table to see more information about each Machine group.
![Viewing the Machine Groups page](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/about-machine-groups/unified-machine-groups-page.png)