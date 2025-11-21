# Understanding Exact Data Match Index Templates
Source: https://help.zscaler.com/unified/understanding-exact-data-match-index-templates
PDF: https://help.zscaler.com/pdf/com/en/1493231.pdf

When creating an [Exact Data Match (EDM)](/unified/about-exact-data-match) index template, you must define your tokens (i.e., criteria) for your data records, and specify at least one primary field. The primary field is a unique key that your DLP policy rules are based on. It is a required field that must be unique based on your data records.
You can configure EDM to function without primary or secondary fields. To learn more, see [Configuring DLP Advanced Settings](/unified/configuring-dlp-advanced-settings).
The primary field can include any recognized standard format with variable lengths (e.g., credit card numbers) or any custom formats with fixed lengths (e.g., alphabetical values). To learn more, see [Creating an Exact Data Match Template](/unified/creating-exact-data-match-template).
To learn more about creating and using EDM templates, see:
- [Evaluating Your Data and DLP Policies](#evaluate-data-DLP-policies)
- [Identifying Primary Fields Within Your EDM Index Template](#identify-primary-fields)
- [Evaluating Your Data Records With Your EDM Index Template](#evaluate-data-records)
- [Understanding EDM Template Processing](#EDM-Template-Creation-Process)
- [Understanding EDM Reporting](#EDM-Reporting)
[]Zscaler recommends considering the following before creating an EDM index template:
- Review the DLP policy you want to create and the data you want to protect.
- As you review the DLP policy, consider the data that must be included in your EDM index template.
- Try to create a template where your data records need to be indexed once, and avoid the need to re-index whenever possible.
- Review your data records to avoid potential duplication.
Let's use the following example:
You're a bank with an employee database and you want to protect your employees' personally identifiable information (PII), as well as their company credit card information.
Your database records contain the following data fields: First Name (FName), Last Name (LName), Social Security Number (SSN), Credit Card Number (CCN), Mobile Phone Number, Postal Code, Street Address, and so on.
The DLP dictionaries or engines you need to create, which can then be used in your DLP policies, must cover a series of field combinations to adequately protect your employees' information. So, based on your records in this example, any of the following data field combinations could be used to create a DLP dictionary:
- SSN, FName, LName
- CCN, FName, LName
- SSN, CCN, LName
- SSN, CCN, FName, LName
However, the EDM index template you create using the Index Tool must allow the dictionary to cover the field combination you require. You can do this by selecting a primary field based on the data field combination you need.
[]Using the example described in the previous section, specifying a primary field allows you to create a single EDM index template to protect your employees' information, where:
- all of the data field combinations you require for an employee PII DLP dictionary and associated policies are covered.
- all of the data field combinations you require for a credit card DLP dictionary and associated policies are covered whenever a company credit card is issued to an employee.
- your employee data records only need to be indexed once.
So, using the Index Tool, you would create an EDM index template that includes the following fields:
- SSN
- CCN
- FName
- LName
To create the employee PII DLP dictionary you require, you'd select SSN as a primary field. However, in order to create the company-issued employee credit card DLP dictionary using the same template, you also need to select CCN as a secondary primary field. The other included fields (i.e., FName, LName) are applied as Secondary Fields for both dictionaries.
Finally, in this example, BankNum is not a required data field for the DLP policies we want to create later, so it is not included within the template.
![Zscaler Index Tool on EDM Index Template field selection page ](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/about-exact-data-match/zia-edmtemplateexample-2primarykeys.png)
When you create the PII-specific DLP dictionary within the Admin Portal, it needs to cover a data field combination that includes: SSN with FName and LName. So you would select **Exact Data Match** as your **Dictionary Type**, and add the following definition based on the EDM index template you created:
- Employee PII Definition
- **SSN** selected as the **Primary Field**
- **FName** and **LName** selected as the **Secondary Fields**
- **All Fields** selected for **Secondary Match On**
![Adding a DLP dictionary with an Exact Data Match definition for employee PII](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-EDM-PII-Dictionary-Example-1.png)
The Zscaler service assumes an AND Boolean operation between the **Primary Field** and the **Secondary Fields**. Also, for **Secondary Match On**, "Any" (i.e., **Match at Least 1 from Secondary Fields**, **Match at Least 2 from Secondary Fields**) assumes an OR operation, while "All" (i.e., **All Fields**) assumes an AND operation.
In other words, the definition above is evaluated by the Zscaler service as: "SSN AND (FName AND LName)".
Because CCN is included as your secondary primary field within the EDM index template, you can use the same template for your company credit card-specific DLP dictionary. In this example, it needs to cover the data field combination that includes: CCN with FName or LName. So, you can add the following definition without having to re-index your employees' data records:
- Company-issued Employee CCN Definition
- **CCN** selected as the **Primary Field**
- **FName** and **LName** selected as the **Secondary Fields**
- **Match at Least 1 from Secondary Fields** selected for **Secondary Match On**
![Adding a DLP dictionary with an Exact Data Match definition for company-issued employee credit cards](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-EDM-CCN-DLP-Dictionary_Example2_0.png)
In other words, the definition above is evaluated by the Zscaler service as: "CCN AND (FName OR LName)".
Using these two DLP dictionaries, the service can then evaluate the following data field combinations when they are added to a DLP engine, which is used to create your DLP policy rules:
- SSN AND (FName AND LName)
- CCN AND (FName OR LName)
To learn more, see [About DLP Engines](/unified/about-dlp-engines).
[]When the Zscaler service evaluates your data records, it only evaluates strings with three characters or more. The service ignores any blank cells (i.e., the service does not consider blank cells to be implicit matches).
For example, you need a PII-specific DLP dictionary that includes SSN with First Name, Last Name, and Date of Birth (DD MM YYYY). First, you create an EDM index template with the following CSV file:
| SSN | First Name | Last Name | Date of Birth |
| --- | ---------- | --------- | ------------- |
| 123-45-6789 | John | Smith |  |
| 234-56-7891 | Mary |  | 01 01 1990 |
| 354-67-8912 |  | Brown | 02 02 1985 |
You then create a dictionary with the following definition based on your EDM index template:
- Employee PII Definition
- **SSN **selected as the **Primary Field**
- **First Name** and **Last Name** selected as the **Secondary Fields**
- **Match at Least 1 from Secondary Fields** selected for **Secondary Match On**
[See image.](#At-Least-One)
With this definition, the match occurs when the primary field and at least one secondary field are present. However, if the secondary field is blank, then the match doesn't occur.
If an employee uploads a file containing the SSN "123456789" and First Name "John", the match occurs. If the employee uploads a file containing the SSN "345678912" instead, the match doesn't occur because no secondary fields were matched. In this example, the only available secondary field was "Brown" and it was not present in the document.
You decide to increase the number of secondary fields for your definition:
- Employee PII Definition
- **SSN** selected as the **Primary Field**
- **First Name**, **Last Name**, and **Date of Birth** selected as the **Secondary Fields**
- **Match at Least 2 from Secondary Fields** selected for **Secondary Match On**
[See image.](#At-Least-Two)
With this definition, the match occurs when the primary field and at least two secondary fields are present. However, if at least one of the secondary fields is blank, then the match doesn't occur.
If an employee uploads a file containing the SSN “234567891”, the First Name “Mary”, and the Date of Birth “01 01 1990”, then the match occurs. If the employee uploads a file containing the SSN “123456789” and the First Name “John” instead, the match doesn’t occur, because the Last Name isn’t present and the Date of Birth is blank.
[]When you click the Submit button during the creation of an EDM template in the Index Tool, Zscaler processes the EDM template to ensure that the template was created properly. The processing by Zscaler checks for any issues related to the EDM template such as data errors, primary field duplication errors, and communication errors. If Zscaler does not find any issues, then a status of completed is displayed for the EDM template in the Index Tool and the template is available for use in the Admin Portal. If Zscaler does find issues, then a status of error is displayed for the EDM template in the Index Tool.
You can view the process details for an EDM template on the Template Details page. This page is accessed by selecting an EDM template row in the Index Tool. The Template Details page displays different information depending on whether the EDM Template process was completed successfully or if there were errors during the process. For completed EDM templates, the following information is displayed on the page:
- Template Detail
- Template Definition
For EDM templates in error, some or all of the following information is displayed on the page:
- Type
- Cause
- Recommended Action
- Log Detail
- Template Detail
- Template Definition
This information provides insight on how to correct an EDM template that is in error.
If an error is due to the primary key limit being exceeded across multiple EDM templates, then an EDM Indexing Failed Schemas notification is also generated and is displayed in the Notification pane of the Admin Portal. This notification lists the EDM template that caused the primary key limit to be exceeded. For your organization, you cannot have more than 2,048 primary duplicate keys across one or more EDM templates.
For this type of EDM template error, the error is associated with multiple EDM templates but the Notification pane only lists the last EDM template that caused the limit to be exceeded. To correct this issue, analyze the last EDM template that caused the issue in the Index Tool and identify which primary key caused the error. Then, delete or rectify that EDM template or any other previous EDM templates that contain that same primary key that was duplicated.
Examples of Primary Duplicate Keys Being Exceeded for EDM Templates
The following examples illustrate how primary duplicate keys can be exceeded across one or multiple EDM templates. All of the examples use the 512 duplicate key limit for an individual EDM template and the 2,048 duplicate key limit across multiple EDM templates.
- [Example of Duplicate Primary Keys Being Exceeded with One EDM Template](#dup-primary-key-example-1)
- [Example of Duplicate Primary Keys Being Exceeded Across Multiple EDM Templates Using a Single Field](#dup-primary-key-example-2)
- [Example of Duplicate Primary Keys Being Exceeded Across Multiple EDM Templates Using More Than One Field](#dup-primary-key-example-3)
In this example, the duplicates occur within one EDM template.
[]
| Template Name | Fields in Template |
| ------------- | ------------------ |
| EDM Template 1 | SSN (Primary Key)600 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
For this example, after EDM Template 1 is processed it receives an error status in the Index Tool with *Too many primary key duplicates* as the error type. This template contains 600 duplicates, which exceeds the 512 duplicate limit for an individual EDM template.
[]In this example, the duplicates are the same for one type of field across multiple EDM templates. The same SSN number is duplicated across all of the EDM templates.
| Template Name | Fields in Template |
| ------------- | ------------------ |
| EDM Template 1 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 2 | SSN (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 3 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 4 | SSN (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 5 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 6 | SSN (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
For this example, after the EDM Templates are processed, EDM Template 1 through EDM Template 5 receive a completed status in the Index Tool. Each of these templates does not exceed the 512 primary duplicate limit for an individual EDM template and the combined number of primary duplicates across your organization is 1,800, which is below the 2,048 duplicate key limit across multiple EDM templates.
EDM Template 6 receives an error status in the Index Tool with a *primary key limit* error type and an EDM Indexing Failed Schemas notification is displayed on the Notification pane of the Admin Portal listing this template name. This template does not exceed the 512 primary duplicate limit for an individual template, but with the addition of this template, the 2,048 primary duplicate key limit across multiple EDM templates has been exceeded for your organization. There were 1,800 duplicates after EDM Template 5 was processed, but now with the addition of EDM Template 6 of 300, that would make 2,100 duplicates.
To correct the primary duplicate error that occurred in EDM Template 6, you need to analyze not only that template but all of the other templates that preceded it to identify how to correct and rectify the primary duplicate error.
[]In this example, the duplicates are the same for different types of fields across multiple EDM templates. The same number is duplicated across SSN, Account Number, Gambler Number, and Patient ID.
| Template Name | Fields in Template |
| ------------- | ------------------ |
| EDM Template 1 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 2 | Account Number (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 3 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 4 | Gambler Number (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 5 | SSN (Primary Key)400 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
| EDM Template 6 | Patient ID (Primary Key)300 Duplicates | CCN (Primary Key)No Duplicates | FNameNo Duplicates | LNameNo Duplicates |
For this example, after the EDM Templates are processed, EDM Template 1 through EDM Template 5 receive a completed status in the Index Tool. Each of these templates does not exceed the 512 primary duplicate limit for an individual EDM template and the combined number of primary duplicates across your organization is 1,800, which is below the 2,048 duplicate key limit across multiple EDM templates.
EDM Template 6 receives an error status in the Index Tool with a *primary key limit* error type and an EDM Indexing Failed Schemas notification is displayed on the Notification pane of the Admin Portal listing this template name. This template does not exceed the 512 primary duplicate limit for an individual template, but with the addition of this template, the 2,048 primary duplicate key limit across multiple EDM templates has been exceeded for your organization. There were 1,800 duplicates after EDM Template 5 was processed, but now with the addition of EDM Template 6 of 300, that would make 2,100 duplicates.
To correct the primary duplicate error that occurred in EDM Template 6, you would need to analyze not only that template but all of the other templates that preceded it to identify how to correct and rectify the primary duplicate error.
[]![Defining Exact Data Match Criteria on the Add DLP Dictionary Page](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-Add-DLP-Dictionary-EDM-At-Least-One.png)
[]![Defining Exact Data Match Criteria on the Add DLP Dictionary Page](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/about-exact-data-match/ZIA-Add-DLP-Dictionary-EDM-At-Least-Two.png)
[]
For reporting purposes, the Zscaler service provides a total `matchCount`, as well as the `triggers` that help determine that count. Total `matchCount` logic is based on the number of unique sets of matches found in the content. The logic also applies to multiple templates used in the same dictionary.
- [Example 1](#edm-reporting-example-1)
- [Example 2](#edm-reporting-example-2)
- [Example 3](#edm-reporting-example-3)
- [Example 4](#edm-reporting-example-4)
- [Example 5](#edm-reporting-example-5)
[]
Use the following CSV file for the following example:
`AlphaNum1, AlphaNum2, AlphaNum3
aaa, 111, abc
bbb, 222, cde
aaa, 444, 111                                                    `
Dictionary logic:
- `AlphaNum1`: The primary field.
- `AlphaNum2 `and `AlphaNum3`: The secondary fields.
- Primary field AND any 1 out of 2 secondary field matches needed.
Upload Text:
`aaa, 111`
Dictionary matches rows:
`aaa, 111, abc
aaa, 444, 111`
`matchCount` is 1 because the upload text has 1 unique match (`aaa, 111`).
[]
Using the same CSV file, index, and dictionary as the previous example:
`AlphaNum1, AlphaNum2, AlphaNum3
aaa, 111, abc
bbb, 222, cde
aaa, 444, 111                                                    `
Dictionary logic:
- `AlphaNum1`: The primary field.
- `AlphaNum2 `and `AlphaNum3`: The secondary fields.
- Primary field AND any 1 out of 2 secondary field matches needed.
Upload Text:
`aaa, 111, abc`
Dictionary matches rows:
`aaa, 111, abc
aaa, 444, 111`
`matchCount` = 1 because the upload text has 1 unique match (`aaa, 111, abc`).
[]Use the following CSV file for the following example:
`LASTNAME, SSN, ACCOUNT NUMBER, ZIP CODE
DOE,111222333,123456789000, 95132
DOE,111222444,123456789000, 95134
DOE,111222555,123456789000, 95135`
Dictionary logic:
- 2 out of 4 field matches needed.
Upload text:
`DOE 123456789000`
Dictionary matches rows:
`DOE,111222333,123456789000, 95132
DOE,111222444,123456789000, 95134
DOE,111222555,123456789000, 95135`
MatchCount = 1 because the upload text has 1 unique match (`DOE``,``123456789000`).
[]
Use the following CSV file for the following example:
`ssn, FirstName, LastName
123, abc, xyz
123, xyz, abc`
Dictionary logic:
- Dictionary A: Match primary AND match all secondary fields.
- Dictionary B: Match primary AND match any one secondary field.
Upload Text 1:
`123, abc`
Dictionary matches:
Dictionary B, `matchCount `= 1.
Upload Text 2:
`123, xyz`
Dictionary matches:
Dictionary B, `matchCount `= 1.
Upload Text 3:
`123, abc, xyz`
Dictionary matches:
Dictionary A, `matchCount` = 1 AND dictionary B, `matchCount `= 1.
Upload Text 4:
`123, abc, xyz
123, abc
123, xyz`
Dictionary matches rows:
`ssn, FirstName, LastName
123, abc, xyz
123, xyz, abc`
Dictionary A, `matchCount` = 1 AND dictionary B, `matchCount `= 1.
[]For the following example, see how the logic applies to multiple templates in the same dictionary.
CSV1 file to index:
`AlphaNum1, AlphaNum2, AlphaNum3
aaa, 111, abc
bbb, 222, cde
aaa, 444, 111`
CSV2 file to index:
`AlphaNum1, AlphaNum2
111, abc
bbb, 222`
Dictionary logic:
- Template 1
- `AlphaNum1`: The primary field.
- `AlphaNum2 `and `AlphaNum3`: The secondary fields.
- Template 2:
- `AlphaNum1`: The primary fields.
- `AlphaNum2`: The secondary fields.
Dictionary:
- Template 1
- `AlphaNum1`: The primary fields.
- `AlphaNum2` and `AlphaNum3`: The secondary fields.
- 1 out of 2 matches needed.
- Template 2
- `AlphaNum1`: The primary fields.
- `AlphaNum2`: The secondary fields.
- All matches needed.
Upload Text:
`aaa, 111, abc`
Dictionary 1 matches rows:
`aaa, 111, abc
aaa, <444>, 111`
- Template A, `matchCount` = 1 because the upload text has 1 unique match (`aaa, 111, abc`),
- Template B, `matchCount` = 1 because the upload text has 1 unique match (`111, abc`).