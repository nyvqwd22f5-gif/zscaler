# Flexera Assets
Source: https://help.zscaler.com/uvm/flexera-assets
PDF: https://help.zscaler.com/pdf/com/en/1528196.pdf

![The Flexera Assets tile](/downloads/uvm/configure/sources/flexera-assets/mceclip4.png)
Flexera allows enterprises to gain visibility and control of IT assets, which reduces ongoing software costs and maintains continuous license compliance.
Required Parameters
- Refresh Token
- Zone
- Organization ID
Generating a Refresh Token
To learn more, refer to the [Flexera documentation](https://docs.flexera.com/flexera/EN/FlexeraAPI/GenerateRefreshToken.htm).
- Log in to one of the following URLs based on the server location of your account:
- **North American**: Log in to `app.flexera.com`.
- **Europe (EU)**: Log in to `app.flexera.eu`.
- **APAC**: Log in to `app.flexera.au`.
- From the top right of the page, click the profile icon.
- Select **User Settings**.
![Selecting User Settings in the Flexera platform](/downloads/uvm/configure/sources/flexera-assets/mceclip0.png)
- From the left-side navigation, click **API Credentials** > **Create API Refresh Token**.
![Selecting API Credentials > Create API Refresh Token in the Flexera platform](/downloads/uvm/configure/sources/flexera-assets/mceclip1.png)
-
Click **Copy** to copy the refresh token.
Save the refresh token to a secure location because it is not displayed again after closing the window.
![Copying the refresh token on the New API Refresh Token page of the Flexera platform](/downloads/uvm/configure/sources/flexera-assets/mceclip2.png)
Zone and Organization ID
In the** **SecOps platform, choose one of the three available zones (i.e., US, EU, or APAC) from the drop-down menu according to the zone in which your user and tenant are provisioned. To learn more, refer to the [Flexera documentation](https://developer.flexera.com/#organization-ids).
Each Flexera organization is assigned a unique organization ID:
- Log in to the Flexera platform based on the server location of your account.
- Identify your organization ID by inspecting the URL. An organization in the NAM zone has the format `https://app.flexera.com/orgs/``<orgID>``/` where **<orgID>** is the unique identifier for the organization. The following organization ID is 30408.
**![The organization ID found in the URL of the Flexera platform](/downloads/uvm/configure/sources/flexera-assets/mceclip3.png)
**