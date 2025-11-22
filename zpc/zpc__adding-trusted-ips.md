# Adding Trusted IPs
Source: https://help.zscaler.com/zpc/adding-trusted-ips
PDF: https://help.zscaler.com/pdf/com/en/1466861.pdf

You can add a list of IP addresses to the ZPC Admin Portal for secure communication in your cloud infrastructure. These IP addresses are trusted and secure for the selected cloud resources within your cloud infrastructure.
The trusted IP changes take up to 12 to 16 hours to reflect across the ZPC modules.
To add trusted IP addresses:
- Go to **Administration** > **Trusted IP List**.
- On the **Trusted IP Management** page, click **+ Trusted IP List**.
[See image.](#add-trusted-ip)
- Under **Trusted IP List**:
- Click **Template** to download the IP address template and enter the list of trusted IP addresses in the .csv or .xlsx file.
- Drag and drop the trusted IP file or browse and upload the trusted IP file.
- For **Trusted IP List Name**, enter a name for the trusted IP list.
- Select the cloud resource to which you want to apply the trusted IP list and click **Next**.
- **Business Units**: Select the [business units](/zpc/about-business-units) from the list.
- **Cloud Accounts**: Select the cloud service providers or individual [cloud accounts](/zpc/about-cloud-accounts) from the list.
- **All Cloud Accounts**: Select to apply the trusted IP list to all the existing and new cloud accounts.
[See image.](#step1)
- On the **Business Units Scope** page or **Accounts Scope** page, select the business units or cloud accounts to associate with the trusted IP list, then click **Next**.
- On the **Trusted IP Scope in ZPC **page, select **Alerts** to [ignore all alerts](/zpc/about-alerts) on external exposure of your cloud resources associated with the trusted IP list.
[See image.](#scope)
- Click **Next**.
- Review the summary of the trusted IP list. Click **Back** to change any value.
[See image.](#summary)
- Click **Finish**.
[![Add Trusted IP List](/downloads/zpc/administration/adding-trusted-ips/zpc-add-trusted-ip.png)
]
[![Add the Trusted IP List](/downloads/zpc/administration/adding-trusted-ips/zpc-add-trusted-ip-list-1.png)
]
[![Select the Scope for Trusted IP](/downloads/zpc/administration/adding-trusted-ips/zpc-trusted-ip-scope.png)
]
[![View the Summary](/downloads/zpc/administration/adding-trusted-ips/zpc-trusted-ip-summary.png)
]