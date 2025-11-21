# Black Duck
Source: https://help.zscaler.com/uvm/black-duck
PDF: https://help.zscaler.com/pdf/com/en/1528221.pdf

![The Black Duck tile](/downloads/uvm/configure/sources/black-duck/mceclip0.png)
Black Duck helps security and development teams identify and mitigate open source-related risks across application portfolios.
Required Parameters
- API Key
- Required Versions: When certain versions are selected, the source retrieves data linked to these versions. When the field is left empty, the source retrieves data from the canonical version for each project.
- Pull Fixes
Retrieving the API Key
- Log in to your Black Duck account using an admin user.
- Go to **Admin** > **User Management**.
- Create or edit the user you want to use for the API source.
- The user should have the **Global Code Scanner** role and be a member of the relevant project.
- In the project, the user should have the **Project Code Scanner** project role.
- Save the user, log out of the Black Duck platform, and then log in to the Black Duck platform using the new or edited user.
- Navigate to the user menu located on the top navigation bar.
- Select **My Access Tokens**.
- Click **Create New Token**.
![The Create Token page in the Black Duck platform](/downloads/uvm/configure/sources/black-duck/mceclip1.png)
- Enter a name. Optionally, enter a description.
- The minimal scope for the API connection is **Read Access Only**.
- The API token is displayed. Save the token because it is not available again.