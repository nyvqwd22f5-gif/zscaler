# runZero Vulnerabilities
Source: https://help.zscaler.com/uvm/runzero-vulnerabilities
PDF: https://help.zscaler.com/pdf/com/en/1528186.pdf

![The runZero Vulnerabilities tiles](/downloads/uvm/configure/sources/runzero-vulnerabilities/mceclip0.png)
runZero is a Cyber Asset Attack Surface Management (CAASM) platform designed to provide security teams comprehensive, unified visibility so they can proactively manage risk and exposure. The runZero Assets source retrieves the Get/export/org/vulnerabilities.jsonl call.
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
- Go to the runZero Swagger API documentation site.
- Click **Authorize** and enter your client ID and secret in the **oauthDefaults (OAuth2, clientCredentials)** section.
- Click **Authorize** to make the authentication call and receive an API bearer token.
- In the GET /account/orgs API documentation section, click **Try it out**.
- Click **Execute**.
- Identify the response and organization ID to use.