# Defining a Browser Access Application within an Existing Application Segment
Source: https://help.zscaler.com/unified/defining-browser-access-application-within-existing-application-segment
PDF: https://help.zscaler.com/pdf/com/en/1492326.pdf

You can define applications for Browser Access when [configuring a new application segment](/unified/configuring-defined-application-segments). However, you can also modify existing application segments to enable Browser Access for an application. To learn more, see [About Browser Access](/unified/about-browser-access).
If you intend to use a different external and internal hostname for a defined application that is browser access enabled within an application segment, the following applies:
- Internal hostnames are not exposed so there is no record of internal hostnames on the public DNS.
- Backend SSL cannot be verified, so a web server certificate error would be displayed to your end users because the hostname of the application doesn't match the hostname of the certificate.
If you intend to use the same external and internal hostname for a defined application that is browser access enabled within an application segment, then the following applies:
- Internal hostnames are exposed on the public DNS.
- Backend SSL can be verified, so your end users will not receive a web server certificate error.
To define applications for Browser Access within an existing application segment:
- Go to **Policies** > **Access Control** > **Private Applications** > **App Segments**.
- Locate the application segment you want to modify in the table, then click the **Edit** icon.
The **Edit Application Segment** window appears.
- In the **Edit Application Segment** window, on the **Define Applications** tab:
- For **Applications**:
- Enter the fully qualified domain name (FQDN) associated with the application.
- Select the **Browser Access** checkbox, then complete the following steps:
- Select a Browser Access (i.e., web server) certificate from the drop-down menu. You can click **Clear All** to remove any selections. To learn more, see [About (Web Server) Certificates](/unified/about-web-server-certificates).
- From the drop-down menu, select the protocol you want to use when a request is made to access the application. If your web server supports **HTTPS**, select this protocol from the drop-down menu. Otherwise, select **HTTP**. You can click **Clear All** to remove any selections.
Via headers are inserted in HTTP requests made using Browser Access.
- Enter the port number. By default, port **80** is entered for **HTTP** and **443** is entered for **HTTPS**.
- If you selected **HTTPS** in step ii above, **Use Untrusted Certificates** is selected by default. If this setting is not selected, requests to access the application using untrusted web server certificates will not succeed.
- (*Optional*) Select **Allow Unauthenticated OPTIONS Request** to forward an unauthenticated HTTP preflight OPTIONS request from the browser to the application.
Only accepts valid OPTIONS requests that include the headers Access-Control-Request-Headers, Access-Control-Request-Method, and Origin in the HTTP request are accepted. If these are not present, then the OPTIONS request to the application is not forwarded.
CORS requests are accepted if the requests are issued by one valid Browser Access domain to another Browser Access domain. The application server requires `with credentials mode` be added to the javascript. This is to allow the browser to pass cookies to the front end javascript. The application server must also allow requests where the Origin header is set to null or to a valid Browser Access application.
[See image.](#BrowserAccess)
- Click **Add More** to add more domains for each application you want to define.
- For **Zscaler Client Connector Access**, enter the **TCP Port Ranges** that can be used to access the application. The port range must include the port specified previously. Also, you must use TCP port ranges.
For example, if you want to specify the port range 80–90, for **From...** enter 80, and for **To...**, enter 90. If you only want to specify one port, you can enter the same number (e.g., 80) for **From...** and **To...**. Click **Add More** to add more TCP port ranges.
Zscaler recommends excluding DNS traffic (port 53) from TCP and UDP port ranges.
[See image.](#ExampleBAApp)
You can't enable **Double Encryption** for applications where Browser Access is enabled.
- Make sure that the rest of the configuration is correct, then click **Save**. To learn more, see [Configuring Application Segments](/unified/configuring-defined-application-segments).
After saving, you are returned to the **Application Segments** page.
- Copy the Canonical Name (CNAME).
- Go to **Policies** > **Clientless** > [**Browser Access**](/unified/about-browser-access#BAPage).
- Expand to view the application within the table.
- Click the **Copy** icon next to the **Canonical Name (CNAME)**. You will need this CNAME record for your public DNS.
- Add the CNAME information you just copied to your public DNS and verify that the FQDN for the Browser Access enabled application resolves to the record.
To properly resolve Browser Access enabled applications, the App Connector must use an internal DNS. If an internal DNS is not used, it will result in a DNS loop.
For example, for a CNAME of:
marketing.mockcompany.com. CNAME 3077.217246660302995456.h.d.zpa-app.net.
You would need to verify that marketing.mockcompany.com. resolves to 3077.217246660302995456.h.d.zpa-app.net..
[]![Edit Application Segment window with Browser Access checkbox within ZPA Admin Portal](/downloads/zpa/browser-access/defining-browser-access-application-within-existing-application-segment/zpa-addapplicationsegment-browseraccess.png)
[]![Edit Application Segment window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/browser-access/defining-browser-access-application-within-existing-application-segment/zpa-editapplicationsegment-addingbaapps_0.png)