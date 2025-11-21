# Exporting Your Client IDs from Microsoft Azure
Source: https://help.zscaler.com/zia/exporting-your-client-ids-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1450376.pdf

You can export a list of client IDs of all the apps connected to your Microsoft Azure environment and [upload](/zia/uploading-apps-bulk) the apps to the Inventory in Zscaler 3rd-Party App Governance** **using the client IDs.
To export the client IDs from Microsoft Azure:
- Sign in to the [Azure Portal](https://portal.azure.com/#home).
You must have Administrator user credentials to access this page.
- Set your portal session to the Azure AD tenant that you want.
- Under **Azure Services**, click **Azure Active Directory**.
[See image.](#Azure-Services)
- In the left-side navigation, click **App registrations**.
[See image.](#App-Registrations)
- On the App Registrations page, choose the **All applications** tab.
A list of all your apps and corresponding client IDs appears.
- Click **Download** to download a CSV file.
After the CSV file is downloaded, the app names appear in the first column and the client IDs appear under App ID in the second column.
[]![Screenshot of Azure Services](/downloads/zia/apptotal/getting-started/find-your-applications-ids/exporting-your-client-ids-microsoft-azure/Azure_Directory.png)
![Screenshot of App Registrations](/downloads/zia/apptotal/getting-started/find-your-applications-ids/exporting-your-client-ids-microsoft-azure/App_Registrations.png?1688728206)
[]