# Datto Alerts
Source: https://help.zscaler.com/uvm/datto-alerts
PDF: https://help.zscaler.com/pdf/com/en/1528156.pdf

![The Datto Alerts tile](/downloads/uvm/configure/sources/datto-alerts/mceclip0.png)
Datto is a secure cloud-based RMM platform that monitors devices such as servers, VMs, ESXi, PCs, laptops, and network devices in real-time alerting on issues and flagging potential problems. The Datto Alerts source retrieves data on all open alerts.
Required Parameters
- API Key
- API Secret Key
- Include Muted Alerts: When checked, the data retrieved includes muted open alerts.
Retrieving the API Key and Secret Key
To enable API access:
- Log in to the Datto platform.
- Go to **Setup** > **Global Settings** > **Access Control**.
- Select **Enable API Access** checkbox.
![Selecting the Enable API Access checkbox in the Access Control section in the Datto platform](/downloads/uvm/configure/sources/datto-alerts/mceclip1.png)
To create an API token for a specific user:
- Log in to the Datto platform.
- Go to **Setup** > **Users**.
- Select the relevant user.
- Click **Generate API Keys**.
- The **API key** and **API Secret Key** are displayed. Save them in a secure location since they are not available again.
![Saving the API key and API secret key on the API page of the Datto platform](/downloads/uvm/configure/sources/datto-alerts/mceclip2.png)
- Save the user.
To learn more, refer to the [Datto documentation](https://rmm.datto.com/help/en/Content/2SETUP/APIv2.htm).