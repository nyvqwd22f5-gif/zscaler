# Exporting and Importing Reports
Source: https://help.zscaler.com/unified/exporting-and-importing-reports
PDF: https://help.zscaler.com/pdf/com/en/1497626.pdf

You can export custom reports to a plain-text JSON (JavaScript Object Notation) file that includes the report definitions. This is useful when you want to back up reports or create duplicates of a report. For example, if you have more than one organization, you can export a report from one organization and import it into another.
The reports use a custom data structure, so you can only import JSON files that were exported from the Zscaler service administrative interface.
Exporting Reports
You can export custom reports only. To export a standard report, you can [copy](/unified/creating-or-copying-report) it, and then export it.
To export a report:
- Go to **Analytics** > **Internet & SaaS** > **Analytics **>** Interactive Reports**.
- From the **Custom Reports** tab, select the checkbox of the report you want to export.
-
Click **Export**.
The service exports it to the default Downloads folder on your computer.
Importing Reports
To import a report:
- Go to **Analytics** > **Internet & SaaS** > **Analytics **>** Interactive Reports**.
-
Click **New Report**, then **Import**.
The **Import** window appears.
-
In the** Import **window:
- Click **Choose File** and select the JSON file.
- Click **Upload**.
The imported report appears in the **Custom Reports** tab.
Duplicating Reports
To duplicate a report:
- Go to **Analytics** > **Internet & SaaS** > **Analytics **>** Interactive Reports**.
- From the **Custom Reports** tab, select the checkbox of the report you want to export.
-
Click **Export**.
The service exports it to the default Downloads folder on your computer.
- Using a text editor, such as Notepad, edit the JSON file.
-
Change the username and title of the report.
[See image.](#json-file)
- Import the report by following the steps in the previous section.
[]![A JSON file sample from a Zscaler report](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/creating-copying-report/ZIA-6.1-Report-JSON-File.png)