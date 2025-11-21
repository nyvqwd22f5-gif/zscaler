# Legit
Source: https://help.zscaler.com/uvm/legit
PDF: https://help.zscaler.com/pdf/com/en/1528361.pdf

![The Legit and Legit Incidents tiles](/downloads/uvm/configure/sources/legit/mceclip0.png)
Legit Security protects your software supply chain and oversees application security from code to cloud. It enables secure software releases through automatic detection and resolution of security concerns.
The SecOps platform has two Legit connectors:
- Legit: Retrieves all data apart from incidents.
- Incidents: Retrieves only incident data.
If your Legit account is connected to Snyk, inform your SecOps platform representative. If you are also retrieving data directly from Snyk in the SecOps platform, the Legit source can be adjusted so it  does not retrieve duplicate data.
Required Parameters
- Auth Token
- Tenant Id
- Sources: Select if to pull all sources or specific ones.
Generating an Auth Token
To generate an auth token:
- In the Legit console, go to **Settings** > **API**.
- Select **Read** > **Generate Token**.
- Copy the auth token and save it for your records.