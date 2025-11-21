# Allowing Traffic to the ID Federation URL by Bypassing Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/allowing-traffic-id-federation-url-bypassing-zscaler-app
PDF: https://help.zscaler.com/pdf/com/en/1285516.pdf

To allow users to bypass Zscaler Client Connector  when they browse to your organization’s identity federation URL for authentication, add a custom PAC file to their [app profile](/zscaler-client-connector/about-zscaler-app-profiles):
- In the Zscaler Client Connector Portal, go to **App Profiles**.
- From the menu on the left, go to **macOS** or **Windows**.
- If you're adding a new policy click **Add macOS Policy **or** Add Windows Policy**. If you’re editing an existing policy, locate the relevant policy and click the **Edit** icon.
- Under **Custom PAC URL**, enter the URL for the custom PAC file.
To learn more about creating a custom PAC file, see [Writing a PAC File](/zia/writing-pac-file). To learn how use a PAC file with Zscaler Client Connector, see [Best Practices for Using PAC Files with Zscaler Client Connector](/zscaler-client-connector/best-practices-using-pac-files-zscaler-app).
- Click **Save**.
![The Custom PAC URL option for the Zscaler Client Connector Profile policy](/downloads/z-app/interoperability/how-do-i-let-traffic-id-federation-url-bypass-zscaler-app/Zscaler-App-Profile-Custom-PAC-URL.png)