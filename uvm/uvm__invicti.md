# Invicti
Source: https://help.zscaler.com/uvm/invicti
PDF: https://help.zscaler.com/pdf/com/en/1528291.pdf

![The Invicti tile](/downloads/uvm/configure/sources/invicti/126163bb-7b67-4274-aef6-4b31e652edaa.png)
Invicti is a DAST tool for DevOps/DevSecOps teams to secure the applications that run their organizations. The Invicti source retrieves vulnerability data, descriptions, cvss, remediation recommendations, and more for digital assets.
Required Parameters
- User ID
- API Token
Retrieving your API Credentials
- In the Invicti platform, from the top right of the page, go to the user menu.
- Select **API Settings**.
- Enter your password and click **Submit**. This does not apply if you use single-sign on.
- On the **API Settings** page, your **User ID** and **API Token** are displayed.
![API Settings page in the Invicti platform](/downloads/uvm/configure/sources/invicti/00f3cb61-438a-4164-8602-c08c9ae04dea.png)
Setting up the Connector in the SecOps Platform
When setting the Invicti connector in the SecOps platform, you see two checkboxes:
- **Strip HTML from data**: When checked, vulnerability data responses (i.e., Remedy, Description, etc.) are retrieved without raw HTML.
- **Enrich Vulnerability Content**: This retrieves further Vulnerability data, including the request sent by the Invicti scanner and the response received.