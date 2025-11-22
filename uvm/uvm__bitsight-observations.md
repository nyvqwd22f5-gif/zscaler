# Bitsight Observations
Source: https://help.zscaler.com/uvm/bitsight-observations
PDF: https://help.zscaler.com/pdf/com/en/1528166.pdf

![mceclip0.png](/downloads/uvm/configure/sources/bitsight-observations/mceclip0.png)
Bitsight helps organizations quantify their cyber risk, measure the impact of their security efforts, and benchmark their performance against peers. The Bitsight Observations source retrieves observations data. To learn more, refer to the [Bitsight documentation](https://help.bitsighttech.com/hc/en-us/articles/360016546433-GET-Detailed-Company-Observations).
Required Parameters
- API Token
- Grades: To learn more, refer to the [Bitsight documentation](https://help.bitsighttech.com/hc/en-us/articles/1500004356421-API-Fields-Finding-Grades).
- Number of days to fetch: The number of days you want to retrieve in each run.
Generating an API Key
The API token should be generated using a user with Reader permissions. To generate an API key:
- Log in to the Bitsight platform.
- Go to **Settings** > **Account** > **API Token**.
- Click **Generate New Token**.
Bitsight also has a company API Token option with admin permissions. It is not required for the SecOps platform Bitsight source but is applicable.