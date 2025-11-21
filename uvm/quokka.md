# Quokka
Source: https://help.zscaler.com/uvm/quokka
PDF: https://help.zscaler.com/pdf/com/en/1528136.pdf

![The Quokka tile](/downloads/uvm/configure/sources/quokka/mceclip0.png)
Quokka is a mobile security and privacy solution. The Quokka source retrieves findings data.
Required Parameters
The API key is a required parameter. To generate the API key, the option should be enabled on the user level by an admin:
- Log in to the Quokka platform.
- From the top right of the page, click the account name to go to the account settings page.
- Select the **Group Admin** tab.
- Click the user you want to edit or create a new user and enable the **API Key** option.
![API Key in the Quokka platform](/downloads/uvm/configure/sources/quokka/mceclip1.png)
- Assign the user the following permissions:
- View Analyzed Apps
- View Reports
- View Shared Apps
- Change API Key
- Android Analysis
- iOS Analysis
- GDPR Report
- OWASP Report
- NIAP Report
- SBOM Report
![Assigning the permissions in the Quokka platform](/downloads/uvm/configure/sources/quokka/mceclip2.png)
- Save the user.
- You can generate an API through the user settings page as a group admin.
- If you are not an admin, in the Quokka platform, from the top right of the page, click your account name to go to the account settings page.
![Account settings in the Quokka platform](/downloads/uvm/configure/sources/quokka/mceclip3.png)
- In the **Security** tab, click **Generate New API Key** or use the existing key.
![Generating a new API key or using the existing key on the Security tab in the Quokka platform](/downloads/uvm/configure/sources/quokka/mceclip4.png)