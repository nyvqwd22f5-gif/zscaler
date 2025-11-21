# Connecting AnySource
Source: https://help.zscaler.com/uvm/connecting-anysource
PDF: https://help.zscaler.com/pdf/com/en/1528226.pdf

When [creating a data source](/uvm/creating-data-sources) to ingest data into the platform, you can either use a dedicated vendor connector, or you can use the AnySource connector. The AnySource connector allows you to upload files directly to the platform. Uploaded files are stored in their original format and can be mapped to the platform's data model. Each source maintains a consistent field mapping, so all files uploaded to a given source should match the structure of the original file (e.g., headers, file type).
To set up the AnySource connector:
- Go to **Configure** > **Sources**.
- Click **Create**.
- Search for and select **AnySource** from the tiles.
- On the **Create AnySource Source** page, in the **Retrieval** section, select a file upload method:
- [Upload File](#uploading-files)
- [AWS S3](#aws-s3-method)
- [GCP](#gcp-method)
- [Webhook](#webhook-method)
- [Upload File API](#upload-file-api-method)
To complete the AnySource connector setup, including Remediation Detection Settings and Suppression Rules, see [Creating Data Sources](/uvm/creating-data-sources).
[]Manually upload a file by dragging and dropping it into the designated area, or selecting it from your local folders. The following file formats are supported for upload: JSON, JSONL, CSV, XLSX, ZIP, XML, ZST, ZSTD.
After your file is uploaded, the **Parser Type **drop-down menu appears.
[See image.](#parser-type)
In most cases, Zscaler recommends selecting **Auto **to automatically detect the file type and parse it accordingly.
If you require more granular control over how the file is parsed, or if the Auto parser does not correctly identify the file type, you can manually select the appropriate Parser Type based on your file's format.
The following parser types are available:
- [JSONL](#jsonl-parser)
- [JSON](#json-parser)
- [CSV](#csv-parser)
- [Excel](#excel-parser)
- [XML](#xml-parser)
- [PYTHON_STREAM](#python-stream-parser)
File Size Limit
Uploaded files must not exceed 50 MB. If your file is larger than this limit, consider the following options:
- Compress the file using one of the supported formats (i.e., ZIP, GZIP, or ZSTD) to reduce its size to within the 50 MB limit.
- Use a file storage service (e.g., AWS S3) to upload the file. This method is recommended for files that cannot be compressed to meet the 50 MB size requirement.
[]![anysource upload file method parser type dropdown](/downloads/uvm/administration/connectors/sources/source-configuration-guides/connecting-anysource/anysource%20upload%20file%20parser%20types.png)
[]No additional configuration is required.
[]You can enter a Root Json Path to access specific data elements. The Root Json Path uses JSONPath expressions. To learn more, refer to the [Overview of JSONPath Expressions](https://www.rfc-editor.org/rfc/rfc9535#name-overview-of-jsonpath-expres).
[]To configure the CSV parser, you must enter the **Delimiter **(e.g., comma, period, pipe) used in the file.
You can also enter a **Quote Character**, which can be any character. The double quote (") is the standard and most commonly used in CSV files.
[]To configure the Excel parser, enter the **Sheet Name **from which the data should be extracted. You can enter the exact name of the sheet, or you can use a wildcard (i.e., an asterisk `*`) to dynamically select the sheet name.
Using only the wildcard extracts the first sheet from the Excel file. You can combine the wildcard with a pattern to extract sheets with a recurring name format. For example, entering `pen_test*` retrieves the first sheet that begins with `pen_test`, regardless of any characters that follow.
Select the **Use first sheet as default **checkbox to return the first sheet if the specified sheet name is not found. If this option is left unchecked and the specified sheet does not exist, an error occurs and no data is retrieved.
[]You can enter the Root XPath to access specific elements within the XML structure. To learn more, refer to the [XPath Syntax guide](https://www.w3schools.com/xml/xpath_syntax.asp).
[]The PYTHON_STREAM parser allows you to configure custom data manipulations and parsing logic necessary for accurately and optimally mapping data.
A common use case is exploding a single row in the ingested data into multiple rows in the transformed data. For example, you can explode a single row that contains multiple CVEs in a column into separate rows of CVEs that can then be mapped to individual findings.
The following functions are available:
- `parse_to_json()`: The primary function where you must implement your custom parsing logic. It is mandatory to define all parsing and output logic within this function for the parser to function correctly.
- `AvalorInputStream()`: Provides access to the uploaded file via the PYTHON_STREAM parser. This function supports two key methods for reading file content:
- `read()`: Reads the entire content of the uploaded file in a single operation and returns it as a single string.
- `readline()`: Reads a single line from the uploaded file and returns it as a string.
- `output_writer.write(json_formatted_string)`: A method used to write rows of data into the platform using the PYTHON_STREAM parser. Accepts a JSON-formatted string as its input.
The following is an example script for parsing files using the PYTHON_STREAM parser:
`import json
def parse_to_json():
# Open input stream for reading
with AvalorInputStream() as inputstream:
line = inputstream.readline()  # Read the first line
while line:
# Assume each line contains a JSON array of CVEs
cve_list = json.loads(line.strip())  # Parse JSON array
# Write each CVE back to output, one at a time, as a JSON string
for cve in cve_list:
output_writer.write(json.dumps(cve))  # Write as JSON without
newline
line = inputstream.readline()  # Read the next line`
[]The platform supports integration with your AWS S3 buckets to automatically extract data as new files are added. When a file is uploaded to a designated bucket, the platform is notified and retrieves the file for processing. To learn more, see [Connecting AnySource Using AWS S3](/uvm/connecting-anysource-using-aws-s3).
[]The platform supports integration with your GCP Cloud Storage buckets to automatically extract data as new files are added. When a file is uploaded to a designated bucket, the platform is notified and retrieves the file for processing.
[]To use a webhook for retrieving data, select the **Push **option from the **Method **drop-down menu. This is a REST API call that receives the data as part of the body. Each source has its own unique webhook ID that is part of the URL.
[See image.](#webhook-url-account-id-webhook-id)
The following is an example API call, including the payload:
curl --location 'https://webhook.avalor.io/inlinedata/<Account ID>/<Unique Webhook ID>' \
--header 'Content-Type: text/plain' \
--data-raw '[{
"field1": false,
"field2": "text",
"field3": [
"item1",
"item2"
]
}]'
File Size Limit
Uploaded files must not exceed 6 MB. If your file is larger than this limit, consider the following options:
- Compress the file using one of the supported formats (i.e., ZIP, GZIP, or ZSTD) to reduce its size to within the 6 MB limit.
- Use a file storage service (e.g., AWS S3) to upload the file. This method is recommended for files that cannot be compressed to meet the 6 MB size requirement.
[]![anysource%20webhook%20push%20method%20.png](/downloads/uvm/configure/sources/connecting-anysource/anysource%20webhook%20push%20method%20.png)
[]The Upload File API allows you to programmatically upload a file to an AnySource data source instance via API.
Prerequisites
The Upload File API method uses token-based authentication using client credentials. To authenticate API requests, you must first obtain client credentials (client ID and client secret) from your platform representative or the SecOps platform support team.
Using the API
To make an API call, you must first generate a token, which is then used to authenticate the request.
Generating a Token
Using your client ID and client secret, access the `oauth2/token` endpoint to generate a token. The token is valid for one hour only.
Replace the following details in the command below:
- `<URL>`
- For **US**: `https://auth.us01.app.avalor.io/oauth2/token`
- For **EU**: `https://auth.eu.app.avalor.io/oauth2/token`
- `<Client ID>`: Your client ID
- `<Client Secret>`: Your client secret
curl --location '<URL>' \
--header 'accept: application/json' \
--header 'content-type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=Client Credentials' \
--data-urlencode 'client_id=<Client ID>' \
--data-urlencode 'client_secret=<Client Secret>'
Making the API Request
The following is an example API call, including the payload:
curl --request POST \
--url 'https://api.region.app.avalor.io/api/webserver/data-source-instance/upload?processDsiId=<Data Source Instance ID>' \
--header 'accountid: <Account ID>' \
--header 'authorization: <Token>' \
--header 'content-type: multipart/form-data' \
--form 'multipartFile=@<File Name>'
Fields to Include in the AnySource File
When ingesting data through the AnySource connector, it's important to include specific fields to enable effective data unification (i.e., entity resolution and data normalization) within the platform's unified data model. To learn more, see [What Is Data Unification?](/uvm/what-data-unification)
Unlike vendor-specific API connectors (e.g., CrowdStrike Managed Hosts, ServiceNow Assets), which automatically extract the necessary fields based on predefined integration logic, the AnySource connector requires you to explicitly determine which fields to include. For example, when uploading a data file manually, you can choose to include the appropriate fields directly in the file. In other cases, such as using the Upload File API, field selection is typically handled through the parsing logic you define.
Best Practices for Field Selection
To ensure ingested data is usable in downstream processes (e.g., normalization, enrichment, correlation, and analytics), follow these best practices when selecting fields:
- Include core identifiers: Always export key attributes for each entity to support correlation across data sources (e.g., ID or unique key, name or title, and timestamps like first seen and last seen).
- Add contextual data: Supplement core fields with additional attributes that provide business, operational, or technical context (e.g., asset type, operating system, business unit, owner, location, or tags).
When possible, export a detailed version of the data to facilitate more accurate mapping and merging across different sources.
The ingestion layer is designed to support a wide variety of file formats and structural variations, so preprocessing (e.g., data cleaning, reformatting) is generally not required, as the system can interpret and normalize diverse input structures during parsing.
Recommended Fields (by Entity Type)
Each entity type (e.g., assets, vulnerabilities) has its own set of core recommended fields. The following examples are the key fields typically associated with assets and vulnerabilities.
Assets
| **Attribute** | **Description** |
| ------------- | --------------- |
| Asset Name/Hostname | The name or hostname of the asset |
| Asset Type | The type of asset (e.g., server, workstation) |
| External or Internal IP Address | The IP addresses associated with the asset |
| Operating System | The operating system running on the asset |
| Asset Owner | The individual or department responsible for the asset |
| Location | The physical or logical location of the asset |
| Asset Status | The status of the asset (e.g., active, decommissioned) |
| Asset Tags | The asset tags, if available. Tags can contain valuable business information. |
| Software Installed | A list of installed software and software versions |
| Asset Criticality | The importance of the asset to the organization (e.g., critical, non-critical) |
Findings
| **Attribute** | **Description** |
| ------------- | --------------- |
| Vulnerability Name/ID | The name or unique identifier for the vulnerability |
| Severity Score/CVSS/Scanner Score | The severity score assigned to the vulnerability, including the numerical score (8.1) and the category (High) |
| Description | A detailed description of the vulnerability and impact |
| Affected Asset | Information about the asset or system with the vulnerability |
| CVE | The CVE identifier, if available |
| Threat Intel Information | Threat intel parameters provided by the vendor |
| Tags | Vulnerability tags, if available. Tags can contain valuable business information. |
| Timestamps | The First Seen and Last Seen fields that state when the vulnerability was first and last discovered or reported |
| Recommendations/Fix | Recommended actions for vulnerability remediation |
| Affected Component | Information about the affected component (i.e. Java, Windows), if available |