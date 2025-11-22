# About DLP Engines
Source: https://help.zscaler.com/unified/about-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1493131.pdf

A DLP engine is a collection of one or more [DLP dictionaries](/unified/about-dlp-dictionaries). When you define your [DLP policy rules](/unified/configuring-dlp-policy-rules-content-inspection) and [Endpoint DLP policy rules](/unified/configuring-endpoint-dlp-policy-rules), you must reference DLP engines, rather than DLP dictionaries. By using a DLP engine, you can create rules to detect content that encompasses more than one dictionary. For example, if your organization wants to protect social security and credit card numbers, create a rule using an engine that contains the Credit Cards and Social Security Numbers dictionaries.
The Zscaler service provides predefined DLP engines and supports custom DLP engines. You can [edit predefined engines](/unified/editing-predefined-dlp-engines), [create custom engines](/unified/adding-custom-dlp-engines), or [clone existing engines](/unified/cloning-dlp-engines) to detect content that is relevant to your organization. When configuring a predefined or custom engine, you can also combine dictionaries with Boolean operators to create logical expressions. To learn more, see [Understanding DLP Engines](/unified/understanding-dlp-engines).
DLP engines provide the following benefits and allow you to:
- Use a collection of DLP dictionaries to define DLP policy rules.
- Create rules to detect content that encompasses more than one dictionary.
- Use Zscaler's predefined DLP engines, or create your own custom DLP engines.
Zscaler DLP engines can scan files with a maximum size of 400 MB. For an archived file, the size of individual files when decompressed can also be a maximum of 100 MB. DLP engines can scan up to 5 levels of compression.
About the DLP Engines Page
On the DLP Engines page (Policies > Data Protection > Common Resources > Dictionaries & Engines > DLP Engines), you can do the following:
- [Add a custom DLP engine.](/unified/adding-custom-dlp-engines)
- View a list of all DLP engines that were configured for your organization. For DLP engines, you can see:
- **Name**: The name of the DLP engine. You can sort this column.
- **Dictionaries**: The DLP dictionaries included in the engine.
- **Description**: The description of the engine, if available. You can sort this column.
- [Edit](/unified/editing-predefined-dlp-engines) or [clone](/unified/cloning-dlp-engines) a DLP engine.
- [Modify the table and its columns.](/unified/using-tables)
- Search for a DLP engine.
- Go to the [DLP Dictionaries](/unified/about-dlp-dictionaries) page, to view, modify, or add DLP dictionaries.
![DLP Engines page within the Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/about-dlp-engines/ZIA-dlp-engines-page-tasks-with-cloning.png)