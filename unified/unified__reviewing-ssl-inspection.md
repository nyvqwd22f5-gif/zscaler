# Reviewing SSL Inspection Policies
Source: https://help.zscaler.com/unified/reviewing-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1488021.pdf

SSL inspection policies allow you to inspect traffic sent using the secure HTTPS protocol to ensure that it is, in fact, encrypted and fully secure and is not exploited to deliver security threats. Zscaler inspects SSL traffic by establishing a separate SSL tunnel between the user's browser and the destination server.
To review SSL inspection policies:
- Under** Exempted Categories**, review the categories that Zscaler exempts from SSL inspection. These categories (Healthcare and Finance) are not inspected because they may contain a user's personally identifiable information (PII).
- By default, Zscaler inspects SSL traffic from Microsoft's web-based applications such as OneDrive. If you want to use Microsoft's recommended setting, which exempts that traffic from SSL inspection, click **Advanced SSL Settings**, select **M365 Exempted**, and click **Save**.
- Under **All Users, All Other Destinations**, note that categories that are not exempted above will have their SSL traffic inspected.
- Under **SSL Root Certificate**, the Zscaler's intermediate root certificate is installed. You can select your own certificate later in the Admin Portal.
- When you are done reviewing the SSL inspection policies, click **Next **to move on to review the [cyber threat protection policies](/unified/configuring-cyber-threat-protection).
Zscaler installs its recommended SSL inspection policies by default. You can fine-tune these policies later in the Admin Portal. To learn more, see [Configuring SSL Inspection Policy](/unified/configuring-ssl-inspection-policy).