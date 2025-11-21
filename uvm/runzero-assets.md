# runZero Assets
Source: https://help.zscaler.com/uvm/runzero-assets
PDF: https://help.zscaler.com/pdf/com/en/1528191.pdf

![The Run Zero Assets tile](/downloads/uvm/configure/sources/runzero-assets/mceclip0.png)
runZero is a Cyber Asset Attack Surface Management (CAASM) platform designed to provide security teams comprehensive, unified visibility so they can proactively manage risk and exposure. The runZero Assets source retrieves the `Get/export/org/assets.jsonl` call and the Asset schema.
Required Parameters
- Client ID
- Client Secret
- Organization ID
Retrieving the Client ID and Client Secret
To retrieve the client ID and client secret:
- In the runZero platform, from the left-side navigation, open the **Account** tab.
- Go to **API Clients**.
- Click **Register New API Client**.
- After the registration process is complete, copy your client ID and client secret.
Retrieving the Organization ID
A list of all organization IDs for your runZero account can be retrieved via the runZero API.
- Go to the runZero Swagger API documentation.
- Click **Authorize** and enter your client ID and secret in the **oauthDefaults (OAuth2, clientCredentials)** section.
- Click **Authorize** to make the authentication call and receive an API bearer token.
- In the GET /account/orgs API documentation section, click **Try it out**.
- Click **Execute**.
![Selecting Execute in the runZero Swagger API documentation](/downloads/uvm/configure/sources/runzero-assets/mceclip1.png)
- Identify the response and organization ID to use.