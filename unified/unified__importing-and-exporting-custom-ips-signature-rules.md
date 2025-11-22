# Importing and Exporting Custom IPS Signature Rules
Source: https://help.zscaler.com/unified/importing-and-exporting-custom-ips-signature-rules
PDF: https://help.zscaler.com/pdf/com/en/1494326.pdf

You can import or export custom IPS signature rules using a CSV file. The import action allows you to add, modify, and delete custom IPS signature rules.
- [Import custom IPS signature rules from a CSV file.](#import)
- [Export your custom IPS signature rules to a CSV file.](#export)
[]When importing custom IPS signature rules using CSV files, you must enclose comma-separated values for individual fields within three single quotes (`'''`) instead of double quotes (`"`) to prevent parsing errors that might occur with certain Perl Compatible Regular Expressions (PCRE) rule options.
[See example rule.](#example-rule)
To import custom IPS signature rules:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Custom IPS Signatures**.
- Click the **Custom Signature Rules** tab.
-
Click** Import from CSV**.
The **Import from CSV** window appears.
-
In the** Import from CSV** window, click **Choose file**, go to the CSV file with your custom IPS signature rules, and click **Open**.
Make sure that the CSV file you are importing uses the same format as the** Sample Import CSV file** provided on the **Custom Signature Rules** page.
- Click **Import**.
- After the CSV file is successfully imported, click **Close**.
A CSV file allows you to import up to 500 custom IPS signature rules, which is also the maximum number of custom IPS signature rules allowed for an organization.
- []Go to **Policies **>** Cybersecurity **>** Inline Security **>** Custom IPS Signatures**.
- Click the **Custom Signature Rules** tab.
- Click **Export to CSV**. Your custom IPS signature rule information is exported to a CSV file.
This CSV file cannot be used to import custom IPS signature rules because the import requires a CSV file in a different format. To import custom IPS signature rules, use the same format as the **Sample Import CSV file** provided by Zscaler.
[]
`'''+''','''Rule_1''','''alert tcp any any -> any 8080 ( msg:"http_header found"; content:"|2f|wp|2d|admin|2f|"; flow:established,to_server; http_uri; pcre:"/\w{0,6}/Ri"; sid:6; )''','''ADVANCED_SECURITY''','''''','''Enable'''`