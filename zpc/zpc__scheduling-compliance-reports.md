# Scheduling Compliance Reports
Source: https://help.zscaler.com/zpc/scheduling-compliance-reports
PDF: https://help.zscaler.com/pdf/com/en/1402636.pdf

You can schedule compliance summary reports for regular distribution to specified recipients.
A warning icon appears next to the Schedule Name if there is an issue with the schedule scope (e.g., the Business Unit assigned to the scheduled report was deleted).
To schedule a compliance report:
- Go to **Administration** > **Scheduled Reports**.
- Click **Add Schedule**.
[See image.](#add-schedule)
- On the **General Information** tab:
- **Schedule Name**: Enter a unique name for the report.
- **Format**: Select either **Excel** or **PDF**.
- **Benchmark**: Select one or multiple active compliance benchmarks.
- Click **Next**.
[See image.](#general-information-image)
- On the **Scope** tab, use the following filter drop-down menus to focus on desired information:
- **Business Units**: Select one or multiple business units. Business units are logical groups of multiple cloud accounts.
- **Clouds**: Select one or multiple cloud service providers.
- **Accounts**: Select one or multiple cloud accounts.
- **Regions**: Select one or multiple regions
[See image.](#scope-image)
To learn more about filters, see [Using Filters](/zpc/using-filters).
- Click **Next**.
- On the **Schedule** tab:
- **Frequency**: Select a schedule as follows:
- Select **Daily** and select the **time** and **timezone**.
- Select **Weekly** and select the **day**, **time**, and **timezone**.
- Select **Monthly** and select the **date**, **time**, and **timezone**.
- **Recipients**: Enter the email addresses of the recipients.
[See image.](#frequency-image)
- Click **Next**, then click **Finish**.
[]![View the general information tab in scheduling compliance reports](/downloads/zpc/reports/scheduling-reports/schedule-report-general-info-tab.png?1660898744)
[]![View the scope tab in scheduling compliance reports](/downloads/zpc/reports/scheduling-reports/zpc-schedule-report-scope.png?1656342453)
[]![View the schedule tab in scheduling compliance reports](/downloads/zpc/reports/scheduling-reports/send_at.png)
[![View the Scheduled Reports page](/downloads/zpc/reports/scheduled-reports/reports-add-schedule.png)
]