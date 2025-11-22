# Adding an HTTP Header Insertion Profile
Source: https://help.zscaler.com/unified/adding-http-header-insertion-profile
PDF: https://help.zscaler.com/pdf/com/en/1529753.pdf

The [HTTP header insertion profile](/unified/about-http-header-insertion-profile) allows you to add custom HTTP request headers and modify existing HTTP request headers. It consists of two parts: adding HTTP header insertion profiles and associating them to a URL Filtering policy rule.
To add an HTTP header insertion profile:
- Go to **Policies **>** Access Control **>** Internet & SaaS **>** HTTP Header Control **> **HTTP Header Insertion Profile**.
-
On the **HTTP Header Insertion Profile** tab, click **Add HTTP Header Insertion Profile**.
The **Add HTTP Header Insertion Profile **window appears.
-
In the **Add HTTP Header Insertion Profile **window:
- **Name**: Enter the name of the HTTP header insertion profile. This is displayed when configuring the URL Filtering policy rules.
-
**HTTP Header**: Enter the key for the HTTP header. It has a limit of 128 characters.
Ensure to enter only request headers.
- [A list of HTTP header keys that are not allowed.](#header-keys-not-allowed)
-
**Value**: Enter the value for the HTTP header. It has a limit of 1,024 characters.
You can add up to 16 HTTP Headers by clicking the **Add Header** button.
- **Description**: (Optional) Enter any additional comments or information. The description cannot exceed 10,240 characters.
[See image.](#add-header-insertion-profile)
- Click **Save **and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []content-security-policy
- etag
- expires
- last-modified
- location
- proxy-authenticate
- public-key-pins
- retry-after
- server
- set-cookie
- strict-transport-security
- timing-allow-origin
- vary
- www-authenticate
- x-content-type-options
- x-frame-options
[]![The ZIA Add HTTP Header Insertion Profile window with header criteria](/downloads/zia/policies/http-header-control/adding-http-header-insertion-profile/ZIA-Add-HTTP-Header-Insertion-Profile-Page.png)