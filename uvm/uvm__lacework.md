# Lacework
Source: https://help.zscaler.com/uvm/lacework
PDF: https://help.zscaler.com/pdf/com/en/1528256.pdf

![The Lacework tile](/downloads/uvm/configure/sources/lacework/mceclip0.png)
Lacework is a cloud security tool that detects threats, vulnerabilities, misconfigurations, and unusual activity in your cloud environments. Lacework learns how your environment is supposed to run and tells you when it deviates.
Required Parameters
- Account
- API Key
- API Secret
- Number of days to fetch: The number of days you want to retrieve in each run. The number should be between one and seven.
Retrieving the API Key and Secret
Generating an API key and secret can be done either by a user with an admin role or a user with write permission for API keys. You can also set up a service user specific for the SecOps platform source setup.
Setting up a Service Account
To create a service user, you need to have organization administrative privileges. To set up a service account:
- Log into the Lacework console.
- Go to **Settings** > **Access control** > **Users**.
- Click **Add New**.
- In the user type section, select **Service User**.
- Name the user and optionally add a description.
- Click **Next** then **Next** again.
- In the user group section, click **Account Admin**.
- Click **Save**.
Creating an API Key
To create an API key:
- Log into the Lacework console.
- Go to **Settings** > **API Keys**.
- For a human user, select the **User API Keys** tab. For a service user, select **Service user API Keys**.
- Click **Add New**.
- Enter a name and optionally add a description.
- For service users, toggle on the **Assign this to a service user** and select the service user from the list.
- Click **Save**.
- After the API key is created, click on the three dots and download the JSON file.
- Open the JSON file and copy the values.
- Paste the **KeyId**, **secret**, and **account name **values in a secure location.