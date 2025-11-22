# Creating an Exact Data Match Template
Source: https://help.zscaler.com/zia/creating-exact-data-match-template
PDF: https://help.zscaler.com/pdf/com/en/1400656.pdf

[Watch a video on Exact Data Match.](https://fast.wistia.net/embed/iframe/5jnzyl383a)
Using the [Index Tool](/zia/about-index-tool) you can create, modify, or delete an Exact Data Match (EDM) index template.
Creating an EDM Template
To create a new EDM template:
- Go to https://<IP Address of the Index Tool VM> to access the Index Tool. Log in to the Index Tool with your ZIA Admin Portal login credentials.
[See image.](#IndexToolLogin)
- In the **Exact Data Match Templates** dashboard, click **Create New Template**.
- In the **New Exact Data Match Template** window:
- Type in a **Template Name**. After the template is saved, this name appears in **Administration **> **Index Templates** within the ZIA Admin Portal.
- Drag and drop a comma-separated values (.csv) file into the window or click **Browse **to select a file.
- Click **Next**.
[See image.](#UploadFile)
- Define the fields you want to include in the template:
- From the drop-down menu, select a **DATA TYPE** for the field.
Be sure to select the type that best matches your data. For example, a field named SSN with sample data from the United States in the format of 123-45-6789 might need the **Social Security Number (US)** type applied, not **Numeric**. Also, for all data types, the Index Tool removes leading and trailing spaces in the data after you submit.
[]The following data types and formats are supported:
- [Aadhaar Card Number (India)](#Aadhaar)
- [ABA Bank Routing Number](#ABA)
- [Alphabetical](#Alphabetical)
- [Alphanumeric](#Alphanumeric)
- [Citizen Service Numbers (Netherlands)](#BSN)
- [Company Number (Japan)](#CorporateNumberJapan)
- [Credit Card Numbers](#CCN)
- [Date](#Date)
- [Email Address](#Email)
- [Identity Card Number (China)](#ChinaIDNumber)
- [Identity Card Number (Malaysia)](#MalaysiaIDNumber)
- [Identity Card Number (Poland)](#PolandIDNumber)
- [Identity Card Number (Thailand)](#ThailandIDNumber)
- [Individual Taxpayer Registry ID (Brazil)](#TaxBrazil)
- [Medicare Number (Australia)](#AussieMedicare)
- [Multi-alphanumeric Identity](#multi-alphanumeric-identity)
- [Multiple Alphanumeric](#multiple-alphanumeric)
- [Multi-words Alphabetical](#multiword-alphabetical)
- [MyNumber (Japan)](#MyNumberJapan)
- [National Document ID (Uruguay)](#NDID-Uruguay)
- [National Health Service Number (UK)](#NHS)
- [National Identification Card Number (Taiwan)](#TaiwanIDNumber)
- [National Identification Number (Chile)](#NIN-Chile-RUN)
- [National Identification Number (France)](#INSEEcode)
- [National Identification Number (Peru)](#DNI-Peru)
- [National Identification Number (Spain)](#DNI)
- [National Insurance Number (UK)](#UKNIN)
- [National Registry Identity Card (Singapore)](#NRIC)
- [Numeric](#Numeric)
- [Passport Number (Australia)](#passport-australia)
- [Resident Registration Number (Korea)](#RRN)
- [Social Insurance Number (Canada)](#CanadaSIN)
- [Social Security Number (Spain)](#SocialSecurityNumberSpain)
- [Social Security Number (Switzerland)](#Swiss-SSN)
- [Social Security Number (US)](#SSN)
- [Standardized Bank Code (Mexico)](#BankMexico)
- [Tax File Number (Australia)](#AussieTaxNumber)
- [Tax Identification Number (Indonesia)](#IndonesiaTaxID)
- Select the **INCLUDE FIELD IN TEMPLATE** checkbox.
- Select the **PRIMARY FIELD** checkbox for the field that you want to designate as the primary criteria for data matching.
You must select at least one primary field, and no more than two. Also, the primary field must be unique for the selected data type.
You can configure EDM to function without primary or secondary fields. To learn more, see [Configuring DLP Advanced Settings](/zia/configuring-dlp-advanced-settings).
- Click **Submit.**
[See image.](#DefineTemplateData)
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| An India-issued 12-digit unique identification (UID) number, where the number can include spaces or hyphens. | 1234-5678-90121234567890121234 5678 9012 |
[]
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A 9 digit ABA Bank routing number. | 211274450 |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of letters (a-z, A-Z). Including hyphens and underscores as character delimiters is supported. You must make sure that the data includes at least 3 characters. If you select this data type as a **PRIMARY FIELD**, the data cannot be longer than 24 characters. | abcdZSaabcd-ZSaabcd_ZS_a |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of digits (0-9) or letters (a-z, A-Z). Including hyphens and underscores as character delimiters is supported. You must make sure that the data includes at least 3 characters. If you select this data type as a **PRIMARY FIELD**, the data can include up to 8 separate variable lengths and cannot be longer than 24 characters. | Z8675309a8675309-ZSa_8675309_ZS |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Netherlands-issued 9-digit citizen service number (BSN), where the number can include spaces or hyphens. | ****111222333111 222 333111-222-333 |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Japan-issued 13-digit Corporate Number, where the first digit is a checksum number. | 728827575847868540463730533952116402622 |
[]
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Uruguay-issued Document ID number (NDIU) using the format, 7-digit number followed by a validation number where:The validation number is calculated by multiplying the 7-digit number, digit by digit, by 8123476. For example if the 7-digit number is 1.234.567, <1,2,3,4,5,6,7>.<8,1,2,3,4,7,6>=1∗8+2∗1+3∗2+4∗3+5∗4+6∗7+7∗6=132132mod10=2 | 1.234.567-2 |
| With popular format check: The popular format for an NDIU number is a 7-8 digit number separated periodically by a delimiter (period or hyphen), where the final digit is a check digit. If the number is not in the popular format, it is not supported. | 123456-C1234567-C1.234.567-C |
[]
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Without popular format check: A 13 to 19-digit credit, debit, or payment card number, where the number can include spaces or hyphens. The Index Tool performs a Luhn check on the data after you submit. | 49295971548728027154539 0864 8005 06904539-0864-8005-0690378413854542304 |
| With popular format check: The popular format for a credit card number is a range from 12-19 numeric digits separated periodically by a delimiter (slash, period, hyphen, or space). If the number is not in the popular format, it is not supported. | AMEX (15 digits)NNNN<delimiter>NNNNNN<delimiter>NNNNNDiner's Club (14 digits)NNNN<delimiter>NNNNNN<delimiter>NNNNChina UnionPay (16 digits beginning with 62 or 60)62NNNNNNNNNNNNN62NNNNNNNNNNNNNNNNNMaestro Debit Card (16–19 digits starting with 50, 56, 57, 58, 6013, 62, 63, or 67)50NN-NNNN-NNNN6013 NNNN NNNNOther Credit Cards (16 digits)NNNN<delimiter>NNNN<delimiter>NNNN<delimiter>NNNNNNNN NNNN NNNN NNNN |
[]
-
-
-
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any date using the format MM/DD/YY, DD/MM/YY, MM/DD/YYYY, or DD/MM/YYYY where:MM: Is the 2-digit month (01-12)DD: Is the 2-digit day (01-31)YY: Is the 2-digit year (00-99)YYYY: Is the 4-digit year (0000-3000)Including forward slashes as character delimiters is supported. | 02/23/9902/23/1999 |
| To obtain access to this feature, contact Zscaler Support.You can configure DLP EDM to have strict checking against popular date formats.This feature supports 6- to 8-digit date formats that contain hyphens (`-`) or periods (`.`). | 25-12-2525-12-202525.12.2525.12.2025 |
[][](https://tools.ietf.org/html/rfc5321#section-4.1.2)
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any email address using the RFC 5321 Simple Mail Transfer Protocol syntax definition. However, international email addresses (i.e., characters using UTF-8 encoding) are not supported. | jane.doe@zscaler.comjdoe47@corp.zscaler.coma.b.c@x.y.rua_b_c@x.y.z.de |
[]
-
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A China-issued 17 or 18-digit Resident Identity Card number using the format of ######YYYYMMDD000@, where:######: Is a 6-digit numberYYYY: Is the 4-digit yearMM: Is the 2-digit month (01-12)DD: Is the 2digit day (01-31)000: Is a 3-digit number@: Is a checksum number or the letter X | 11010819700805664411010819700805880X |
[]
-
-
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Malaysia-issued 12-digit national identity card (MyKad) number using the format of YYMMDD-##-000@, where:YY: Is the 2-digit yearMM: Is the 2-digit month (01-12)DD: Is the 2-digit day (01-31)##: Is a 2-digit number (0-99, excluding 17-20, 69-70, 73, 80-81, 94-97)000: Is a 3-digit number@: Is a 1-digit number (0-9)Including spaces and hyphens as character delimiters is supported. | 991111113456991111-11-3456991111 11 3456 |
[]
-
-
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Poland-issued 11-digit national identification number (PESEL) using the format of YYMMDD####@, where:YY: Is the 2-digit yearMM: Is the 2-digit month.For people born between 1900 and 1999 (01-12)For people born between 2000 and 2099 (21-32)DD: Is the 2-digit day (01-31)####: Is a 4-digit number@: Is a checksum number | 8401120165442251488383 |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Thailand-issued national identity card number using a 12-digit number and the 13th digit is a checksum. Including hyphens and underscores as character delimiters is supported. | 3-7377-29920-32-63_7377_29920_32_6 |
[]
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Brazil-issued 11 digit Individual Taxpayer Registry ID number (CPF). The popular format for CPF numbers is "ddd.ddd.ddd-dd". Since '.' (dot) is an EDM numeric delimiter a CPF number in the format "401.757.431-93" does not match. | 40175743193 |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| An Australia-issued 10-digit Medicare number, where the first digit is from 2 to 6 and the ninth digit is a checksum. Including spaces and hyphens as character delimiters is supported. | 2123 45670 12123-45670-1 |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of a maximum of 4 alphanumeric character groupings. The character groupings can include any combination of digits (0-9), letters (a-z, A-Z), and special characters, and each character grouping must include at least three alphanumeric characters.A field with this data type cannot be selected as a primary field for a template.Zscaler recommends the use of the Multi-alphanumeric Identity data type instead of this data type. This data type does not follow the order of the indexed string. A match can happen even if the data does not appear in the same order. | Bob Anne Smith1234 Smith Street, San Jose123 Gary-Carter Street, Quebec |
[]
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of a maximum of 4 words and three spaces (e.g., personal names, city names, entity names).A field with this data type cannot be selected as a primary field for a template. | San FranciscoGeneral Motors CompanyBob SmithMary Joe Fernandez James |
[]
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of a maximum of 4 alphanumeric character groupings. The character groupings can include any combination of digits (0-9), letters (a-z, A-Z), and special characters, and each character grouping must include at least three alphanumeric characters.When you upload data, strings are normalized and a match occurs only if all of the data appears in the same order as the normalized character grouping. For example, if the following strings are sent:"123 Bob Anne Smith aaas" matches."Bob 123 Anne Smith aaaa" does not match."123 Anne Bob Smith aaaa" does not match."Bob 12 Anne Smith aaaa" matches because "12" is too short and is ignored."Bob + Anne Smith" matches.A field with this data type can be selected as a primary field for a template. | Bob Anne Smith1234 Smith Street, San Jose |
[]
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Japan-issued 12-digit My Number (also known as Individual Number), where the last digit is a checksum number. Including hyphens, spaces, and ‘.’ (dot) as delimiters is supported. | 6756161481736756-1614-81736756 1614 81736756.1614.8173 |
[]
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A 10 digit United Kingdom-issued National Health Service (NHS). | 3256728308 |
[]
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Taiwan-issued national identification card number using one prefix letter (A-Z, excluding L, R, S, Y), one digit (1 or 2), an 8-digit number, and the ninth digit is a checksum. | M140051654 |
[]
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Chile-issued national identity card number (RUN) using the format of an 8-digit number followed by a verification digit where the digit is either a number or the letter K. | 76086428-52211011-K |
| With popular format check: The popular format for a RUN number is an 8-digit number separated periodically by a delimiter (period or hyphen), where the final digit is either a check digit or the letter K. If the number is not in the popular format, it is not supported. | 1234567-C1.234.567-C12345678-C12.345.678-C |
[]
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A France-issued national identification number (INSEE code) using the format of 0YYMM######## @@, where:0: Is a 1-digit number (1 or 2)YY: Is the 2-digit yearMM: Is the 2-digit month (01-12)########: Is a 8-digit number@@: Is a 2-digit checksumIncluding spaces and hyphens as character delimiters is supported. | 1801269552223 801801269552223-80 |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Peru-issued national identity card number (CUI) using an 8-digit number followed by a verification digit. | 32415895-B42388604-341510304-B |
| With popular format check: The popular format for a CUI number is an 8-digit number with a hyphen and a check digit. If the number is not in the popular format, it is not supported. | 12345678-C |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Spain-issued national identity card number (DNI) using an 8-digit number and one letter representing the checksum (a-z, A-Z, excluding i, o, u, I, O, U). | 45592283G25621992s |
[]
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A United Kingdom-issued insurance number (NINO) using 2 prefix letters (a-z, A-Z), 6 digits (0-9), and a suffix letter. Including hyphens and underscores as character delimiters is supported. | AB123456CAB878977C |
| With popular format check: The popular format for a NINO number contains 2 prefix letters (a-z, A-Z), 6 digits, and a suffix letter. The popular format can contain spaces. If the number is not in the popular format, it is not supported. | AA123456AAA 12 34 56 A |
[]
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Singapore-issued NRIC number/FIN using the format of #0000000@, where:#: Is a letter that can be S, T, F, or G0000000: - Is a 7-digit number@: Is a checksum letter calculated with respect to # and 0000000Including hyphens and underscores as character delimiters is supported. | S-1234567-AT-1234567-B |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Any combination of digits (0-9). Including spaces and hyphens as character delimiters is supported. You must make sure that the data includes at least 3 characters. If you select this data type as a **PRIMARY FIELD**, the data can include up to 8 separate variable lengths and cannot be longer than 24 characters. | 212-867-530986 7 530 9 |
[]
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| An Australian passport using the format of An(7), where A is a single letter and n is a combination of 7 digits. A delimiter (hyphen, spaces, or period) after the letter and before the numbers is supported.The following letters are valid for the An(7) passport format: M, N, E, D, F, A, C, U, and X | N1234567N-1234567N 1234567 |
| An Australian passport using the format of AAn(6), where AA is a combination of two letters and n is a combination of 6 digits. A delimiter (hyphen, spaces, or period) after the letters and before the numbers is supported.The following letter combininations are valid for the AAn(6) passport format: PA - PF, PU, PW, PX, PZ, and RA - RZ | PA123456PB-123456RA 123456 |
[]
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A South Korea-issued resident registration number using the format of YYMMDD-######@, where:YY: Is the 2-digit yearMM: Is the 2-digit month (01-12)DD: Is the 2-digit day (01-31)######: Is a 6-digit number@: Is a checksumIncluding spaces and hyphens as character delimiters is supported. | 800821-6490697800821 6490697 |
[]
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| Without popular format check: A Canada-issued 9-digit social security number, where the number can include spaces or hyphens. | 123-456-789123456789 |
| With popular format check: A 9-digit number separated at the 3rd and 6th digit by a delimiter (period, hyphen, or space) or not separated at all. If the number is not in the popular format, it is not supported. | 123-456-789123 456 789123.456.789123456789 |
[]
-
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Spain-issued 12-digit social security number using the format of ##00000000@@, where:##: Is a 2-digit number (01-50, 53, 66)00000000: Is a 8-digit number@@: Is a 2-digit checksumIncluding hyphens, spaces, and ‘.’ (dot) as character delimiters is supported. | 28123456784028-12345678-4028 12345678 4028.12345678.40 |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Switzerland-issued 13-digit social security number (AHV), where the first three digits are 756 and the 13th digit is a checksum. The popular format for the AHV number is “756.dddd.dddd.dd”. Including ‘.’ (dot) as character delimiters is supported. | 756.2022.6001.167562022600116 |
[]
-
-
-
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A United States-issued 9-digit social security number, where the number can include spaces or hyphens. | 123-45-6789123 45 6789123456789 |
| With popular format check: A 9-digit number separated in parts by a delimiter (hyphen or space) or not separated at all. If the number is not in the popular format, it is not supported. | 123 45 6789123-45-6789123456789 |
[]
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| A Mexico-issued 18 digit Standardized Bank Code (CLABE) number. | 102211123456789015 |
[]
-
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| An Australia-issued 8 or 9-digit tax file number, where the number can include spaces or hyphens. | 123-456-789123 456 7891234567-8 |
[]
-
-
| **Supported Format** | **Examples** |
| -------------------- | ------------ |
| An Indonesian-issued 15-digit tax identification number (NPWP), where the 9th digit is a checksum. The popular format for the tax identification number is “dd.ddd.ddd.d-ddd.ddd”. Including ‘.’ (dot) and hyphens as character delimiters is supported. | 02183241512345602.183.241.5-123.456 |
You are redirected back to the **Exact Data Match Templates** dashboard, and the tool processes the template. If the template was created properly, **Completed** is shown in the **Status** column. If the template was not created properly, then** Error** is shown.
Click on the template row to view the **Template Details** page. If an error occurred, details about the error are displayed. Be sure to read the **Error Detail**, which includes a **Recommended Action**, while troubleshooting the issue.
[See image.](#ErrorDetails)
When an EDM template is created, it appears on the [Index Templates](/zia/about-exact-data-match) page of the ZIA Admin Portal, where you can view the template's details or delete it. You cannot change the template name after creation. Also, after creation, you cannot update the included fields or the selected primary fields within the template. In order to make these modifications, you must create a new template.
Submitting New EDM Template Data
To submit new data for an EDM template:
- Log in to the Index Tool.
- In the **Exact Data Match Templates** dashboard, locate the template you want to modify.
- In the **Actions **column:
- If you need to resubmit data for a template that was processed successfully (i.e., has a Completed status), click the **Submit New Data** icon. The data types, included fields, and primary fields you originally selected for the template are not updated. You must create a new template to modify the data types and selected fields.
- If you need to resubmit data for a template that did not process successfully (i.e., has an Error status), click the **Submit New Data** icon or click the **Edit Template** icon. The ability to edit a template only becomes available if there was an error when you originally submitted the data. If you edit a template, you are able to modify the data types and selected fields to resolve the issue.
[See image.](#DashboardActions)
You can also click on the template row and, in the **Template Details** page that appears, click **Submit New Data** or **Edit Template** (if available).
[See image.](#TemplateDetailActions)
The selected included fields and primary fields you originally selected for the template are not updated. You must create a new template to modify fields.
- In the **Upload File** window that appears, drag and drop the .csv file into the window or click** Browse** to select the file.
- Click **Submit**.
Scheduling Updates for an EDM
After you have successfully uploaded your template, you can schedule regular updates. You can also choose to receive an [Alert](/zia/about-alerts) if there are any missed updates.
To schedule regular updates for your EDM Template:
- Log in to the Index Tool.
- In the Exact Data Match Templates dashboard, locate the template you want to schedule updates for.
- Perform one of the following actions:
- In the **Actions** column, click the **Schedule** icon.
[See image.](#scheduleIcon)
- Click on the template row. The Template Details page appears. In this window, click **Create Schedule**.
[See image.](#scheduleLabelButton)
- In the **Schedule Template Update** window, select the following:
- **File Path**: The file path is automatically populated with the location that you uploaded your file to. Ensure that the file is still at this location.
- **Status**: Select whether to **Enable** or **Disable** your schedule
- **Repeat**: Choose if the update repeats **Monthly**, **Weekly**, or **Daily**.
- **Every**: If you selected **Monthly** or **Weekly**, choose when in the selected period the update repeats. For example, if you selected **Weekly**, you can choose to have the update happen every Friday.
If you select **Monthly**, index updates are converted to, and trigger in UTC. It is possible that after being converted, your update may occur between the 29th and 31st UTC. If a month doesn't contain the converted date, that update is skipped.
For example, if you schedule your update to occur on the 28th of every month at 5:00 PM PST, it does not trigger in February since the UTC time is already 1:00 AM February 29 and that date does not exist (excluding leap years). If you schedule your update to occur on the first of every month at 8:00 AM IST, it also does not happen every month. As the UTC time is 3:00 AM on the 31st, it does not occur in February, April, June, September, or November.
Zscaler recommends you schedule your monthly updates to occur between the 2nd and the 27th.
- **At**: Choose what time the scheduled update happens on.
- **Time Zone**: Select the time zone your update happens in.
- **Update Now**: Select to immediately update the template.
[See image.](#scheduleWindow)
- Click **Save**.
To edit your schedule:
- Log in to the Index Tool.
- In the Exact Data Match Templates dashboard, locate the template whose schedule you want to edit.
- Perform one of the following actions:
- In the** Actions** column, click the **Schedule** icon. The **Schedule Index Update** window appears.
- Click on the template row. The Template Details page appears. Click** Edit Schedule**. The **Schedule Index Update** window appears.
- Make your desired changes and click **Save**.
To delete your schedule:
- Log in to the Index Tool.
- In the Exact Data Match Templates dashboard, locate the template whose schedule you want to delete.
- Perform one of the following actions:
- In the **Actions** column, click the **Schedule** icon. The **Schedule Index Update** window appears.
- Click on the template row. The Template Details page appears. Click **Edit Schedule**. The **Schedule Index Update** window appears.
- In the **Schedule Index Update** window, click **Delete** in the lower right-hand corner.
To temporarily disable your schedule, set the status to **Disable**.
Deleting an EDM Template
To delete an EDM template, do one of the following sets of steps:
- Delete from the Exact Data Match Templates Dashboard
- Log in to the Index Tool.
- In the **Exact Data Match Templates** dashboard, locate the template you want to remove.
- In the **Actions** column, click the **Delete** icon.
You can also click on the template row and, in the **Template Details** page, click **Delete Template**.
- In the confirmation window that appears, click **Delete**.
- []Delete from the Index Templates
- Go to** Administration** > **Index Templates**.
- Locate the template you want to remove and click the **View** icon.
- In the **View Template** window, click **Delete**.
[See image.](#ViewTemplate-AdminPortal)
- In the confirmation window that appears, click **Confirm**.
[]**![zia-indextool-login.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-indextool-login.png)
**
[]**![Create Exact Data Match template page with defined fields displayed](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-indextool-selectdatafields.png)
**
[]**![Index Tool Template Details Page with Error Details Displayed](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-indextool-edmfileerror.png)
**
[]**![New Exact Data Match Template page within the Index Tool](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-indextool-edmfileupload.png)
**
[]**![View Template window for Index template within Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-exact-data-match/creating-exact-data-match-template/ZIA-DLP-EDM-View-Template.png)
**
[]![Screenshot showing the difference between a template with an error and a template with no error.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-dlp-with-error0.png)
[]**![zia-indextool-submitdataandedittemp.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-indextool-submitdataandedittemp.png)
**
[]![Screenshot showing the Schedule icon highlighted](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-dlp-schedule-icon.png)
[]![Screenshot showing the Create Schule button view](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-dlp-create-schedule-label.png)
[]![Screenshot of the Schedule Template Update window](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/creating-exact-data-match-template/zia-dlp-schedule-window.png)