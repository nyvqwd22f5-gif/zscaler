# NetBox Connectors
Source: https://help.zscaler.com/uvm/netbox-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528006.pdf

![The NetBox Devices, NetBox IP Addresses, and NetBox Virtual Machines tiles](/downloads/uvm/configure/sources/netbox-connectors/mceclip0.png)
NetBox is an infrastructure resource modeling (IRM) platform that supports network automation and management, including IP address management (IPAM), device inventory, and virtual machine and cluster management.
There are three available NetBox** **connectors:
- Devices: Retrieves types of devices and where they are installed.
- IP Addresses: Retrieves IP networks and addresses, VRFs, and VLANs.
- Virtual Machines: Retrieves your virtual machines and clusters.
Required Parameters
- [API Token](#api-token)
- [Netbox URL](#url)
Roles and Permissions
Any NetBox user has the ability to generate an API token. Alternatively, admins have the option to create a dedicated user specifically for generating the API token with more controlled permissions. The following table outlines the minimally required permissions needed for the user with which the API token is associated:
| **Stream** | **Permissions** |
| ---------- | --------------- |
| NetBox Devices | `DCIM > Device` |
| NetBox IP Addresses | `IPAM > IP Address` |
| NetBox Virtual Machines | `Virtualization > Virtual Machine` |
[]
To create the API Token, you’ll need to be a **NetBox Admin**.
To retrieve the API token:
-
In the NetBox platform, from the top right, select your user profile and then click API Tokens. Alternatively, from the left-side navigation, go to **Admin** > **Authentication**.
![Selecting API Tokens in the NetBox platform](/downloads/uvm/configure/sources/netbox-connectors/mceclip1.png)
- Click **Add a Token**.
- **User**: If you created a dedicated user with restricted permissions, from the **User** drop-down menu, select the user. If you did not create a dedicated user with restricted permissions, leave your user selected.
- **Write enabled**: Deselect the checkbox.
- **Expires**: Optionally, enter an expiration date. If an expiration date is set on the token, it needs to be refreshed upon expiration to ensure continuous connectivity.
- **Description**: Optionally, enter a description.
- **Allowed IPs**: Optionally, add a list of allowed IP addresses. Restricting IP addresses is not recommended.
- Click **Create**.
**![Adding the token details in the NetBox platform](/downloads/uvm/configure/sources/netbox-connectors/c1c41654-0a1c-427b-be10-dcc99dbebb98.png)
**
[]
The NetBox URL is your specific NetBox instance which can be found in your management console URL in the format `https://<your_instance>.cloud.netboxapp.com`. For example, `https://acme78.cloud.netboxapp.com`.
![The NetBox URL in the NetBox platform](/downloads/uvm/configure/sources/netbox-connectors/3b0a8437-1d71-4f15-8e9c-fec3a60290bd.png)