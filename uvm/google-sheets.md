# Google Sheets
Source: https://help.zscaler.com/uvm/google-sheets
PDF: https://help.zscaler.com/pdf/com/en/1527656.pdf

![The Google Sheets tile](/downloads/uvm/configure/sources/google-sheets/86c944d4-b10e-483c-baa5-c202ddbe862b.png)
The Google Sheets connector allows you to upload files from your Google Sheets to the platform.
Required Parameters
The source Authentication configuration requires the following parameters:
- [Client ID and Client Secret](#param1)
- [Refresh Token](#param2)
In the source setup Retrieval section, set the following:
- [Spreadsheet ID](#h_01JNZQ8PCPM2PQQ40D2V7VYJTF): Enter the spreadsheet ID located in the spreadsheet URL.
- Sheets (optional): Filter the specific sheet within the spreadsheet that you want to ingest.
Prerequisites
To allow the platform to access your Google Sheets via API, ensure that your Google Sheets API is enabled. To learn more, refer to the [Google Cloud documentation](https://support.google.com/googleapi/answer/6158841?hl=en).
To enable the API for your project:
- Log in to the GCP console.
- From the left-side navigation, click **APIs & Services** > **Library**.
![14b54bfe-44fa-4586-84e7-8ec8df846006.png](/downloads/uvm/configure/sources/google-sheets/14b54bfe-44fa-4586-84e7-8ec8df846006.png)
- In the **Google Workspace** section, select the **Google Sheets API** tile.
![21c4baa4-2930-4346-b875-073d85c040cb.png](/downloads/uvm/configure/sources/google-sheets/21c4baa4-2930-4346-b875-073d85c040cb.png)
- Click **Enable**.
[]
To generate a Client ID and Client Secret:
- Log in to the GCP console.
- From the left-side navigation, click **APIs & Services** > **Credentials**.
**![47dc51bb-332b-441f-bebb-382840a81306.png](/downloads/uvm/configure/sources/google-sheets/47dc51bb-332b-441f-bebb-382840a81306.png)
**
- Click** Create credentials** > **OAuth client ID**.
**![4e52eb57-2766-45dc-bb07-f16811d25a7f.png](/downloads/uvm/configure/sources/google-sheets/4e52eb57-2766-45dc-bb07-f16811d25a7f.png)
**
- In the **Create OAuth client ID** window, configure the following:
- **Application type**: Select **Web application**.
- **Name**: Enter a name for the authentication credentials.
- In the **Authorized Redirect URIs** section, in the **URIs I** field, enter `https://developers.google.com/oauthplayground`.
![233c4db3-3038-4505-bcea-95fe6be7007f.png](/downloads/uvm/configure/sources/google-sheets/233c4db3-3038-4505-bcea-95fe6be7007f.png)
- Click **Create**.
- Copy the **Client ID **and** Client secret**.
**![146bc6fa-717b-412a-af93-b58d091ba069.png](/downloads/uvm/configure/sources/google-sheets/146bc6fa-717b-412a-af93-b58d091ba069.png)
**
[]
To retrieve the refresh token:
- Go to the [OAuth 2.0 Playground](https://developers.google.com/oauthplayground/).
- From the top right, select** OAuth 2.0 Configuration**.
![6491ebe9-4957-41a5-a0d9-789c24b3d8f5.png](/downloads/uvm/configure/sources/google-sheets/6491ebe9-4957-41a5-a0d9-789c24b3d8f5.png)
- Select the **Use your own OAuth credentials **checkbox.
- Enter the obtained **Client ID** and **Client Secret** values.
- Click **Close**.
**![266b5665-e7d1-4dc8-95e3-83a9ddf7cd06.png](/downloads/uvm/configure/sources/google-sheets/266b5665-e7d1-4dc8-95e3-83a9ddf7cd06.png)
**
- From the left-side navigation, in the **Step 1 **section, select **Google Sheets API v4**.
- Select** **all the scopes.
![2e53651e-a8c7-4ddd-885a-b0526dd39b10.png](/downloads/uvm/configure/sources/google-sheets/2e53651e-a8c7-4ddd-885a-b0526dd39b10.png)
- Click **Authorize APIs**.
**![c3e7cf9a-ca3c-4dd9-860f-59b47071b041.png](/downloads/uvm/configure/sources/google-sheets/c3e7cf9a-ca3c-4dd9-860f-59b47071b041.png)
**
- When prompted, select your Gmail account** **and click **Allow**.
**![8524d73d-7769-4ebd-8479-bd4d20daa9e2.png](/downloads/uvm/configure/sources/google-sheets/8524d73d-7769-4ebd-8479-bd4d20daa9e2.png)
**
- In the **Step 2 **section, click **Exchange authorization code for tokens** to generate and display the **Access Token** and **Refresh Token**.
**![bc315222-f0b2-4e17-873f-5cd224154fa2.png](/downloads/uvm/configure/sources/google-sheets/bc315222-f0b2-4e17-873f-5cd224154fa2.png)
**
- Copy and save the** Refresh Token**.
**![c6be58b8-2718-4371-bd58-37f90f624b62.png](/downloads/uvm/configure/sources/google-sheets/c6be58b8-2718-4371-bd58-37f90f624b62.png)
**
Spreadsheet ID
The spreadsheet ID can be found in the URL of the Google Sheets spreadsheet you want to ingest, between `d/` and `/edit`.
For example, if the URL is `https://docs.google.com/spreadsheets/d/9J31VsFnlj_9hSfWHAJKCBN5aF3J0lVh9opFewIUaKJd/edit`, the spreadsheet ID is `9J31VsFnlj_9hSfWHAJKCBN5aF3J0lVh9opFewIUaKJd`.
![d140e3ea-6092-475e-a50e-92b8b41c193b.png](/downloads/uvm/configure/sources/google-sheets/d140e3ea-6092-475e-a50e-92b8b41c193b.png)