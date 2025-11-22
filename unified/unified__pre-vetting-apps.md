# Pre-Vetting Apps
Source: https://help.zscaler.com/unified/pre-vetting-apps
PDF: https://help.zscaler.com/pdf/com/en/1516061.pdf

Depending on your organization's policy, users might request approval for apps, third-party integrations, and browser extensions before installing them.
In this case, you can search across the 3rd-Party App Governance Catalog and pre-vet if an application should be installed and introduced to your environment. You can also manually add it to your inventory and then [classify](/unified/classifying-apps) the app for future records.
If the app is not yet available in the App Catalog, you can submit the app for sandboxing and be notified when it is ready for your review.
- [Add an App to Your Inventory](#add-app-inventory)
- [Submit an App for Sandboxing](#submit-app-sandbox)
[]To add an app to your inventory:
- In the left-side navigation, go to **Inventory**.
-
Search for an app by name or client ID. To learn more, see [Searching for Apps](/unified/searching-apps).
[See image.](#search-app-name)
-
In the search results, if the app appears in blue, then it is in the App Catalog. Select the app to open the [App Panel](/unified/about-app-panel) and further review it.
[See image.](#add-app-inventory-icon)
-
(Optional) Click **Add to inventory **in the App Panel header. The header also appears in blue if the app is in the App Catalog.
[See image.](#add-app-app-panel-icon)
You can add multiple apps to your inventory at once. To learn more, see [Uploading Apps in Bulk](/unified/uploading-apps-bulk).
[]To submit an app for sandboxing:
- In the left-side navigation, go to **Inventory**.
-
Enter the client ID of the app in the search bar.
[See image.](#search-client-id)
A `No Applications Found` message appears, prompting you to submit the client ID to the 3rd-Party App Governance Sandbox.
[See image.](#app-not-found-submit-sandbox)
-
Click **Submit**.
A summary appears indicating that your app is **Pending**. You receive an email when your app is uploaded.
[See image.](#pending-app)
The same summary appears when you [upload apps in bulk](/unified/uploading-apps-bulk) and 3rd-Party App Governance does not recognize one of the apps. The unrecognized apps are sent for sandboxing automatically and marked as pending.
[]![Screenshot of the search bar in the App Inventory](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/pre-vetting-apps/SearchBar_App_Inventory.png)
[]![Screenshot of the inventory search results](/downloads/zia/apptotal/how/general/apps-pre-vetting/apptotal_inventory_search_results.png)
[]![Screenshot of the Add to inventory button in the App Panel ](/downloads/zia/apptotal/how/general/apps-pre-vetting/apptotal_app_panel_add_app.png)
[]![Screenshot of client ID search in App Inventory](/downloads/zia/apptotal/how/general/apps-pre-vetting/apptotal_inventory_search_clientID.png)
[]![Screenshot of No Applications Found message, prompting user to submit the app for sandboxing in AppTotal.](/downloads/zia/apptotal/how/general/apps-pre-vetting/app_not_found_submit.png)
[]![Screenshot of a pending app in the submit for sandboxing summary](/downloads/zia/apptotal/how/general/apps-pre-vetting/apptotal_sandbox_pending.png)