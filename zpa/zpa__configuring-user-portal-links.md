# Configuring User Portal Links
Source: https://help.zscaler.com/zpa/configuring-user-portal-links
PDF: https://help.zscaler.com/pdf/com/en/1484336.pdf

Within the ZPA Admin Portal, you can add up to 500 links per user portal. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To add links to a user portal:
- Go to **Resource Management **>** User Portal **>** Portal Links**.
- Click **Add Portal Links**.
The **Add Portal Links** window appears.
- In the **Add Portal Links** window:
- [1. App Type](#ApplicationSegments)
- [2. Link Type](#LinkType)
- [3. Links](#Links)
- [4. Review](#Review)
- []On the **App Type **tab, select **Private Applications **or **Public Applications**.
- **Private Applications**: Links that point to private applications configured in ZPA.
- **Public Applications**: Links that point to public applications that are accessible to users but not configured in ZPA.
- Click **Next**.
[See image.](#AppType)
[]On the **Link Type** tab:
- If you selected **Private Applications** in the previous step:
- **User Portal**: Select the user portal that can display these links. You can select more than one user portal. Click **Select All** or click **Clear Selection** to remove any selections.
- **Application Segments**: Select the application segments you want to associate to the user portals from the drop-down menu. The links you specify are based on the applications included in these segments. You can search for a specific application segment, click **Select All**, or click **Clear Selection** to remove any selections.
- **Applications**: Select the applications that you want to include within the application segments you selected previously. Click **Select All** or click **Clear Selection** to remove any selections. The application segment name and application segment domain both appear in the drop-down menu.
- Click **Next**.
[See image.](#LinkType-Private)
- If you selected **Public Applications** in the previous step:
- **User Portal**: Select the user portal that can display these links. You can select more than one user portal. Click **Select All** or click **Clear Selection** to remove any selections.
- Under **URLs**:
- Select a protocol (i.e., **HTTP**, **HTTPS**) for the link.
- Enter a fully qualified domain name (FQDN) for the application (e.g., `www.example.com`).
- (Optional) Enter a specific path for the URL (e.g., entering `/preferences` creates a link pointing to www.example.com/preferences).
- (Optional) Click **Add More** to add more public URLs.
- Click **Next**.
[See image.](#LinkType-Public)
During configuration, you can only add up to 150 links at a time. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations). To avoid incorrect or inconsistent policy evaluation, a private application should not be used to a create a **Public Applications** link type. Zscaler recommends the following when adding a **Public Applications** link to an application segment:
- Delete the public applications user portal link.
- Enter the application when [configuring an application segment](/zpa/configuring-defined-application-segments).
- Create the private applications user portal link with the application configured in the application segment.
- []On the **Links** tab, a links list for all of the selected applications is displayed. Click **Expand All** to see more information about each link. Configure the following link information, as needed:
- **Name**: The name of the link, as specified in the application segment, is displayed by default. You can change this to any display name you require for the link. For example, the default name could be www.example.com, but could be changed to "My Example Application." This is how the link text appears within the user portal.
- **Display on Portal**: Select **Enabled** to display the link in the user portal. If **Disabled** is selected, the link is not displayed on the user portal.
-
**Protocol**: Select a protocol (i.e., **HTTP**, **HTTPS**) for the link.
If you selected **Private Applications** in step 1:
- For private applications where Browser Access is not enabled, you can specify **HTTP** or **HTTPS**.
- For private applications where Browser Access is enabled, this field defaults to the protocol that was configured in the application segment, and it cannot be changed.
If you selected **Public Applications** in step 1, you must specify **HTTP** or **HTTPS**. By default, this field is populated based on the protocol selection made in step 3.
-
**Domain**: The domain name used in the URL for the link is automatically entered based on the configured application segments you selected in step 2. This field is read only.
- If this is a Browser Access-enabled application, the FQDN as specified in the application segment is displayed by default.
- If this is an application that can only be accessed with Zscaler Client Connector, the IP address or FQDN as specified in the application segment is displayed by default.
Regardless of whether the application is Browser Access-enabled or requires Zscaler Client Connector, the URL string supports HTTP and HTTPS protocols.
- **Path**: (Optional) By default this is set to forward slash (/), but you can edit this field to use a specific path for the URL. For example, an HTTPS link to www.exampleapp1.com would have a URL of https://www.exampleapp1.com/ by default. However, you can change the path to `/preferences` so that the URL points to https://www.exampleapp1.com/preferences.
- **Description**: (Optional) You can enter a description for the link.
- **Logo/Favicon**: (Optional) Click **Select Image** to upload a logo or favicon for the link. You can upload any valid .ico, .jpg, or .png image file type that is 32x32 pixels or smaller.
- Click **Next**.
[See image.](#Links-Img)
If a user is connecting to ZPA via Zscaler Client Connector on at least one device, they see links for applications they can access across all devices. However, an access policy restricts access to an application based on the Zscaler Client Connector Posture Profile criteria.
For example, you could have an access policy rule that allows a user to access the HR Application on their Windows device, but have another rule that allows them to access the Sales Application on their macOS device. In this example, the user sees links for the HR Application and Sales Application on the user portal, but they can only access an application if they are using the proper device. To learn more, see [About Access Policy](/zpa/about-access-policy) and [About Device Posture Profiles](/zscaler-client-connector/about-device-posture-profiles).
[]On the **Review** tab, review your links configuration, then click **Save**.
[See image.](#Review-Img)
[]![Add Portal Links window with App Type tab ](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-apptype.png)
[]![Add Portal Links window with Link Type tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/Add%20Portal%20Links_1.png)
[]![Add Portal Links window with Link Type tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-public-linktype.png)
[]![Add Portal Links window with Links tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-links.png)
[]![Add Portal Links window with Review tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-review.png)