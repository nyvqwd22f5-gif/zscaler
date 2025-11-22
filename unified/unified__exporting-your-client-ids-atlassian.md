# Exporting Your Client IDs from Atlassian
Source: https://help.zscaler.com/unified/exporting-your-client-ids-atlassian
PDF: https://help.zscaler.com/pdf/com/en/1515296.pdf

Atlassian doesn't have a straightforward way of exporting a list of client IDs of all the apps connected to your environment.
The Zscaler team prepares a dedicated script that is shared with clients to help them extract the client IDs. Reach out to your Zscaler representative to get the script.
You must generate an [API token](https://id.atlassian.com/manage-profile/security/api-tokens) and read the instructions in the header before running the script.
# This script will extract app IDs for Atlassian JWT apps and OAuth apps, and export to a CSV file "atlassian_app_ids.csv"
# Please insert the following values before running the script:
# 	create an API token here https://id.atlassian.com/manage-profile/security/api-tokens
#	domain = "PUT_YOUR_ATLASSIAN_DOMAIN_HERE"
#	username = "ADMIN@DOMAIN.COM"
The output must include app IDs in a CSV file.
You can [upload](/unified/uploading-apps-bulk) the apps to the Inventory** **in 3rd-Party App Governance** **using the app IDs.