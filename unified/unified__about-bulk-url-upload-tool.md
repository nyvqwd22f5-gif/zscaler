# About Bulk URL Upload Tool
Source: https://help.zscaler.com/unified/about-bulk-url-upload-tool
PDF: https://help.zscaler.com/pdf/com/en/1493951.pdf

The Bulk URL Upload tool is a JAVA CLI tool, which runs locally on the customers' client to update URLs in bulk. This tool allows you to easily manage URL category updates using your Zscaler API credentials.
This article covers the following topics:
- [Downloading and installing the Bulk URL Upload tool](#download-install)
- [Defining the API config file](#api-file-config)
- [Defining the URL upload file](#url-upload-csv)
- [Managing custom URLs and categories using the Bulk URL Upload tool](#manage-urls)
- [Troubleshooting the Bulk URL Upload tool](#error-messages)
[]To download and install the Bulk URL Upload tool:
- Download the [UrlUpload.gz](/downloads/zia/policies/url-filtering/about-url-upload-tool/UrlUpload.gz) file.
The UrlUpload.gz file consists of urlupload.jar, truststore, and example.csv.
-
In the command prompt, run the following command to extract the files from the downloaded UrlUpload.gz file:
tar -xvf UrlUpload.gz
[]In the API config file, specify the following values:
- `BASE_URI`: The base URI for your cloud.
- `API_KEY`: The API Key provisioned for your organization.
- `USERNAME`: (Optional) The Zscaler API username.
- `UPLOAD_CSV_FILE`: (Optional) The URL upload path for the CSV file.
- [See the API config sample file](#api-config-sample)
[]BASE_URI=https://admin.zscaler.net/api/v1
API_KEY=lcurlapikeyl
USERNAME=admin@org.com
UPLOAD_CSV_FILE=upload_files/urls.csv
[]You can define one or combination of the following operations in the URL upload file:
- [Associate or Dissociate](#associate-dissociate)
- [Delete](#delete)
- [RESET](#reset)
- [Comment](#comment)
The following table lists the operators used for various operations:
| Operator | Operation |
| -------- | --------- |
| + or A | Adds or associates a URL to a category.A new category can be added only if a URL is associated with it. |
| - or D | Deletes a category or a URL from a category. |
| * or R | Replaces all the existing URLs from a category by removing them and adding a new set of URLs. |
| # | Marks the line that begins with this operator as a comment and does not execute the line. |
| RESET | Ignores all the lines before the RESET line in the file and counts only the lines after for execution. Only the last instance of the RESET takes effect when there are multiple instances. |
A sample URL upload file is as follows:
+, CAT5, RETAIN_PARENT, url42.com
+, CAT4, CUSTOM, url43.com
+, CAT3, RETAIN_PARENT, url44.com
+, CAT2, CUSTOM, url45.com
+, CAT1, CUSTOM, url46.com
+, CAT10, RETAIN_PARENT, url47.com
+, CAT9, CUSTOM, url48.com
+, CAT8, RETAIN_PARENT, url49.com
+, CAT7, CUSTOM, url50.com
+, CAT6, CUSTOM, url51.com
[]You can use this operation to associate, dissociate, or replace URLs in a category.
Following are the syntax with examples for associating, dissociating, or replacing URLs in a category:
-
Associate a URL to a category.
`+, <category name>, <categorization type>, <url>`
The following example associates the URL, moviesonline.com with the Movies category:
`+, Movies, CUSTOM, moviesonline.com`
-
Associate a URL to a category and also retain it in the parent category.
`+, <category name>, RETAIN_PARENT, <url>`
The following example associates the URL, moviesonline.com with the Movies category and also retains it in its parent category:
`+, Movies, RETAIN_PARENT, moviesonline.com`
-
Dissociate a URL to a category.
`-, <category name>, <categorization type>, <url>`
The following example dissociates the URL, moviesonline.com from the Movies category:
`-, Movies, CUSTOM, moviesonline.com`
-
Dissociate a URL from a category, but retain it in its parent category.
`-, <category name>, RETAIN_PARENT, <url>`
The following example disassociates the URL, moviesonline.com from the Movies category, but retains it in its parent category:
`-, Movies, RETAIN_PARENT, moviesonline.com`
-
Replace the existing set of URLs in a category with a new set of URLs.
`*, <category name>, <categorization type>, <url1>
+, <category name>, <categorization type>, <url2>`
The following example removes all the URLs under the Movies category and adds the URLs, primevideo.com and neflix.com:
`*, Movies, CUSTOM, primevideo.com
+, Movies, RETAIN_PARENT, netflix.com`
To replace URLs in a category, use * to add the first URL instance and + for the subsequent instances under the same category.
[]You can use this operation to delete a custom category. This operation dissociates all the URLs associated to the category and then deletes the category.
-, <category name>
The following example deletes the Movies category after dissociating all the URLs associated with the Movies category:
`-, Movies`
[]You can use the RESET operation to ignore all the previous lines specified in the url_upload file and execute only the operations specified after. This operation can be used when you have to make a few updates to the URLs or categories after a bulk update using the same url_upload file. Though you can use as many RESET operations as you want in a file, only the last instance in the file takes effect.
*, <category name>, <categorization type>, <url1>
+, <category name>, <categorization type>, <url2>
+, <category name>, <categorization type>, <url3>
RESET
-, <category name>, <categorization type>, <url4>
+, <category name>, <categorization type>, <url5>
In the following example, all the operations on URLs before the RESET line are ignored, and only those after the line is executed:
`*, Movies, CUSTOM, primevideo.com
+, Movies, RETAIN_PARENT, netflix.com
RESET
-, Movies, CUSTOM, moviesonline.com
+, Movies, CUSTOM, zee5.com`
[]You can add comments in the URL upload file to provide notes or information on the operations defined in the file. Use # at the beginning of the line where you want to add your comments.
# <comments.>
For example:
`#`
[]To manage custom URLs and categories using the Bulk URL Upload Tool:
- Ensure that you have the following resources on your system before running the Bulk URL Upload tool:
- JAVA Runtime (JRE) version 8 or higher.
- An API config file, which contains the `BASE_URI`, `API_KEY`, `USERNAME` (Optional), `UPLOAD_CSV_FILE` (Optional).
- A URL upload file, which is a CSV file that contains operations on URLs and URL categories.
-
Run the following command to execute the Bulk URL Upload tool:
java -jar urlupload.jar
A prompt to enter the path of the API config file appears.
Please provide Path To API Config File:
-
Enter the API config file path to initiate a connection with the API server.
A prompt to enter the username of the API server appears.
Please Enter your Username:
-
Enter the username of the API server. If the username is defined in the API config file, then the username is auto-populated.
A prompt to enter the password appears.
Please Enter your Password:
-
Enter the password.
A prompt to enter the path of the URL upload file appears after a connection with the server is established.
Please Provide Path To The File Containing Custom Urls To Upload:
-
Enter the URL upload file path to execute the operations defined in the URL upload file. If the URL upload file path is defined in the API config file, then the URL upload file path is auto-populated.
The Bulk URL Upload tool initiates the uploading of contents from the URL upload file.
Uploading Contents from File:
The output of the Bulk URL Upload tool is displayed.
A sample output of the Bulk URL Upload tool is as follows:
Uploading Contents from File : upload_files/urls.csv
Added Category Successfully: CAT5
Added Category Successfully: CAT4
Added Category Successfully: CAT3
Added Category Successfully: CAT2
Added Category Successfully: CAT1
Added Category Successfully: CAT10
Added Category Successfully: CAT9
Added Category Successfully: CAT8
Added Category Successfully: CAT7
Added Category Successfully: CAT6
Operation Completed
Activation Successful
Session Closed
Alternatively, you can also directly run the following command to execute the URL upload file using the tool:
java -jar urlupload.jar -c <API Config File Path> -f <url Upload CSV>
This command overrides the URL upload file path in the API config file.
You will be prompted to enter the credentials of the API server.
The output of the Bulk URL Upload tool is displayed.
[]You may encounter any of the following error messages while running the Bulk URL Upload tool. The following table lists the reason and resolution for each error message:
| Exit Status | Error Message | Reason | Resolution |
| ----------- | ------------- | ------ | ---------- |
| 1 | `***ERROR*** : Failed To Establish Authenticated Channel With Server` | This error occurs due to a server error or incorrect credentials. | Retry after some time or provide correct credentials. |
| 2 | `***ERROR*** : Failed To Fetch URL CATEGORIES` | This error occurs when the GET request fails to retrieve the existing categories. | Retry after some time. |
| 3, 5 | `***ERROR*** : Invalid Operation => <LINE>``Please use one of the two formats:``1. All url related : <OPERATION,CATEGORY,CLASSIFICATION,URL> ->``Ex: +,CAT9,CUSTOM,.youtube.com OR A,CAT9,CUSTOM,.youtube.com``2. Delete Category : <-,CATEGORY> -> Ex: -,CAT9 OR``<D,CATEGORY> -> Ex: D,CAT9` | This error occurs when there is an invalid operation.For example, adding a new category without any URL associated with it or deleting a category that doesn't exist.i.e., +, <category> or -, <category that doesn't exist>. | Remove the invalid line.A new category can be added only if a URL is associated with it. |
| 6 | `***ERROR*** : Wrong Format...Please use one of the two formats:``1. All url related : <OPERATION,CATEGORY,CLASSIFICATION,URL> ->``Ex: +,CAT9,CUSTOM,.youtube.com OR A,CAT9,CUSTOM,.youtube.com``2. Delete Category : <-,CATEGORY> -> Ex: -,CAT9 OR <D,CATEGORY> ->``Ex: D,CAT9` | This error occurs when there is a wrong format in the CSV file. | Check the format in the CSV file and correct it. |
| 7 | `***ERROR*** : <filename> Not Found...` | This error occurs if there is an incorrect file path specified. | Provide the correct file path. |
| 8 | `<JAVA IO EXCEPTION ERROR>` | This error occurs when there is an error in reading the file. | Check permissions or contact Zscaler Support. |
| 9 | `***ERROR*** : Failed To Add Category : <CategoryName>` | This error occurs when there is a failure during POST while adding a new category. | Contact Zscaler Support. |
| 10 | `***ERROR*** : Failed To Modify Category : <CategoryName>` | This error occurs when there is a failure during PUT while modifying a category. | Contact Zscaler Support. |
| 11 | `***ERROR*** : Failed To Delete Category : <CategoryName>` | This error occurs when there is a failure to delete a category. | Contact Zscaler Support. |
| 12 | `***ERROR*** : Failed To Close Established Authenticated Channel With Server` | This error occurs when there is a failure to close the session. | No intervention required. |
| 13, 14 | `***ERROR*** : Unknown Classification in <LINE>``Please use RETAIN_PARENT/CUSTOM` | This error occurs when there is an incorrect categorization type. | Provide the correct categorization type in the line.i.e., either CUSTOM or RETAIN_PARENT. |
| 15 | `***ERROR*** : Expected JSON Response for GET. Exiting...` | This error occurs when the response from the server is not in JSON format. | Try again or contact Zscaler Support. |
| 16 | `***ERROR*** : Expected JSON Response for POST. Exiting...` | This error occurs when the response from the server is not in JSON format. | Try again or contact Zscaler Support. |
| 17 | `***ERROR*** : Expected JSON Response for PUT. Exiting...` | This error occurs when the response from the server is not in JSON format. | Try again or contact Zscaler Support. |
| 18 | `***ERROR*** : Expected JSON Response for DELETE. Exiting...` | This error occurs when the response from the server is not in JSON format. | Try again or contact Zscaler Support. |
| 19 | `***ERROR*** : No Input Provided` | This error occurs when the user prompt is empty. For example, when CTRL+C is pressed on prompt. | Enter suitable information in the prompt. |
| 20 | `***ERROR*** : Please Specify BASE_URI, API_KEY, USERNAME(OPTIONAL), UPLOAD_CSV_FILE(OPTIONAL) in API Config file...``Ex:``BASE_URI=admin.zscaler.net/api/v1``API_KEY=lSomeapikeyl``USERNAME=admin@org.com``UPLOAD_CSV_FILE=upload_file/urls.csv` | This error occurs when the API config file does not have a proper format. | Edit the API config file and use a properly formatted file. |
| 21 | `***ERROR*** : Couldn't get Console instance` | This error occurs when the program needs to run on a console, and could not find a console object. | Run it on a console. For example, Command Prompt for windows. |