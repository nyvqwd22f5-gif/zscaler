# SentinelOne Connectors
Source: https://help.zscaler.com/uvm/sentinelone-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528041.pdf

![The SentinelOne Threats, SentinelOne Vulnerabilities, and SentinelOne Assets tile](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip0.png)
SentinelOne provides a range of products and services through its Singularity XDR platform, offering comprehensive protection against cyber threats such as malware, ransomware, and advanced persistent threats (APTs).
There are three available SentinelOne connectors:
- Threats: Retrieves thread-related data, flagged as a threat in the Management Console's Threats section when SentinelOne Agents detect suspicious or malicious activity.
- Vulnerabilities: Retrieves vulnerability information from SentinelOne application data.
- Assets: Retrieves data related to SentinelOne agents.
Required Parameters
- [Server URL](#server-url)
- [API Token](#api-token)
[]
The server URL is your specific SentinelOne instance which can be found in your management console URL, in the format `https://<your_InstanceID>.sentinelone.net`. For example, `https://usea1-acme.sentinelone.net`.
![mceclip1.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip1.png)
[]
The following process outlines how to create an API token using a service user. You can also generate the API key associated with a console user.
To create an API token:
- Log into the SentinelOne Management Console as an admin.
- From the left-side navigation, click **Settings**.
**![mceclip6.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip6.png)
**
- Click the **Users** tab.
- Click **Service Users**.
- Click **Actions**.
![mceclip7.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip7.png)
g
- Click **Create New Service User**.
- In the **Create New Service User** window, configure the following:
- **Name**: Enter a name for the service user.
- **Description**: Enter a description.
- **Expiration Date**: From the drop-down menu, select an expiration date.
- Click **Next**.
**![mceclip3.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip3.png)
**
- In the** Select Scope of Access **window:
- Select the **Site**.
- Select the **Viewer **role.
- Click** Create User**.
**![mceclip4.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip4.png)
**
- Copy the API Token** **and save it in a secure location. This is the last time the token is viewable.
![mceclip5.png](/downloads/uvm/configure/sources/sentinelone-connectors/mceclip5.png)