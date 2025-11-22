# Understanding Data Classification
Source: https://help.zscaler.com/dspm/understanding-data-classification
PDF: https://help.zscaler.com/pdf/com/en/1474711.pdf

Data classification describes the process of identifying and categorizing sensitive data based on predefined criteria such as the level of sensitivity, level of risk, etc. Organizing the sensitive data and [creating an inventory](/dspm/about-resource-inventory) based on its severity level and impact helps you implement effective data governance, security controls (encryption, principle of least privilege, etc.) and regulatory compliance as per [International Standards Organization (ISO)](https://www.iso.org/home.html), [General Data Protection Regulation (GDPR)](https://gdpr.eu/tag/gdpr/), [Health Insurance Portability and Accountability Act (HIPAA)](https://www.hhs.gov/hipaa/index.html), [Payment Card Industry Data Security Standard (PCI DSS)](https://www.pcisecuritystandards.org/), [California Consumer Privacy Act (CCPA)](https://oag.ca.gov/privacy/ccpa) and other data protection or data privacy regulations. This process is crucial for protecting data, quickly resolving any issues, and minimizing the risk of unauthorized access or data loss that could lead to financial and business implications.
DSPM uses predefined [DLP engines and dictionaries](/dspm/about-dlp-engines-and-dictionaries) for data classification and offers visibility into what type of sensitive data is stored in your cloud resources, the region where the data is stored, the files containing sensitive data, the severity of risk associated with the sensitive data, etc. Some of the common sensitive data categories include personally identifiable information (PII), health records, financial records, credit card numbers, government records, etc. To learn more, see [About Resource Inventory](/dspm/about-resource-inventory).
Data classification includes the following benefits and enables you to:
- Know what type of data is stored in your cloud resources.
- Know in which region this data is located.
- Know the users, roles, or services that are authorized to access the data.
- Know how the data is stored and managed.
- Evaluate the severity of risk associated with the data and prioritize remediation.
- Implement compliance regulations and internal controls for data governance.
Document Categories and Subcategories
The DLP engine running in DSPM automatically classifies each document (file) using the following ML categories and subcategories:
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
-
-
-
-
| Document Category | Subcategory |
| ----------------- | ----------- |
| DMV | Vehicle Registration and Titling DocumentsDriver's License DocumentsVehicle Inspection and Emissions Testing DocumentsCommercial Driver and Vehicle DocumentationDriver History and Compliance RecordsViolation, Fee, and Payment DocumentsSpecial Permits and Temporary DocumentationPublic Records and Information Requests |
| Financial | Invoices and Expense ReportsFinancial Governance and Compliance GuideFinancial StatementsManagement ReportsInvestment and Financial PlanningLoan and Financing DocumentsTax Documents |
| HR | Applicant and Employee RecordsPolicy and Procedure DocumentsPerformance Management DocumentsRecruitment DocumentsEmployee Relations DocumentsCompensation and Benefits DocumentsCompliance and Legal Documents |
| Immigration | Citizenship and Naturalization DocumentsVisa DocumentsFamily and Dependent Immigration DocumentsTravel and Entry DocumentsWork Authorization and Employment DocumentsResidency and Green Card DocumentsAsylum and Refugee DocumentsImmigration Fee and Payment DocumentsImmigration Appeal and Review DocumentsDeportation and Removal Documents |
| Insurance | Business Insurance DocumentsMedical Insurance DocumentsAuto Insurance DocumentsReal Estate Insurance DocumentsLife Insurance Documents |
| Legal | Miscellaneous Legal DocumentsCorporate DocumentsCourt DocumentsIntellectual Property DocumentsContracts and AgreementsFamily Law DocumentsEstate Planning DocumentsRegulatory and Compliance Documents |
| Medical | Legal and Regulatory DocumentsResearch and Clinical Trial DocumentsAdministrative DocumentsPatient Medical RecordsTherapy and Rehabilitation RecordsLaboratory and Diagnostic ReportsPrescriptions and Medication RecordsClinical DocumentsEmergency and Critical Care Documents |
| Medical Imaging | SchematicsSatellite ImagesID Cards |
| Real Estate | Lease and Rental DocumentsPurchase and Sale DocumentsProperty Ownership DocumentsMaintenance and Property Management DocumentsFinancing Documents |
| Source Code | CC++C#DartGoHTMLJavaJavaScriptKotlinPerlPHPPowerShellPythonRubyRustShellSQLSwiftTypeScript |
| Technical | Technical Specifications and Design DocumentsStandard Operating Procedures (SOPs) and Maintenance GuidesProject DocumentationTechnical Reports and ProposalsTraining MaterialsCompliance and Regulatory DocumentsUser Manuals and GuidesAPI and Release Documentation |