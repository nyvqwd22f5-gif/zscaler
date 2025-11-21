# Using Default PAC Files to Forward Traffic to ZIA
Source: https://help.zscaler.com/zia/using-default-pac-files-forward-traffic-zia
PDF: https://help.zscaler.com/pdf/com/en/1399461.pdf

The Zscaler service hosts four non-editable default PAC files, recommended.pac, proxy.pac, mobile_proxy.pac, and kerberos.pac, which are all configured to automatically forward all browser traffic to the nearest ZIA Public Service Edge.
The service recommends that you deploy the **recommended.pac** file to your organization's devices. If necessary, your organization can use more than one PAC file. For example, you can use one PAC file for mobile devices and another for all other devices. Use the [Kerberos PAC file](/zia/how-do-i-use-zscaler-kerberos-default-pac-file) if you are deploying [Kerberos authentication](/zia/about-kerberos-authentication). You can also use a [custom PAC file](/zia/how-do-i-use-custom-pac-file-forward-traffic-zia) to forward web traffic to the Zscaler service.
![Screenshot of all the Zscaler's default PAC files](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/using-default-pac-files-forward-traffic-zia/zia-using-default-pac-files-all-defaultpac.png)
To use the default PAC file that is hosted by the Zscaler service:
- Go to **Administration **>** Hosted PAC Files**.
- Copy the **Hosted URL** of the default PAC file.
[See image.](#seeimage2)
- [Distribute the PAC file URL to your users.](/zia/how-do-i-distribute-pac-file-url-my-users)
[]![Screenshot of the Hosted URL of the Recommended PAC file](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/using-default-pac-files-forward-traffic-zia/zia-using-default-pac-files-recommended-pac.png)