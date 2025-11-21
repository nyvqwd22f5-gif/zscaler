# Allowing Traffic to the ID Federation URL by Bypassing Zscaler Client Connector
Source: https://help.zscaler.com/unified/allowing-traffic-id-federation-url-bypassing-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1495676.pdf

To allow users to bypass Zscaler Client Connector when they browse to your organization’s identity federation URL for authentication, add a custom PAC file to their [app profile](/unified/configuring-zscaler-client-connector-app-profiles):
- In the Admin Portal, go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **macOS** or **Windows**, and click **Add macOS Policy **or** Add Windows Policy** to add a new policy or click the **Edit** icon beside an existing policy.
-
Under **Custom PAC URL**, enter the URL for the custom PAC file.
To learn more about creating a custom PAC file, see [Writing a PAC File](/unified/writing-pac-file). To learn how use a PAC file with Zscaler Client Connector, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
- Click **Save**.
![Custom PAC URL](/downloads/unified/networking/client-connector/deployment/interoperability/allowing-traffic-id-federation-url-bypassing-zscaler-client-connector/client-connector-custom-pac-url.png)