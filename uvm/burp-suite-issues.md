# Burp Suite Issues
Source: https://help.zscaler.com/uvm/burp-suite-issues
PDF: https://help.zscaler.com/pdf/com/en/1527731.pdf

![af622989-9e59-42f1-9057-22ae598542cd.png](/downloads/uvm/configure/sources/burp-suite-issues/af622989-9e59-42f1-9057-22ae598542cd.png)
Burp Suite is a web application security testing toolkit for proxying, scanning, and intrusion testing.
Burp Suite Issues retrieves Burp Suite Sites, Scans and Issues data.
Required Parameters
In the source **authentication** **setup**, you will need the following parameters when creating a Burp Suite authentication -
- [API Key](#h_01JH07F2AHN8CFBDD75HJD31HC)
- [URL](#h_01JH07F2AHWVZAKEZB0285043G)
In the **source setup page**, select your configured Burp Suite authentication.
Roles and Permissions
To generate a Burp Suite API key, you need to **create** an ***API user*** in Burp Suite*** Enterprise Edition***.
- To create a Burp Suite API user, you need to be a **Burp Suite Enterprise Edition administrator**.
The **API user** created for this connector must carry the following permissions:
- `Scan viewer` Role: The API user must be a member of the `Scan viewer` group or a group that uses the `Scan viewer` role.
- The API user must be assigned an additional role (custom role or the `Sites maintainer` role) that includes the following permissions.
-
- `View sites`
- `View site details`
-
Retrieving the Parameters
Retrieving API Key
To use Burp Suite API, you first need to create an API user in Burp Suite Enterprise Edition. This generates an API key that you can use to authenticate requests that you send to the API.
To create an API user,
- Log in to Burp Suite Enterprise Edition as an **administrator**.
- Click **Team** > **Add a new user**
- Enter an informative name and username that will help you identify the user later. For example, Zscaler API User.
- Enter an email address, such as the email address of the admin user.
- From the **Choose a login type** menu, select **API key**
- Assign the user to groups and roles as outlined in the [Roles and Permissions](#01JH07FZDHTWGQEDQ8ZZBGCQV4) section above.
Ensure that the assigned groups have the necessary permissions for the user to make the API calls.
- Click **Save**
- When prompted, click **Copy API key** and securely **save** the key
**IMPORTANT:** you will not have access to this key again. If you lose it, you will have to generate a new key.
Retrieving URL
The Burp Suite API URL is generated along with the API Key when creating the API user. The expected format is `https://<server_IP>:<port>`. For example, `https://20.65.782.40:8334/`
Note: If you use the **Copy API link button**, please remove the url path after the port number.