# Bitsight Findings
Source: https://help.zscaler.com/uvm/bitsight-findings
PDF: https://help.zscaler.com/pdf/com/en/1528161.pdf

![mceclip0.png](/downloads/uvm/configure/sources/bitsight-findings/mceclip0.png)
Bitsight helps organizations quantify their cyber risk, measure the impact of their security efforts, and benchmark their performance against peers. The Bitsight Findings source retrieves findings data. Findings are an enriched version of observations. They contain additional information, such as remediation details, and can sometimes even aggregate data from several observations.
Required Parameters
- API Token
- Grades: To learn more, refer to the [Bitsight documentation](https://help.bitsighttech.com/hc/en-us/articles/1500004356421-API-Fields-Finding-Grades).
Generating an API Key
The API token should be generated using a user with Reader permissions. To generate an API key:
- Log in to the Bisight platform.
- Go to **Settings** > **Account** > **API Token**.
- Click **Generate New Token**.
Bitsight also has a company API Token option with admin permissions. It is not required for the SecOps platform Bitsight source but is applicable.