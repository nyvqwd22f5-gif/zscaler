# About API Key Management
Source: https://help.zscaler.com/zpc/about-api-key-management
PDF: https://help.zscaler.com/pdf/com/en/1455756.pdf

An API key is required in order to access the publicly available set of Zscaler Posture Control (ZPC) APIs. Only the API key is required for authentication prior to accessing the publicly available set of ZPC APIs.
Generating an API key only occurs in the ZPC Admin Portal from the API Keys page. API keys are always accessible from the page and are only displayed when the key is first created. They are not available in the saved configuration.
API keys provide the following benefits and enable you to:
- Authenticate and access the ZPC APIs.
- Generate the API key used to access the ZPC APIs.
About the API Keys Page
On the API Keys page (Administration > Authentication & Authorization > API Keys), you can do the following:
- Export your API key. The API key is needed for making API calls.
- [Create an API key](/zpc/creating-api-keys). You can create a maximum of 100 API keys.
- Search for a specific API key.
- View a list of API keys. For each key, you can see:
- **Name**: The name of the API key.
- **Group**: The assigned group of the API key.
- **Role**: The assigned role of the API key.
- **Creation Date**: The date and time the API key was created.
- **Revocation Date**: The date the API key is revoked. Revoked API keys no longer allow access to authenticate to the ZPC API, but remain in the table.
- **Status**: Indicates whether the key is active, inactive, or revoked.
- [Modify the table and its columns](/zpc/using-tables).
- [Revoke](/zpc/revoking-api-keys) or [delete](/zpc/deleting-api-keys) an API key.
![Viewing the API Keys page in the ZPC Admin Portal](/downloads/zpc/authentication-authorization/api-key-management/about-api-key-management/zpc-annotated-api-keys-page.png?1686264649)