# Supported Data Stores and File Types
Source: https://help.zscaler.com/dspm/supported-data-stores-and-file-types
PDF: https://help.zscaler.com/pdf/com/en/1498686.pdf

DSPM supports the scanning of AWS, Azure, GCP data stores (storage services, virtual machines, and their associated disks and databases), and on-premises databases for sensitive data, vulnerabilities, and misconfigurations. To learn more, see [About Scan Settings](/dspm/about-scan-settings).
AWS Data Stores
The following AWS data stores are supported:
- Simple Storage Service (S3)
- AWS EC2 Instances
- RDS Instance and Clusters (MySQL, PostgreSQL, Aurora MySQL, Aurora PostgreSQL)
- NoSQL Data Stores (DynamoDB tables)
- Unmanaged MS-SQL Server Databases
- Unmanaged PostgreSQL Databases
- Unmanaged Oracle Databases
- Unmanaged MySQL Databases
- Amazon Bedrock Knowledge Bases
-
AWS Bedrock Custom Model
-
AWS Bedrock Imported Model
-
AWS Databricks
Azure Data Stores
The following Azure data stores are supported:
- Storage accounts and associated containers (Blobs)
- Azure Virtual Machines
- SQL Databases and Servers
- PostgreSQL Flexible Server
- Unmanaged MS SQL Server Databases
- Unmanaged PostgreSQL Databases
- Unmanaged Oracle Databases
- Unmanaged MySQL Databases
- Azure Databricks
- Azure AI Foundry
- Azure AI Foundry Hub
- Azure OpenAI
GCP Data Stores
The following GCP data stores are supported:
- GCP Storage Buckets
- GCP Cloud SQL (SQL, MySQL and PostgreSQL)
- Google Compute Engine (VM)
Snowflake Databases
Snowflake is considered as a dedicated cloud service provider, and support is available for its databases.
On-Premises Databases
The following on-premises datastores are supported:
- MS-SQL
- PostgreSQL
- Oracle
- MySQL
- On-Premises File Server
Supported File Types
DSPM scans the following file types in storage services and virtual machines, but not in databases:
| File Type | File Extension |
| --------- | -------------- |
| Apple iWork | `.keynote`, `.numbers`, `.pages` |
| Archive | `.7z`, `.bz2`, `.gz`, `.rar`, `.rar5`, `.tar`, `.zip` |
| Code/Scripts | `.au3`, `.bat`, `.c`, `.cc`, `.cmd`, `.cpp`, `.cs`, `.go`, `.h`, `.hh`, `.hpp`, `.hta`, `.inc`, `.j`, `.java`, `.js`, `.m`, `.pl`, `.pm`, `.ps1`, `.py`, `.rb`, `.sh`, `.sql`, `.swift`, `.vb`, `.vbs`, `.wsc`, `.wsf`, `.wsh` |
| Data/Configuration | `.csv`, `.dat`, `.json`, `.xml`, `.yaml`, `.yml` |
| Documents | `.bas`, `.doc`, `.docm`, `.docx`, `.dotm`, `.dotx`, `.pdf`, `.rtf`, `.txt` |
| Email | `.eml`, `.emlx`, `.msg` |
| Excel | `.xlam`, `.xls`, `.xlsb`, `.xlsm`, `.xlsx`, `.xltm` |
| HTML | `.html` |
| Images | `.vdx`, `.vsd`, `.vsdm`, `.vsdx`, `.vss`, `.vssm`, `.vssx`, `.vst`, `.vstm`, `.vstx` |
| Installer | `.msi` |
| Java-related | `.jar`, `.java` |
| Log files | `.log` |
| Makefiles | `.mak`, `.mk` |
| Microsoft Access | `.mdb` |
| PowerPoint | `.potm`, `.potx`, `.ppam`, `.pps`, `.ppsm`, `.ppsx`, `.ppt`, `.pptm`, `.pptx` |
| Tableau | `.tbm`, `.tds`, `.tdsx`, `.twb`, `.twbx` |
| UI/Markup | `.xaml` |
| Others | `.xampp` |
Malware-Prone File Types
The following file types are considered more susceptible to malware and security threats due to their executable nature or ability to embed harmful scripts:
- [Archive Files](#archive-files)
- [Executable Files](#executable)
- [Microsoft Office Files](#office)
- [Source Codes](#source)
- [Web Content](#web)
- [Other Files](#other)
[]
| File Type | File Extension |
| --------- | -------------- |
| Archive | `.zip` |
| `.rar` |
| `.rar5` |
| `.tar` |
| `.bz2` |
| `.7z` |
| `.jar` |
[]
| File Type | File Extension |
| --------- | -------------- |
| Bash Script | `.sh` |
| MSC Files | `.msc` |
| Python Files | `.py` |
| Visual Basic Script | `.vbs` |
| Windows PowerShell Script | `.ps1` |
[]
| File Type | File Extension |
| --------- | -------------- |
| Microsoft Excel | `.xls` |
| `.xlsx` |
| `.xlsm` |
| `.xlam` |
| `.xltm` |
| `.xlsb` |
| Microsoft MDB | `.mdb` |
| Microsoft Outlook Message | `.msg` |
| Microsoft PowerPoint | `.ppt` |
| `.pptx` |
| `.pptm` |
| `.ppsx` |
| `.ppam` |
| `.potm` |
| `.potx` |
| `.ppsm` |
| Microsoft RTF | `.rtf` |
| Microsoft Visio | `.vsd` |
| `.vsdx` |
| `.vsdm` |
| `.vss` |
| `.vst` |
| `.vssx` |
| `.vstx` |
| `.vssm` |
| `.vstm` |
| `.vdx` |
| Microsoft Word | `.doc` |
| `.docx` |
| `.docm` |
| `.dotx` |
| `.dotm` |
[]
| File Type | File Extension |
| --------- | -------------- |
| Assembly File | `.asm` |
| AU3 Files | `.au3` |
| Basic Source Code | `.bas` |
| C Files | `.c` |
| `.h` |
| `.cc` |
| `.hh` |
| `.cs` |
| `.cpp` |
| `.hpp` |
| `.hxx` |
| GO Files | `.go` |
| Included Files | `.inc` |
| Java | `.java` |
| `.j` |
| `.java` |
| Make Files | `.mak` |
| `.mk` |
| Perl | `.pl` |
| `.pm` |
| Ruby | `.rb` |
| Visual Basic | `.vb` |
| XAML | `.xaml` |
| YAML | `.yaml` |
| `.yml` |
[]
| File Type | File Extension |
| --------- | -------------- |
| JavaScript | `.js` |
| `.js` |
[]
| File Type | File Extension |
| --------- | -------------- |
| Apple Documents | `.keynote` |
| `.pages` |
| `.numbers` |
| CSV File | `.csv` |
| DAT File | `.dat` |
| EML Files | `.eml` |
| `.emlx` |
| JSON Files | `.json` |
| Log File | `.log` |
| Portable Document File | `.pdf` |
| Tableau | `.twb` |
| `.twbx` |
| `.tbm` |
| `.tdsx` |
| `.tds` |
| Text | `.txt` |
| XML | `.xml` |
| HTML | `.html` |
| Windows Script | `.wsc` |
| Other Microsoft File | `.wsf` |
| `.wsh` |