# CyCognito Connectors
Source: https://help.zscaler.com/uvm/cycognito-connectors
PDF: https://help.zscaler.com/pdf/com/en/1527666.pdf

**Note:** This connector and its documentation are still in development, and may exhibit some limitations or inconsistencies until fully released.
![97fecdea-57cb-4dd6-b8f3-858ad2ef66ef.png](/downloads/uvm/configure/sources/cycognito-connectors/97fecdea-57cb-4dd6-b8f3-858ad2ef66ef.png)
CyCognito is an exposure management platform that reduces risk by discovering, testing and prioritizing security issues.
There are 2 available **CyCognito **connectors:
- **CyCognito - Issues **retrieves a detailed and actionable overview of security issues across your enterprise's digital assets.
- **CyCognito - Assets **retrieves a comprehensive view of your enterprise's digital assets.
Required Parameters
The source **Authentication** configuration requires the following parameters:
- [**API Key**](#h_01JNB04VXHH9M1F0VRDZA8DGNH)
- [**URL**](#h_01JNB0645JV76K0ZWHC14KR5X4) - the base URL of your CyCognito instance
In the source setup **Retrieval** section, set the following:
- **Asset Types dropdown** (applicable in CyCognito Assets) - select the specific asset types to include in the scope of your data retrieval.
Retrieving the Parameters
Retrieving the API Key
You must be an **Admin** or an** IT User** to have access to generating an API key.
To generate an API key,
- In the CyCognito Platform, navigate to **Workflow & Integration **> **API Key Management**
**![32bf54b4-d1aa-4140-b5d7-8c1b315921f2.png](/downloads/uvm/configure/sources/cycognito-connectors/32bf54b4-d1aa-4140-b5d7-8c1b315921f2.png)
**
- Click the **+ button** to add an API key
![1e1560f5-df84-400d-9eb9-3c7794ed32ea.png](/downloads/uvm/configure/sources/cycognito-connectors/1e1560f5-df84-400d-9eb9-3c7794ed32ea.png)
- Enter a key **name**
- Assign the Key **Read only **access
- Optionally set an expiration date for the API key. If you do so, please make sure to refresh this key once it expires.
- Click **Create**
**![3c6a16c8-51b6-4cb0-b338-5bf4b8732d77.png](/downloads/uvm/configure/sources/cycognito-connectors/3c6a16c8-51b6-4cb0-b338-5bf4b8732d77.png)
**
- **Copy** the generated API key and save it securely
**IMPORTANT**: The API key will only be displayed once, and you will not be able to access it again later.
URL
In the URL field, enter your CyCognito** Base URL** **prefixed with api**.
Examples include:
- `https://api.cycognito.com`
- `https://api.platform.cycognito.com`
- `https://api.us-platform.cycognito.com`