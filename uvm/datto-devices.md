# Datto Devices
Source: https://help.zscaler.com/uvm/datto-devices
PDF: https://help.zscaler.com/pdf/com/en/1528146.pdf

![The Datto Devices tile](/downloads/uvm/configure/sources/datto-devices/mceclip0.png)
Datto is a secure cloud-based RMM platform that monitors devices such as servers, VMs, ESXi, PCs, laptops and network devices in real-time alerting on issues and flagging potential problems. The Datto Devices source retrieves data on the accounts devices.
Required Parameters
- API Key
- API Secret Key
Retrieving the API Key and Secret Key
To enable API access:
- Log in to the Datto platform.
- Go to Setup > Global Settings > Access Control.
- Select Enable API Access checkbox.
![Selecting the Enable API access checkbox on the Access Control page of the Datto plaform](/downloads/uvm/configure/sources/datto-devices/mceclip1.png)
To create an API token for a specific user:
- Log in to the Datto platform.
- Go to **Setup** > **Users**.
- Select the relevant user.
- Click **Generate API Keys**.
- The **API key** and **API Secret Key** are displayed. Save them in a secure location since they are not available again.
![mceclip2.png](/downloads/uvm/configure/sources/datto-devices/mceclip2.png)
- Save the user.
To learn more, refer to the [Datto documentation](https://rmm.datto.com/help/en/Content/2SETUP/APIv2.htm).