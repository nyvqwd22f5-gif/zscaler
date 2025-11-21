# Freshservice
Source: https://help.zscaler.com/uvm/freshservice
PDF: https://help.zscaler.com/pdf/com/en/1528286.pdf

![The Freshservice tile](/downloads/uvm/configure/sources/freshservice/9e859160-96cf-4451-99aa-eb588f3d8932.png)
The Freshservice connector retrieves ticket ID, details about the individual or team requesting the service, status of the ticket (i.e., open, closed, in progress), priority, assignee, and any other relevant metadata associated with the service request, such as tags, labels, or custom fields.
Required Parameters
- API Key
- Domain: Your domain is detailed in your URL (e.g. `https://domain.freshservice.com`).
- Start date: The date from which you want to start retrieving data. Enter the date in the `YYYY-MM-DDT00:00:00Z` format.
Retrieving your API Key
- Log in to your Support portal.
- In the top right of the portal, click on your profile picture.
- Go to the **Profile Settings** page.
- Your API key is available below the change password section to your right.
To learn more, refer to the [Freshservice documentation](https://api.freshservice.com/v2/#authentication).