# Configuring User Portal Links
Source: https://help.zscaler.com/unified/configuring-user-portal-links
PDF: https://help.zscaler.com/pdf/com/en/1492426.pdf

Within the Admin Portal, you can add up to 500 links per user portal. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
To add links to a user portal:
- Go to **Policies **>** Access Control **> **Clientless **>** Portal Links**.
- Click **Add Portal Links**.
The **Add Portal Links** window that appears
- In the **Add Portal Links** window:
- [1. App Type](#ApplicationSegments)
- [2. Link Type](#LinkType)
- [3. Links](#Links)
- [4. Review](#Review)
- []In the **App Type **tab, select **Private Applications **or **Public Applications**.
- **Private Applications**: Links that will point to private applications configured under Private Applications in the Admin Portal.
- **Public Applications**: Links that will point to public applications that are accessible to users but not configured under Private Applications in the Admin Portal.
- Click **Next**.
[]In the **Link Type** tab:
- If you selected **Private Applications** in the previous step:
- Select the **User Portal** that can display these links. You can select more than one user portal. Click **Select All** or click **Clear Selection** to remove any selections.
- Select the **Application Segments** you want to associate to the user portals from the drop-down menu. The links you specify are based on the applications included in these segments. You can search for a specific application segment, click **Select All**, or click **Clear Selection** to remove any selections.
- Select the **Applications** you want to include within the application segments you selected previously. Click **Select All** or click **Clear Selection** to remove any selections.
- Click **Next**.
[See image.](#LinkType-Private)
- If you selected **Public Applications** in the previous step:
- Select the **User Portal** that can display these links. You can select more than one user portal. Click **Select All** or click **Clear Selection** to remove any selections.
- Under **URLs**:
- Select a protocol (i.e., **HTTP**, **HTTPS**) for the link
- Enter a fully qualified domain name (FQDN) for the application (e.g., www.example.com).
- (Optional) Enter a specific path for the URL (e.g., entering /preferences would create a link pointing to wwww.example.com/preferences).
Click **Add More** to add more public URLs.
- Click **Next**.
[See image.](#LinkType-Public)
During configuration, you can only add up to 150 links at a time. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
[]In the **Links** tab, a links list for all of the applications selected is displayed. Click **Expand All** to see more information about each link. Configure the following link information, as needed:
- **Name**: The name of the link, as specified in the application segment, is displayed by default. You can change this to any display name you require for the link. For example, the default name could be www.example.com, but could be changed to "My Example Application". This is how the link text will appear within the user portal.
- **Display on Portal**: Enable the link. If **Disabled**, the link will not be displayed on the user portal.
- **Protocol**: Select a protocol (i.e., **HTTP**, **HTTPS**) for the link.
If you selected **Private Applications** in the previous step:
- For private applications where Browser Access is not enabled, you can specify **HTTP** or **HTTPS**.
- For private applications where Browser Access is enabled, this field will default to the protocol that was configured in the application segment, and it cannot be changed.
If you selected **Public Applications** in the previous step, you must specify **HTTP** or **HTTPS**. By default, this field is populated based on the protocol selection made in the previous step.
- **Domain**: The domain name used in the URL for the link is automatically entered based on the configured application segments you selected in the previous step. This field is read only.
- If this is a Browser Access-enabled application, the fully qualified domain name (FQDN) as specified in the application segment is displayed by default.
- If this is an application that can only be accessed by the Zscaler Client Connector, the IP address or FQDN as specified in the application segment is displayed by default.
Regardless of whether the application is Browser Access-enabled or requires Zscaler Client Connector, the URL string supports HTTP and HTTPS protocols.
- **Path**: (Optional) By default this is set to forward slash (/), but you can edit this field to use a specific path for the URL. For example, an HTTPS link to www.exampleapp1.com would have a URL of https://www.exampleapp1.com/ by default. However, you could change the path to /preferences so that the URL points to https://www.exampleapp1.com/preferences.
- **Description**: (Optional) You can enter a description for the link.
- **Logo/Favicon**: (Optional) Click **Select image** to upload a logo/favicon for the link. You can upload any valid .ico, .jpg, or .png image file type that is 32 x 32 pixels or smaller.
Click **Next**.
[See image.](#Links-Img)
If a user is connecting to Private Applications via Zscaler Client Connector on at least one device, then they will see links for applications they can access, across all devices. However, access policy will restrict access to an application based upon the Zscaler Client Connector Posture Profile criteria.
For example, you could have an access policy rule that allows a user to access the "HR Application" on their Window's device, but have another rule that allows them to access the "Sales Application" on their macOS device. In this example, the user will see links for the "HR Application" and "Sales Application" on the user portal, but they will only be able to access an application if they are using the proper device. To learn more, see [About Access Policy](/unified/about-access-policy) and [About Device Posture Profiles](/unified/about-device-posture-profiles).
[]In the **Review** tab, review your links configuration, then click **Save**.
[See image.](#Review-Img)
[]![Add Portal Links window with Link Type tab ](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-private-linktype.png)
[]![Add Portal Links window with Link Type tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-public-linktype.png)
[]![Add Portal Links window with Links tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-links.png)
[]![Add Portal Links window with Review tab](/downloads/zpa/user-portal/configuring-application-links-user-portals/zpa-addportallinks-review.png)