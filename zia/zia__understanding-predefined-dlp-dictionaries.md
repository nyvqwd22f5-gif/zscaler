# Understanding Predefined DLP Dictionaries
Source: https://help.zscaler.com/zia/understanding-predefined-dlp-dictionaries
PDF: https://help.zscaler.com/pdf/com/en/1447026.pdf

Zscaler provides the following Data Loss Prevention (DLP) dictionaries. Dictionaries marked with an asterisk (*) are *not *supported for Endpoint DLP. To learn more, see [About Endpoint DLP](/zia/about-endpoint-dlp). To learn more about configuring predefined DLP dictionaries, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
- [Aadhaar Card Number (India)](#aadhaar)
- [ABA Bank Routing Numbers](#ABA)
- [Addresses (Japan)*](#Addresses-Japan)
- [Adult Content](#Adult)
- [Australia Passport Number](#AustraliaPassport)
- [Bulgaria Uniform Civil Number](#BulgariaUniformCN)
- [Citizen Service Numbers (Netherlands)](#CitizenServiceNums)
- [CNPJ Number (Brazil)](#CNPJ-Brazil)
- [Corporate Finance Document](#corporate-finance-document)
- [Corporate Legal Document](#corporate-legal-document)
- [Corporate Number (Japan)](#CorporateNumberJapan)
- [Court Document](#court-document)
- [Credentials and Secrets](#CredentialsAndSecrets)
- [Credit Cards](#Credit)
- [Diseases Information](#DiseasesInformation)
- [Driver’s License (United States)](#USDriversLicense)
- [Drugs Information](#DrugsInformation)
- [Enhanced Driver's License (United States)](#EnhancedUSDriversLicense)
- [Financial Statements](#Finance)
- [First Names (Japan)*](#FirstName-Japan)
- [Fiscal Code (Italy)](#Fiscal-Code-Italy)
- [Full Names (Japan)*](#FullNames-Japan)
- [Gambling](#Gambling)
- [ID Card](#IDCard)
- [Identity Card Number (China)](#IDCardNumChina)
- [Identity Card Number (Hong Kong)](#Hong-Kong-Identity-Card)
- [Identity Card Number (Malaysia)](#MalaysiaIDNumber)
- [Identity Card Number (Thailand)](#ThailandIDNumber)
- [Illegal Drugs](#Drugs)
- [Immigration Document](#immigration-document)
- [Individual Taxpayer Registry ID (Brazil)](#Natural)
- [Insurance Document](#insurance-document)
- [International Bank Account Number (IBAN)*](#IBAN)
- [Invoice Document](#invoice-document)
- [Last Names (Japan)*](#LastNames-Japan)
- [Legal Document](#legal-document)
- [Medical Document](#medical-document)
- [Medical Imaging](#MedicalImaging)
- [Medical Information](#Medical)
- [Medicare Numbers (Australia)](#MedicareNumAustralia)
- [Mexico Unique Population Registration Code](#MexicoPopRegCode)
- [My Number (Japan)](#MyNumberJapan)
- [National Document ID (Uruguay)*](#NDID-Uruguay)
- [Names (Canada)](#names-canada)
- [Names (Spain)](#names-spain)
- [Names (US)](#Name-US)
- [National Economic Registry Number (Poland)](#PolandEconRegistryNumber)
- [National Health Index Number (New Zealand)](#NationalHealthIndex-NZ)
- [National Health Service Number (UK)](#NHS)
- [National Identification Card Number (Taiwan)](#NatIDCardNumTaiwan)
- [National Identification Number (Chile)*](#NIN-Chile-RUN)
- [National Identification Number (France)](#NatIDNumFrance)
- [National Identification Number (Poland)](#PolishIDNumber)
- [National Identification Number (Spain)](#NatIDNumSpain)
- [National Insurance Number (UK)](#National)
- [National Provider Identifier](#NationalProviderID)
- [NDC Number (Package)](#NDC-Package)
- [NDC Number (Product)](#NDC-Product)
- [NRIC Numbers (Singapore)](#NRIC)
- [Passport Number (Asia)*](#Asia-PassportNumber)
- [Passport Number (European Union)](#EU-PassportNumber)
- [Personal Identification Number (Croatia)](#PIN-Croatia)
- [Real Estate Document](#real-estate-document)
- [Resident Registration Number (Korea)](#RRN)
- [Resume Document](#resume-document)
- [Salesforce.com Data](#Salesforce)
- [Satellite Data](#SatelliteData)
- [Schematic Data](#SchematicData)
- [Self-Harm & Cyberbullying](#self-harm-cyberbullying)
- [Social Insurance Numbers (Canada)](#SIN)
- [Social Security Number (Austria)](#AustriaSSN)
- [Social Security Number (Spain)](#SocialSecurityNumberSpain)
- [Social Security Number (Switzerland)](#Swiss-SSN)
- [Social Security Numbers (US)](#SSN)
- [Source Code](#Source)
- [Standardized Bank Code (Mexico)](#CLABE)
- [Tax Document](#tax-document)
- [Tax File Numbers (Australia)](#TaxFileNumAustralia)
- [Tax Identification Number (Austria)](#AustriaTaxID)
- [Tax Identification Number (Belgium)](#BelgiumTaxID)
- [Tax Identification Number (Denmark)](#DenmarkTaxID)
- [Tax Identification Number (Finland)](#FinlandTaxID)
- [Tax Identification Number (France)](#FranceTaxID)
- [Tax Identification Number (Germany)](#GermanyTaxID)
- [Tax Identification Number (Greece)](#GreeceTaxID)
- [Tax Identification Number (Hungary)](#HungaryTaxID)
- [Tax Identification Number (Indonesia)](#IndonesiaTaxID)
- [Tax Identification Number (Ireland)](#IrelandTaxID)
- [Tax Identification Number (Luxembourg)](#LuxembourgTaxID)
- [Tax Identification Number (New Zealand)](#NewZealandTaxID)
- [Tax Identification Number (Peru)](#PeruTaxID)
- [Tax Identification Number (Poland)](#PolandTaxID)
- [Tax Identification Number (Portugal)](#PortugalTaxID)
- [Tax Identification Number (Spain)](#SpainTaxID)
- [Tax Identification Number (Sweden)](#SwedenTaxID)
- [Tax Identification Number (US)](#USTaxID)
- [Technical Document](#technical-document)
- [Transportation and Motor Department Document](#transportation-motor-department)
- [Treatments Information](#TreatmentsInformation)
- [Unique Identification Code (Peru)*](#DNI-Peru)
- [Unique Master Citizen Number](#UniqueMasterCitNumber)
- [VAT Number (Austria)](#AustriaVAT)
- [VAT Number (Belgium)](#BelgiumVAT)
- [VAT Number (France)](#FranceVAT)
- [VAT Number (Germany)](#GermanyVAT)
- [VAT Number (Ireland)](#IrelandVAT)
- [VAT Number (Luxembourg)](#LuxembourgVAT)
- [VAT Number (Netherlands)](#NetherlandsVAT)
- [Weapons](#Weapons)
[]This dictionary detects Aadhaar Unique Identification (UID) numbers from India.
The popular format for an Aadhaar UID number is a 12-digit number, separated at the 4th and 8th digits by a delimiter. The delimiter can be a period, hyphen, or space.
The following are examples of popular formats:
- NNNNNNNNNNNN
- NNNN-NNNN-NNNN
This dictionary uses the *Verhoeff *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Aadhaar UID number matches a valid range.The Aadhaar UID number can contain:A period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.An alphabetical boundary. | The number formats that can trigger the dictionary are:Q2161 6729 3627O8384-2795-9970A number format like 2@075-8515-612d5 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Aadhaar UID number is in a popular format.The Aadhaar UID number can contain a non-alphanumeric boundary. It cannot be bound by alphabetical characters.The Aadhaar UID number must use the same delimiters for the full number. | The number formats that can trigger the dictionary are:@216167293627@8384-2795-9970The number formats that do not trigger the dictionary are:2075-8515/6125F838427959970B |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Aadhaar UID number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Aadhaar Card*, *UID*, or *UIDAI number.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:@216167293627@8384-2795-9970The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:2075-8515/6125F838427959970B |
[]This dictionary detects ABA routing transit numbers from the United States.
The popular format for an ABA routing transit number is a 9-digit number that has no delimiters.
An example of a popular format is NNNNNNNNN.
This dictionary uses the *Luhn *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the ABA routing transit number matches a valid range.The ABA routing transit number can contain a period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed. | The number formats that can trigger the dictionary are:021---302---567053 9021 97QQ036001808//011...600...033The number formats that do not trigger the dictionary are:50dd86d97067aa8543210bb74 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The ABA routing transit number is in a popular format.The ABA routing transit number can not contain a period, hyphen, or space as delimiters. No delimiters are allowed. | The number formats that can trigger the dictionary are:053902197036001808011600033The number formats that do not trigger the dictionary are:021---302---56750dd86d97067aa8543210bb74 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The ABA routing transit number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *aba routing number,* *aba number*, *american bank association routing number*, *bank routing number*, or *routing transit number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:021302567053902197036001808011600033The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:50dd86d97067aa8543210bb74 |
[]
This dictionary is disabled by default. To access this feature, contact your Zscaler Account team.
This dictionary detects content related to addresses from Japan.
This dictionary does not use a checksum.
The following are examples of acceptable formats for Japanese Addresses:
- 〒064-0807 北海道札幌市中央区南七条西２ー４ー４ (full address with hyphen as delimiter)
- 〒064-0807 北海道札幌市中央区南七条西２丁目４番４号 (full address with kanji]
- 札幌市中央区南七条西2の4の4 (postal code optional)
- 札幌市中央区南七条西2丁目4-4 (postal code is optional)
- 新宿区高田馬場1-7-2 (postal code and prefecture are optional)
- 新宿区高田馬場1丁目7の2 (postal code and prefecture are optional)
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects adult or mature content.
The popular format for adult or mature content is sexually explicit keywords, as well as foul language words.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
[]This dictionary detects passport numbers (AUPP) from Australia.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the AUPP number matches a valid range. | Number formats that trigger the dictionary:N1234567NN123456N 1234567The number formats that do not trigger the dictionary are:N12345 67Q1234567 (invalid first letter)PG123456 (invalid letter combination) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The AUPP number is in a popular format. | A number format like N1234567 or NN123456 triggers the dictionary.The number formats that do not trigger the dictionary are:N 1234567N12345 67PA123-456 (delimiter in wrong place) |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The AUPP number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *passport, passport number, passportno*,* passport num*,* immigration and citizenship*,* issuing authority*,* national identity card*,* passport details*,* *and *travel document.* | A number format like N1234567 or NN123456 triggers the dictionary.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:N 1234567N12345 67PG 123456 |
[]This dictionary detects uniform civil numbers (EGN) from Bulgaria.
This dictionary uses the *Modulo 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the EGN number matches a valid range. | The number formats that can trigger the dictionary are:752 316 92637 -52/.316 926...- 3A number format like 7523169264 (invalid checksum) will not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The EGN number is in a popular format. | A number format like 7523169263 triggers the dictionary.The number formats that do not trigger the dictionary are:752 316 92637 -52/.316 926...- 3 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The EGN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *bucn*, *egn*, *vim*, *uniform civil number*, and *unified civil number*. | A number format like 7523169263 triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:752 316 92637 -52/.316 926...- 3 |
[]This dictionary detects citizen service numbers (BSN) from the Netherlands.
The popular format for a citizen service number is a 9-digit number that can be separated by a hyphen after 3 digits.
An example of a popular format is NNNNNNNNN.
This dictionary uses the *Mod 11 Check Digit *checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the citizen service number matches a valid range. | The number formats that can trigger the dictionary are:132...24077409619543525 86627002444--52155041143401 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The citizen service number is in a popular format. | The number formats that can trigger the dictionary are:096195435@244452155@041143401The number formats that do not trigger the dictionary are:132...24077425 8662700 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The citizen service number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Citizen service number*, *BSN*, *Burgersservicenumber*, *Sofinummer*, *Persoonsgebonden nummer*, *Persoonsnummer*, or *Personal Number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:096195435@244452155@041143401The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:132...24077425 8662700 |
[]This dictionary detects the 14-digit Brazilian National Registry of Legal Entities (CNPJ) number.
This dictionary uses the *Mod 11 *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the CNPJ number matches a valid range. | The number formats that can trigger the dictionary are:44 455 566 0001 8844.455/5660001...8844 -455/ .566 0001...-88A number format like 44455566000185 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The CNPJ number is in a popular format. | A number format like 44.455.566/0001-88 triggers the dictionary.The number formats that do not trigger the dictionary are:4445556600018844 455 566 0001 8844 -455/ .566 0001...-8844.455.566/0001 88 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The CNPJ number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *CNPJ*, *Cadastro Nacional da Pessoa Jurídica*, *National Registry of Legal Entities*, and *CNPJ#*. | A number format like 44.455.566/0001-88 triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:4445556600018844 455 566 0001 8844 -455/ .566 0001...-8844.455.566/0001 88 |
[]This dictionary detects Corporate Numbers from Japan.
You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence):
- Low: The dictionary counts an instance as a violation if it matches a valid range.
- Medium: The dictionary counts an instance as a violation if:
- The requirements of Low Confidence are met.
- The Corporate Number is in a popular format.
- High: The dictionary counts an instance as a violation if:
- The requirements of Medium Confidence are met.
- The Corporate Number is accompanied by any of the dictionary’s default or custom high confidence phrases.
[]This dictionary detects corporate finance documents, like earnings reports, Form 10-K, etc.
Zscaler supports only the following document types for corporate finance documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a supported corporate finance document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects corporate legal documents, like LLC operational agreements, Secretary of State forms, etc.
Zscaler supports only the following document types for corporate legal documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a supported corporate legal document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects court documents, like attorney forms, witness subpoenas, etc.
Zscaler supports only the following document types for court documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a supported court document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary allows you to select one or more credentials and secrets dictionaries (i.e., tokens, keys, passwords, etc.) for the following:
- Amazon MWS Auth Token
- Git Token
- GitHub Token
- Google API Key
- Google OAuth Access Token
- Google OAuth ID
- JWT Token
- PayPal Braintree Access Token
- Picatic API Key
- Private Key
- SendGrid API Key
- Slack Access Token
- Slack Webhook
- Square Access Token
- Square OAuth Secret
- Stripe API Key
[See image.](#CredentialsAndSecrets_Screenshot)
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Medium** | This dictionary counts an instance as a violation if any of the selected sensitive credentials and secrets are matched. |
| **High** | This dictionary counts an instance as a violation if any of the selected sensitive credentials and secrets are matched with a custom high confidence phrase.If you set the Confidence Score Threshold to High, you must specify at least one Custom High Confidence Phrase. |
[]![The Selection Options for the Credentials and Secrets DLP Dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-CredentialsAndSecrets.png)
[]This dictionary detects content related to credit card numbers.
When you add the Credit Cards dictionary to a DLP engine, you must configure the match count. To learn more, see [Configuring the Match Count](/zia/understanding-dlp-engines#match-count).
[See image.](#DLP-Engine-CC-Match-Count)
The popular format for a credit card number is a range from 12-19 numeric digits, separated after every 4 digits by a delimiter that is checked for similarity and is correctly spaced. The delimiter can be a slash, period, hyphen, or space.
The following are examples of popular formats:
- AMEX (15 digits)
- NNNN<delimiter>NNNNNN<delimiter>NNNNN
- Diner's Club (14 digits)
- NNNN<delimiter>NNNNNN<delimiter>NNNN
- Other Credit Cards (16 digits)
- NNNN<delimiter>NNNN<delimiter>NNNN<delimiter>NNNN
- NNNN NNNN NNNN NNNN
This dictionary uses the *Luhn *checksum.
To use this dictionary to detect credit card numbers, the following guidelines apply:
These guidelines might not apply to certain use cases. You can adjust your dictionary configurations according to your DLP needs.
- To catch a small exfiltration of numbers in documents:
- Set a **Confidence Score Threshold** of **High** for the dictionary.
- When adding a dictionary to an engine, set a low value for the dictionary's match count.
- To catch a large exfiltration of numbers in spreadsheets or other file types:
- Set a **Confidence Score Threshold** of **Medium** for the dictionary.
- When adding a dictionary to an engine, set a high value for the dictionary’s match count.
- In general, configuring a dictionary with a **Low Confidence Score Threshold** and a low match count value results in too many false positives. Zscaler recommends setting a **Confidence Score Threshold** of **High** when its match count value is low.
- Rich Text Format (RTF) files contain formatting code that can mimic credit card and social security numbers, affecting when a DLP rule is triggered. Plain text files do not contain this formatting code, therefore the DLP rule triggers as expected. So that the DLP policy triggers if confidential numbers are leaked in RTF files, do one of the following steps:
- Set any value greater than **1** for the dictionary’s match count in the engine.
- Set a **Confidence Score Threshold** value of **High**.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if:The credit card number matches the length of at least one provider.The credit card number can be validated by Luhn checksum.The credit card number can contain a period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed. | The number formats that can trigger the dictionary are:491-6710478214413491-67...104782 1441347 1697--47625799...2136839-32 977351853721 653983--865084716 7361 13842732 (Valid length and can be validated by Luhn checksum)The number formats that do not trigger the dictionary are:aa5269946762375011aa4716 7361 1384 2731 (Cannot be validated by the Luhn checksum) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The credit card number is in a popular format.The credit card number, the length, and starting range of the number match that of the credit card providers.The credit card number must use the same delimiters for the full number. Plus, the delimiters must be equally spaced. | The number formats that can trigger the dictionary are:4716-9747-6257-992153721653983865084716 7361 1384 2732The number formats that do not trigger the dictionary are:4916:7104-7821 441349167-104-7821-4413a3683:9329:773-518a |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The credit card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Amex*, *MasterCard*, *Visa*, *CVV Code*, *CCV Number*, *select card type*, *Discover*, *Diners Club*, *jcb*, *pay with checking account*, *pay check money order*, *credit card number*, *card holder name*, or *expiration date*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:4716-9747-6257-99215269:9467:6237:501153721653983865084716 7361 1384 2732A number like a3683:9329:773-518a does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
If a violation is enough to trigger a DLP policy and you have configured a [DLP email notification](/zia/about-dlp-notification-templates), your auditors receive an email. If you have also included the ${DLPTRIGGERS} macro, the email includes what content triggered the violation.
[See image.](#DLP-Violation-Notification)
[]This dictionary uses phrase matching to detect content related to diseases information. It does not use a checksum.
You can specify an Action to configure how the dictionary evaluates matching disease names:
- **Count All**: The dictionary counts all matches of the disease name, including identical disease names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the disease name toward the match count only once, regardless of how many times the disease name appears.
[]![The Match Count for the Credit Cards DLP Dictionary](/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/ZIA_Add_DLP_Rule_Credit_Cards_Match_Count.png)
[]![Screenshot of a DLP email notification](/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/zia-dlp-example-notification-low.png)
[]This dictionary allows you to select driver's license dictionaries for one or more of the 50 U.S. states plus the District of Columbia.
[See image.](#USDL_Screenshot)
This legacy dictionary has been replaced, but not deprecated, by the [Enhanced Driver's License (United States)](#EnhancedUSDriversLicense-note) predefined dictionary, which allows you to customize sub-dictionaries for each of the 50 U.S. states, plus the District of Columbia.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Medium** | This dictionary counts an instance as a violation if the selected driver's license is matched. |
| **High** | The requirements of Medium Confidence are met and the driver's license is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Driver's License, Driver's License number, DL#, 2-letter state codes (e.g., CA for California or WA for Washington).* |
The **Proximity Length** field appears when the dictionary’s Confidence Score Threshold is High. The proximity length defines how close a high confidence phrase must be to an instance of the pattern (that the dictionary detects) to count as a match. The phrase can be located in any direction from the pattern within the document. Enter a value from 0–10,000 bytes. A proximity length of 0 disables this option (i.e., the phrase can be any distance from the pattern).
[]![The Selection Options for the United States Driver's License DLP Dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-US_DriversLicense.png)
[]This dictionary uses phrase matching to detect content related to drug information. It does not use a checksum.
You can specify an Action to configure how the dictionary evaluates matching drug names:
- **Count All**: The dictionary counts all matches of the drug name, including identical drug names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the drug name toward the match count only once, regardless of how many times the drug name appears.
[][]This dictionary allows you to select driver's license dictionaries for one or more of the 50 U.S. states, plus the District of Columbia. Additionally, you can set the Confidence Score Threshold, Proximity Length, and Custom High Confidence Phrases for each state sub-dictionary.
[See image.](#Enhanced-USDL_Screenshot)
The following table lists the confidence score threshold criteria for this dictionary, using the Alabama and Alaska sub-dictionaries as an example. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
-
-
-
-
-
-
-
-
-
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Medium** | This dictionary counts an instance as a violation if the selected state's driver's license number is matched. | For an engine that uses the Alabama and Alaska sub-dictionaries with Medium Confidence Score:1234567 triggers both sub-dictionaries12345678 triggers the Alabama sub-dictionary only |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The driver's license number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Drivers License, Drivers License Number, DL#*,* *and *State *name* *(i.e., *Alabama, Alaska*, etc.)* *for the corresponding sub-dictionary*.* | For an engine that uses the Alabama and Alaska sub-dictionaries with High Confidence Score:1234567 does not trigger either sub-dictionaryDriver's License 1234567 triggers both sub-dictionariesDriver's License 12345678 triggers the Alabama sub-dictionary onlyAlabama 1234567 triggers the Alabama sub-dictionary onlyAlaska 1234567 triggers the Alaska sub-dictionary only |
[]![The Selection Options for the Alabama Driver's License DLP Sub-dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-US_EnhancedDriversLicense.png)
[]This dictionary detects content related to financial statements. It detects a financial document based on machine learning which clusters keywords that typically occur in financial documents. Examples of keywords are *Accounts Payable*, *Common Stock*, *Current Liabilities*, and so on.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold.](/zia/editing-predefined-dlp-dictionaries#confidence)
[]This dictionary detects content related to First Names from Japan.
This dictionary does not use a checksum.
The following are examples of acceptable formats for Japanese First Names:
- 三郎
- 清子
- 美代子
- 四郎
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects Italian fiscal codes from Italy.
The popular format for an Italian fiscal code is a 16-character alphanumeric code that has no delimiters.
An example of a popular format is FFF-NNN-YYMDD-RRRRC. It has the following structure:
- FFF: Represents the first three letters of the last name.
- NNN: Represents the first three letters of the first name.
- YYMDD: Represents the date of birth.
- YY: Represents the year.
- M: Represents the month. It is represented by a letter that maps to a month.
- DD: Represents the date.
- RRRR: Represents the town of birth. It is represented by alphnumeric characters.
- C: Represents the checksum value. It is represented by a letter.
This dictionary uses the *Mod 26 Check Digit* checksum (maps to a letter A-Z).
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The Fiscal Code (Italy) dictionary is a regex based dictionary. It is more strict in formatting, even in low confidence. The special characters must be in the right positions. There could be a mix of different special characters, and there may even be consecutive special characters at the right positions, but they cannot be in the wrong positions.The dictionary counts an instance as a violation if the Italian fiscal code matches a valid range.The Italian fiscal code can contain only a period, hyphen, or space as delimiters. Multiple periods are allowed for a low confidence score. | The number formats that can trigger the dictionary are:RSS MRA 70A41 F205ZKAYSAN92D03L246ARSS MRA- ... 70A41F205ZKAYSAN 92D03L246 ... AThe number formats that do not trigger the dictionary are:RSS MRA70A41F20 5ZKAYSAN9 2D03L246A |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Italian fiscal code is in a popular format. | The number formats that can trigger the dictionary are:RSS MRA 70A41 F205ZKAYSAN92D03L246AThe number formats that do not trigger the dictionary are:RSS MRA- ... 70A41F205ZKAYSAN 92D03L246 ... A |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Italian fiscal code is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *codice fiscal, repubblica italiana, Italian fiscal code, *or* Italian tax code.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:RSS MRA 70A41 F205ZKAYSAN92D03L246AThe number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:RSS MRA- ... 70A41F205ZKAYSAN 92D03L246 ... A |
[]This dictionary detects content related to Full Names from Japan.
This dictionary does not use a checksum.
For example, if the First Name is 富市, and the Last Name is 村山, the following are examples of acceptable formats for Japanese Full Names:
- 村山富市 (no delimiters)
- 村山 富市 (spaces as delimiter)
- 村山　富市 (unicode space as delimiter)
- 村山,富市 (ASCII comma as delimiter)
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects content related to gambling. It detects documents that have keywords related to both online and physical gambling and betting.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold.](/zia/editing-predefined-dlp-dictionaries#confidence)
[]This dictionary detect images of ID Cards, such as licenses and passports.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects Resident Identity Card numbers from China.
The popular format for a Resident Identity Card number is an 18-character number, but the last character can either be a digit or the character *X* (case insensitive).
The following are examples of popular formats:
- NNNNNNNNNNNNNNNNNX
- NNNNNNNNNNNNNNNNNN
This dictionary uses the *Mod 11 Check Digit* checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Resident Identity Card number matches a valid range. | The number formats that can trigger the dictionary are:36--2331198--00322524X3607 2719830115027X3425011992...07064058A number format like 1404011998vv05055835 does not trigger the dictionary. It contains alphabetical characters. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Resident Identity Card number is in a popular format. | The number formats that can trigger the dictionary are:36072719830115027X342501199207064058The number formats that do not trigger the dictionary are:a36233119800322524X (Starts with a character)a1404011998vv05055835 (Starts with a character) |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Resident Identity Card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Chinese identity card number.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:36233119800322524X36072719830115027X342501199207064058140401199805055835 |
[]This dictionary detects Hong Kong identity card (HKID) numbers from Hong Kong.
The popular format for an HKID number is 8 or 9 alphanumeric characters without delimiters. It starts with either one or two alphabet letters, followed by 6 random digits, and ends with a checksum character that must be enclosed in parentheses. The checksum character can be either a digit or the letter "A" (case insensitive). For example, P553722(7), MR427885(6), and FK057839(A).
This dictionary uses the *Mod 11 Check Digit* checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the HKID number matches a valid range.HKID is a regex-based dictionary, and is strict in formatting, even in low confidence. No special characters are allowed other than parentheses.If the parentheses are not balanced, it does not trigger the dictionary. There can be only a single pair of parentheses. Nested parentheses do not trigger the dictionary. | The number formats that can trigger the dictionary are:P553722(7)P553722(A)The number formats that do not trigger the dictionary are:P5537227P553722-7-P553722(7P5537227)P553722((7)) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The HKID number is in a popular format. | The number format that can trigger the dictionary is P553722(7).The number format that does not trigger the dictionary is P5537227. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The HKID number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Hong Kong Identity Card, HKIC, HKID, Identity Card, or Hong Kong Permanent Resident ID Card.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:P553722(7)P553722(A) |
[]This dictionary detects National Identity Card (MyKad) numbers from Malaysia.
The popular format for a MyKad number is a 12-digit number. The first group of numbers is the date of birth (YYMMDD). The second group of numbers (SS) represents the place of birth of the holder: the states (01-13), the federal territories (14-16), or the country of origin (60-85). The last group of numbers (###G) is a serial number in an unidentified pattern which is randomly generated. The last digit (G) is an odd number for a male and an even number for a female.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the MyKad number matches a valid range. | The number formats that can trigger the dictionary are:13...0125281813261231129312170 726145727@240921167814@16022--5148988A number format like 1007192dd33724 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The MyKad number is in a popular format. | The number formats that can trigger the dictionary are:261231129312@240921167814@The number formats that do not trigger the dictionary are:13...0125281813170 72614572716022--5148988A100719233724A |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The MyKad number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *mykad, Malaysian nric, or mypr.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:261231129312@240921167814@100719233724The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:13...0125281813170 72614572716022--5148988 |
[]This dictionary detects National Identification (PESEL) numbers from Poland.
The popular format for a PESEL number is an 11-digit number. The PESEL number has the form of YYMMDDZZZXQ, where YYMMDD is the date of birth (with century encoded in month field), ZZZX is the personal identification number where X codes the sex (even number for females and odd number for males), and Q is a check digit which is used to verify whether a given PESEL is correct or not.
This dictionary uses the *Luhn* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the PESEL number matches a valid range. | The number formats that can trigger the dictionary are:.14.1017...04491-82-12270--5195-971 0050 7364The number formats that do not trigger the dictionary are:2302130d3028(55111304237) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The PESEL number is in a popular format. | The number formats that can trigger the dictionary are:97100507364@23021303028$The number formats that do not trigger the dictionary are:.14.1017...04491-82-12270--5195-A55111304237G |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The PESEL number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *pesel liczba *or* peselliczba*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:141017044918212270519597100507364@23021303028$55111304237 |
[]This dictionary detects National Identity Card numbers from Thailand.
The popular format for a National Identity Card number is a 13-digit string in the format of N-NNNN-NNNNN-NN-N. In the Popular Format Checking process, it checks for 4 delimiters.
This dictionary uses the *Luhn* *variation* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the National Identity Card number matches a valid range.The National Identity Card number can contain only a period, hyphen, or space as delimiters. | The number formats that can trigger the dictionary are:@9082208241537@1-1964-43062-03-25-40 42-291 43-14-981614275771913-5887-693...20-66-7A number format like 070ww7389561584 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The National Identity Card number is in a popular format. | The number formats that can trigger the dictionary are:@9082208241537@1-1964-43062-03-28161427577191The number formats that do not trigger the dictionary are:070ww73895615845-40 42-291 43-14-93-5887-693...20-66-7 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The National Identity Card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *thailand identity card number*, *thailand national*,* date issue*,* or date expiry*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:@9082208241537@1-1964-43062-03-28161427577191The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:07ss073895615845-4042-291cc43-14-9 |
[]This dictionary detects content related to illegal drugs. It detects the names of illegal drugs such as Cocaine, Heroin, Ketamine, and so on.
This dictionary does not use a checksum.
You can modify the** **Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
[]This dictionary detects immigration documents, like passport renewal forms, I-485, I-856, I-907, etc.
Zscaler supports only the following document types for immigration documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from an immigration document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects Individual Taxpayer Registry ID numbers (CPF) from Brazil. If you use an Exact Data Match (EDM) Index Template to try and detect a CPF number, the format ddd.ddd.ddd-dd does not work because '.' (period) is an EDM delimiter. However, if you include this dictionary in a rule, the format ddd.ddd.ddd-dd is detected.
The popular format for an Individual Taxpayer Registry ID number is different for individuals versus legal persons. For individuals, it is an 11-digit number with the last two numbers being the result of an arithmetic operation from the 9 previous ones. For legal persons, it is a 14-digit string formatted as XX.XXX.XXX/XXXX-XX. The first 8 digits identify the company, the four digits after the slash identify the branch or subsidiary, and the last 2 digits are the result of an arithmetic operation from the previous ones.
This dictionary uses the *Mod 11 Check Digit* checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Individual Taxpayer Registry ID number matches a valid range.The Individual Taxpayer Registry ID number can contain:A period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.An alphabetical boundary. | The number formats that can trigger the dictionary are:088.258.987-38103.015.819-32The number formats that do not trigger the dictionary are:989.786.5232-27286.648.5a71-80345.543.66@5-02 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Individual Taxpayer Registry ID number is in a popular format.The Individual Taxpayer Registry number can contain a non-alphanumeric boundary. It cannot be bound by alphabetical characters. | The number formats that can trigger the dictionary are:286.648.571-80088.258.987-38@345.543.665-02@103.015.819-32A number format like 989.786.523-2--7 does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Individual Taxpayer Registry ID number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Natural Persons Register *or* Registration Number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:286.648.571-80088.258.987-38@345.543.665-02@103.015.819-32A number format like 989.786.523-2--7 does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
[]This dictionary detects insurance documents, like employee insurance, home insurance, commercial insurance, medical insurance, etc.
Zscaler supports only the following document types for insurance documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from an insurance document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary allows you to select IBAN dictionaries for one or more of the following countries:
- Andorra (AD)
- Austria (AT)
- Bosnia (BA)
- Belgium (BE)
- Bulgaria (BG)
- Switzerland (CH)
- Cyprus (CY)
- Czechia (CZ)
- Germany (DE)
- Denmark (DK)
- Estonia (EE)
- Spain (ES)
- Finland (FI)
- Faroe Islands (FO)
- France (FR)
- United Kingdom (GB)
- Gibraltar (GI)
- Greenland (GL)
- Greece (GR)
- Croatia (HR)
- Hungary (HU)
- Ireland (IE)
- Israel (IL)
- Iceland (IS)
- Italy (IT)
- Liechtenstein (LI)
- Lithuania (LT)
- Luxembourg (LU)
- Latvia (LV)
- Monaco (MC)
- Montenegro (ME)
- Malta (MT)
- Netherlands (NL)
- North Macedonia (MK)
- Norway (NO)
- Poland (PL)
- Portugal (PT)
- Romania (RO)
- Serbia (RS)
- Sweden (SE)
- Slovenia (SI)
- Slovakia (SK)
- San Marino (SM)
- Tunisia (TN)
- Turkey (TR)
[See image.](#IBAN_Screenshot)
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Medium** | This dictionary counts an instance as a violation if any of the selected IBAN numbers are matched. |
| **High** | This dictionary counts an instance as a violation if any of the selected IBAN numbers are matched by any of the dictionary’s default or custom high confidence phrases. |
[]![The Selection Options for the International Bank Account Number (IBAN) DLP Dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-IBAN-Dictionary.png)
[]This dictionary detects invoice documents, like Bill of Sale forms, purchase orders, etc.
Zscaler supports only the following document types for invoice documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a supported invoice document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects content related to Last Names from Japan.
This dictionary does not use a checksum.
The following are examples of acceptable formats for Japanese Last Names:
- 村山
- 佐久間
- 平山
- 五十嵐
- 佐藤
- 鈴木
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects legal documents, like living wills, name change certificates, etc.
Zscaler supports only the following document types for legal documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a legal document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects medical documents, like medical consent forms, HIPAA forms, medical record forms, etc.
Zscaler supports only the following document types for medical documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a medical document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects instances of medical imaging, such as x-rays and scans.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects content related to medical information. It detects the drug and disease names based on the ICD 10 code.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
[]This dictionary detects Medicare numbers from Australia.
The popular format for a Medicare number is an 11-digit number. In the Popular Format Checking process, the Mod 10 checksum is performed and the number has to pass the checksum.
This dictionary uses the *Mod 10 *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Medicare number matches a valid range. | The number formats that can trigger the dictionary are:@6014812406@59...89916...49739--388984 01A number format like 24//2877813//2 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Medicare number is in a popular format. | The number formats that can trigger the dictionary are:@6014812406@59899164973938898401A number format like A2428778132B does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Medicare number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *bank account details*, *medicare payments*, *mortgage account*, *bank payments*, *information branch*, *credit card loan*, *department human services*, *medicare*, or *medi care*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:@6014812406@59899164973938898401A number format like A2428778132B does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
[]This dictionary detects Mexico Unique Population Registration Code numbers.
This dictionary uses the *Mod 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Mexico Unique Population Registration Code number matches a valid range. | The number formats that can trigger the dictionary are:HEGG.560427MVZRRL04HEGG 560427MVZRRL04HEGG-560427MVZRRL04HEGG.- 560427MVZRRL04HEGG560427 MVZRRL04HEGG560427.MVZRRL04HEGG560427-MVZRRL04HEGG560427 -MVZRRL04HEGG 560427-MVZRRL04The number formats that do not trigger the dictionary are:HEGG560427MVZRRL03 (bad checksum)HE GG560427MVZRRL04 (unpopular format; doesn't match regex)HEGG560427MVZRRL 04 (unpopular format; doesn't match regex)HE GG 560427 MVZRRL 04 (unpopular format; doesn't match regex) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Mexico Unique Population Registration Code number is in a popular format. | The number formats that can trigger the dictionary are:HEGG560427MVZRRL04hEGG560427MVZRRL04hegg560427mvzrrl04A number format like HEGG-560427MVZRRL04 does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Mexico Unique Population Registration Code number is accompanied by any of the dictionary’s default high confidence phrases. For example, *Clave Única de Registro de Población*, *CURP*, *clave única*, *ClaveÚnica#*, and *clavepersonalIdentidad#*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:HEGG560427MVZRRL04hEGG560427MVZRRL04hegg560427mvzrrl04A number format like HEGG-560427MVZRRL04 does not trigger the dictionary. |
[]This dictionary detects My Numbers (also referred to as Individual Numbers) from Japan. The popular format for a My Number (Japan) instance is NNNN-NNNN-NNNN or N(12).
This dictionary uses the *Mod 11-2* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/unified/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the My Number occurrence is 12 digits with a valid checksum and does not match any popular format. | The number formats that can trigger the dictionary are:67 56 16 14 81 736756-1614.8173675616148173A number format like 6756 1614 8174 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The My Number instance is in a popular format. | The number formats that can trigger the dictionary are:6756 1614 8173675616148173The number formats that do not trigger the dictionary are:6756-1614.817367 56 16 14 81 73 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The My Number instance is accompanied by any of the dictionary’s default high confidence phrases. For example, *individual number* or *mynumber*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:6756 1614 8173675616148173A number format like 67 56 16 14 81 73 does not trigger the dictionary. |
[]This dictionary detects content related to Uruguay-issued Document ID numbers.
The popular format for a Uruguay-issued Document ID number is a 7- or 8-character ID formatted as NNNNNN-C, NNNNNNN-C, or N.NNN.NNN-C, where N is a number (0 to 9) and C is the verification digit.
This dictionary uses the *MOD 10 *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/unified/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Document ID number matches a valid range.The Document ID number can contain periods or hyphens as delimiters. Multiple periods and hyphens are allowed. | The number formats that can trigger the dictionary are:244984823876157244984-82.387.615-72387615-7 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Document ID number is in a popular format. | The number formats that can trigger the dictionary are:244984-82.387.615-72387615-7The number formats that do not trigger the dictionary are:81234761.234.5672.387.615-7 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Document ID number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Numero de CedulaI Documento de Identidad* or *Cedula de Identidad Uruguaya*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:Numero de CedulaI Documento de Identidad 244984-8Numero de CedulaI Documento de Identidad 2.387.615-7Cedula de Identidad Uruguaya 2387615-7The number formats that do not trigger the dictionary are:244984-82.387.615-72387615-7 |
[]This dictionary detects content related to names from Canada.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | The dictionary counts an instance as a violation if the content contains either a first name or a last name that is in the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if the content contains a first name and last name that is in the dictionary. |
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects content related to names from Spain.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | The dictionary counts an instance as a violation if the content contains either a first name or a last name that is in the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if the content contains a first name and last name that is in the dictionary. |
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects content related to names from the United States. It detects first and last names.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | The dictionary counts an instance as a violation if the content contains either a first name or a last name that is in the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if the content contains a first name and last name that is in the dictionary. |
You can also specify an Action to configure how the dictionary evaluates matching names:
- **Count All**: The dictionary counts all matches of the name, including identical names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the name toward the match count only once, regardless of how many times the name appears.
[]This dictionary detects the 9- or 14-digit Polish National Economic Registry Number (REGON) number.
This dictionary uses the *Mod 11 *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the REGON number matches a valid range. | The number formats that can trigger the dictionary are:13 345678313345678 313 345678-313 34567831234013 34567831234-013 4567831234 /-0A number format like 133456788 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The REGON number is in a popular format. | The number formats that can trigger the dictionary are:13345678313 345678 31334567831234013/34567831234/0The number formats that do not trigger the dictionary are:13 345678313345678 313 345678-313 34567831234013 34567831234-013 4567831234 /-0 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The REGON number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *regon*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:13345678313 345678 31334567831234013/34567831234/0The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:13 345678313345678 313 345678-313 34567831234013 34567831234-013 4567831234 /-0 |
[]This dictionary detects New Zealand National Health Index Numbers (NZNHIN).
NZNHINs have two formats, both of which are undelimited with no special characters in between:
- Old format: `AAANNNC`
- New format: `AAANNAC`
The old format uses *Modulo 11* checksum; the new format uses the *Modulo 24* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the NZNHIN number matches a valid range. | A number format like WLD-9413 can trigger the dictionary.The number formats that do not trigger the dictionary are:WL-D9413 (doesn't match regex)WLD9-413 (doesn't match regex)WLD94-13 (doesn't match regex) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NZNHIN number is in a popular format. | The number formats that can trigger the dictionary are:WLD9413aDh48zjA number format like WLD-9413 does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The NZNHIN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *National Health Index Number*, *National Health Index Num*, *NHI number*, or *NHI#*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:WLD9413aDh48zjA number format like WLD-9413 does not trigger the dictionary. |
[]This dictionary detects National Health Service (NHS) numbers from the United Kingdom.
The popular format for an NHS number is a 10-digit number formatted as NNN <delimiter>NNN<delimiter>NNNN. The delimiters can be a period, hyphen, or space.
This dictionary uses the *Mod 11 Check Digit *checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the NHS number matches a valid range.The NHS number can contain:A period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.An non-alphanumeric boundary. | The number formats that can trigger the dictionary are:566 80183265431043544808619--02265878649888130323...3851 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NHS number is in a popular format.The NHS number can contain a non-alphanumeric boundary. It cannot be bound by alphabetical characters.The NHS number must use the same delimiters for the full number. | The number formats that can trigger the dictionary are:@5878649888@1303233851The number formats that do not trigger the dictionary are:5@668018326543!1043!544A8086190226A |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The NHS number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *NHS Number* or *National Health Services Number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:56680183265431043544A8086190226A@5878649888@1303233851 |
[]This dictionary detects National Identification Card numbers from Taiwan.
The popular format for a National Identification Card number is a 10-digit string that contains one letter and 9 digits. It can also contain a period, hyphen, or space as delimiters.
This dictionary uses the *Luhn* checksum but the leading alphabet letter gets converted to a numerical equivalent.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the National Identification Card number matches a valid range.The National Identification Card number can contain a period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.The National Identification Card number can not contain a delimiter between the first alphabet letter and the next number. | The number formats that can trigger the dictionary are:D146. 665-645--I145639659!!F172388317VVZ258578175DDThe number formats that do not trigger the dictionary are:Z...222063149!!X14234881733 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The National Identification Card number is in a popular format.The National Identification Card number can only have a non-alphanumeric character for the end delimiter. | The number formats that can trigger the dictionary are:I145639659!!X142348817@@Z258578175The number formats that do not trigger the dictionary are:Z...222063149F172388317VV |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The National Identification Card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *taiwanese national identification card number.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:I145639659Z222063149!!X142348817@@Z258578175A number format like F172388317VV does not trigger the dictionary if accompanied by any of the dictionary's default or custom high confidence phrases. |
[]This dictionary detects National Identity Card (RUN) numbers from Chile.
The popular format for a RUN number is an 8- or 9-digit number following the format NNNNNNN-C, NNNNNNNN-C, N.NNN.NNN-C, or NN.NNN.NNN-C, where N is a number (0 to 9) and C is a checksum of a number (0 to 9) or a letter (A to K).
The dictionary uses the *Mod 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/unified/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the RUN number matches a valid range.The RUN number can contain periods or hyphens as delimiters. Multiple periods and hyphens are allowed. | The number formats that can trigger the dictionary are:12.345.678-917.317.684-8The number formats that do not trigger the dictionary are:61410766.141.076 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The RUN number is in a popular format. | The number formats that can trigger the dictionary are:2211011-K6.141.076-76141076-712.450.547-K The number formats that do not trigger the dictionary are:6141076717.317.684-8 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The RUN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *RUN*, *Rol Unico Nacional*, *RUT*, or *Rol Unico Tributario.* | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:RUN 6.141.076-7RUT 17.317.684-8Rol Unico Tributario 12.450.547-kThe number formats that do not trigger the dictionary are:12.345.678123456789-K |
[]This dictionary detects National Institute of Statistics and Economic Studies (INSEE) numbers from France.
The popular format for an INSEE number is a 15-digit number with the first 13 digits and last 2 digits separated by a space.
This dictionary uses the *Mod by 97* checksum. The last two digits are check digits.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the INSEE number matches a valid range.The INSEE number can contain:A period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.An alphabetical boundary. | The number formats that can trigger the dictionary are:@113103115324014@127...1139450--100 58#23--0036713141980# |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The INSEE number is in a popular format.The INSEE number can contain:A non-alphanumeric boundary.Only one space between N(13) and N(2).The INSEE number can not contain a period or a hyphen as a delimiter. | The number formats that can trigger the dictionary are:2430966952225 591160568707959 73%1271139450100 58$#2300367131419 80#The number formats that do not trigger the dictionary are:A138057773213587c113103115324014 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The INSEE number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *insee*, *national id*, *national identification*, *social security number*, *social security code*, and *social insurance number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:2430966952225 591160568707959 73 |
[]This dictionary detects Unique Identification Code (CUI) numbers from Peru.
The popular format for a CUI number is an 8- or 9-digit number using the format NNNNNNNN, NNNNNNNN-C, or NNNNNNNNC, where N is a number (0 to 9) and C is a checksum of either a number (0 to 9) or the letter K.
This dictionary uses the *Mod 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/unified/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the CUI number matches a valid range. The number can be either 8 digits with no checksum or 9 digits with a valid checksum.The CUI number can contain periods or hyphens as delimiters. Multiple periods and hyphens are allowed. | The number formats that can trigger the dictionary are:42388604245004601The number formats that do not trigger the dictionary are:42388604-211234567 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The CUI number is in a popular format.The CUI number is either 8 digits with no checksum or 9 digits with a valid checksum.The CUI number can contain an alphabetical character (A to K) as an ending boundary. | The number formats that can trigger the dictionary are:42388604-324500460-112345678-KThe number formats that do not trigger the dictionary are:4238860412 345 678 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The CUI number is either 8 digits with no checksum or 9 digits with a valid checksum.The CUI number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *CUI*, *Codigo Unico Identificacion*, *DNI*, or *Documento Nacional de Identidad*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:Documento Nacional de Identidad 42388604-3CUI 24500460-1The number formats that do not trigger the dictionary are:DNI 423-886-04245004601123 456 78K |
[]This dictionary detects National Identity Card numbers (DNI) from Spain.
The popular format for a National Identity Card number is a 9-character number with 8 digits and one letter for security.
This dictionary uses the *Mod by 23* checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the National Identity Card number matches a valid range.The National Identity Card number can contain:A period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed.An alphanumeric character as a lead boundary. | The number formats that can trigger the dictionary are:20---222624Na22369319WThe number formats that do not trigger the dictionary are:0 1311947@G33052840-T |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The National Identity Card number is in a popular format.The National Identity Card number can contain an alphabetical character as an ending boundary.The National Identity Card number can not have a delimiter between the last alphabet character and the number. | The number formats that can trigger the dictionary are:01311947G20222624N33052840TA number format like a22369319W does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The National Identity Card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *national identification number*, *national identity number*, *insurance number*, *personal identification number*, *national identity*, *personal identity no*, or *unique identity number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:20222624N22369319W33052840TA number format like d01311947G does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
[]This dictionary detects National Insurance Numbers (NINO) from the United Kingdom.
The popular format for a NINO is a 9-character number. The format of the number is two prefix letters, 6 digits, and one suffix letter. Either of the first two prefix letters cannot be D, F, I, Q, U, or V. The second letter cannot also be O. The prefixes BG, GB, NK, KN, TN, NT, and ZZ are not allocated.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the NINO matches a valid range. | The number formats that can trigger the dictionary are:AA-123456.C@#AA876589C@BB...123456...DA number format like RR65------3456 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NINO is in a popular format. | The number formats that can trigger the dictionary are:AA123456CAA876589CThe number formats that do not trigger the dictionary are:BB123456...DAA-127456.G |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The NINO is accompanied by any of the dictionary’s default high confidence phrases. For example, *national insurance number* or *national insurance*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:AA123465CRK765432CThe number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:rh123456UAA56432D |
[]This dictionary detects National Provider Identifier (NPI) numbers from the United States.
This dictionary uses the *Luhn* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the NPI number matches a valid range. | The number formats that can trigger the dictionary are:123 456 789312.345-6789 31 -23/ .456 78...- 9 3A number format like 1234567894 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NPI number is in a popular format. | A number format like 1234567893 can trigger the dictionary.The number formats that do not trigger the dictionary are:123 456 789312.345-6789 31 -23/ .456 78...- 9 3 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The NPI number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *national provider identifier number*, *national provider identifier*, and *npi*. | A number format like 1234567893 can trigger the dictionary.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:123 456 789312.345-6789 31 -23/ .456 78...- 9 3 |
[]This dictionary detects content related to National Drug Code (NDC) package codes.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if it matches a key in the hash table. | The number formats that can trigger the dictionary are:00020800010990-92573910014001-0899528---606--45The number formats that do not trigger the dictionary are:000-20800-01 (first hyphen at wrong position)0990-925-739 (second hyphen at wrong position)0002-08-00-01 (too many non-adjacent hyphens)99528---6-06--45 (too many non-adjacent hyphens) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NDC package code is in a popular format. | The number formats that can trigger the dictionary are:0002-0800-0110014-001-0886157-0014-1The number formats that do not trigger the dictionary are:00020800010990-92573910014001-0899528---606--45 |
You can also specify an Action to configure how the dictionary evaluates matching package codes:
- **Count All**: The dictionary counts all matches of the package code, including identical codes, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the package code toward the match count only once, regardless of how many times the code appears.
[]This dictionary detects content related to National Drug Code (NDC) product codes.
This dictionary does not use a checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if it matches a key in the hash table. | The number formats that can trigger the dictionary are:000208000990--9257The number formats that do not trigger the dictionary are:000-20800 (hyphen at wrong position)00020-800 (hyphen at wrong position)0990-925-7 (too many non-adjacent hyphens) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NDC package code is in a popular format. | The number formats that can trigger the dictionary are:0002-080010014-00186157-0014The number formats that do not trigger the dictionary are:000208000990--9257 |
You can also specify an Action to configure how the dictionary evaluates matching product code:
- **Count All**: The dictionary counts all matches of the product code, including identical codes, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the product code toward the match count only once, regardless of how many times the code appears.
[]This dictionary detects National Registration Identity Card Numbers (UIN and FIN) from Singapore.
The popular format for a National Registration Identity Card number is a 9-character number that includes 7 digits, with the first character being either S, T, F, or G, and the last character is a checksum calculated with respect to the first letter and the 7 digits.
This dictionary uses the *Mod 11 Check Digit *checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the National Registration Identity Card number matches a valid range.The National Identity Card number can contain a period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed. | The number formats that can trigger the dictionary are:T156--2546AG545...8130RaS8879619EdThe number formats that do not trigger the dictionary are:F2d397111UT0v75 8616C |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The National Registration Identity Card number is in a popular format.The National Registration Identity Card number can not contain any delimiters.The boundary check is not performed for the National Registration Identity Card number as both the start and end have a character. | The number formats that can trigger the dictionary are:T1562546AG5458130RaS8879619EdThe number formats that do not trigger the dictionary are:F2d397111UT0v758616C |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The National Registration Identity Card number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *nric*, *national registration identity card*, *guin*, *fin*, *passport number*, or *birth certificate*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:T1562546AG5458130RF2397111UT0758616CaS8879619Ed |
[]This dictionary allows you to select passport number dictionaries for one or more of the following countries:
- China (CN)
- Japan (JP)
- South Korea (KR)
- Malaysia (MY)
- Philippines (PH)
- Singapore (SG)
- Taiwan (TW)
- Turkey (TR)
[See image.](#Asia-PassportNumber_Screenshot)
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Medium** | This dictionary counts an instance as a violation if any of the selected passport numbers are matched. |
| **High** | This dictionary counts an instance as a violation if any of the selected passport numbers are matched by any of the dictionary’s default or custom high confidence phrases. |
[]![The Selection Options for the Passport Number (Asia) DLP Dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-Asia-Passport-Dictionary.png)
[]This dictionary allows you to select passport number dictionaries for one or more European Union countries.
[See image.](#EUPassport_Screenshot)
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Medium** | This dictionary counts an instance as a violation if the selected country's passport number is matched. |
| **High** | The requirements of Medium Confidence are met and the passport number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Passport, Passport number, passport#.* |
[]This dictionary detects Personal Identification Number (Croatia) numbers.
This dictionary uses the *ISO/IEC 7064, Mod 11,10* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the PIN (Croatia) number matches a valid range. | The number formats that can trigger the dictionary are:hr 94577403194hr.- 12345678911HR..9942692209 6The number formats that do not trigger the dictionary are:HR69435151531 (bad checksum)H R69435151538 (unpopular format; doesn't match regex)HR69435 151538 (unpopular format; doesn't match regex)8684 9310 961 (unpopular format; doesn't match regex) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The PIN (Croatia) number is in a popular format. | The number formats that can trigger the dictionary are:HR69435151531HR 6943515153124631579813The number formats that do not trigger the dictionary are:94 577 403194hr.-12345678911HR69435 151538hr.- 12345678911 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The PIN (Croatia) number is accompanied by any of the dictionary’s default high confidence phrases. For example, *OIB*, *Osobni identifikacijski broj*, and *Personal identification number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:HR69435151531HR 6943515153124631579813The number formats that do not trigger the dictionary are:94 577 403194hr.-12345678911HR69435 151538hr.- 12345678911 |
[]![The Selection Options for the European Union Passport DLP Dictionary](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/understanding-predefined-dlp-dictionaries/ZIA-DLP-EUPassport.png)
[]This dictionary detects real estate documents, like personal or commercial lease agreements, property buying or selling agreements, etc.
Zscaler supports only the following document types for real estate documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a real estate document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects Resident Registration Numbers (RRN) from South Korea.
The popular format for an RRN is a 13-digit number with each digit providing specific information.
This dictionary uses the *Luhn variation *checksum*.*
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the RNN matches a valid range.The RNN can contain:A period, hyphen, or space as delimiters. Multiple periods are allowed.An alphabetical boundary. | The number formats that can trigger the dictionary are:9 70403-2966211780220-1296377#840...719-2145299@D921009-5664079DA number format like 720590-2208919 does not trigger the dictionary because it fails the popular format check. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The RRN is in a popular format.The RRN can contain:A non-alphanumeric boundary.Only a hyphen as a delimiter. | The number formats that can trigger the dictionary are:970403-2966211!780220-1296377@The number formats that do not trigger the dictionary are:720590-2208919#840...719-2145299@D921009-5664079D |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The RNN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *korean resident registration number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:970403-2966211!780220-1296377@890320-1104929840719-2145299921009-5664079940219-5027845 |
[]This dictionary detects resume documents.
Zscaler supports only the following document types for resume documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a resume document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects content related to Salesforce.com data. It detects keywords that are embedded in a Saleforce report, such as Copyright and Saleforce.com.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
[]This dictionary detects images that contain satellite data.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects images of schematic data, such as blueprints.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]The Self-Harm and Cyberbulling dictionary is intended for use by K-12 educators. If you’re an educator, contact your Zscaler Account team to enable this dictionary.
This dictionary detects when students use public search engines to search for self-harm-related content, or when they post bullying-related content on social media.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
[]This dictionary detects Social Insurance Numbers (SIN) from Canada.
The popular format for an SIN is a 9-digit number, separated at the 3rd and 6th digits by a delimiter. The delimiter can be a period, hyphen, or space.
The following are examples of popular formats:
- NNNNNNNNN
- NNN-NNN-NNN
This dictionary uses the *Luhn *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the SIN matches a valid range.The SIN can contain only a period, hyphen, or space as delimiters. Multiple periods, hyphens, and spaces are allowed. | The number formats that can trigger the dictionary are:CC036964 310CC@054120 373$@620301 192%AA021574 728A number format like 650------72...aa...7266 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The SIN is in a popular format.The SIN can contain delimiters only after the 3rd and 6th digits. The delimiters must be the same character. It cannot contain different delimiters.The SIN can have a boundary but the characters immediately before and after the SIN cannot be alphanumeric. | The number formats that can trigger the dictionary are:054120373650-727-266The number formats that do not trigger the dictionary are:@620 301 192AA021574 728650-72.7266 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The SIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *social insurance number* or *national identification number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:036 964 310054120373@620 301 192650-72.7266369 893 144A number format like AA021574 728 does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
[]This dictionary detects Social Security numbers (ATSSN) from Austria.
This dictionary uses the *Modulo 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the ATSSN number matches a valid range. | The number formats that can trigger the dictionary are:123 701 01801237--0101801 -23/.701 -. 0 ... -180A number format like 1238010180 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The ATSSN number is in a popular format. | The number formats that can trigger the dictionary are:12370101801237 010180The number formats that do not trigger the dictionary are:123 701 01801237--0101801 -23/.701 -. 0 ... -180 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The ATSSN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *sozialversicherungsnummer*, *Austria SSN*, *soziale sicherheit kein*, *sozialversicherungsnummer#*, and *sozialesicherheitkein#*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:12370101801237 010180The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:123 701 01801237--0101801 -23/.701 -. 0 ... -180 |
[]This dictionary detects social security numbers from Spain.
You can modify the [Confidence Score Threshold](/zia/editing-predefined-dlp-dictionaries#confidence):
- Low: The dictionary counts an instance as a violation if it matches a valid range.
- Medium: The dictionary counts an instance as a violation if:
- The requirements of Low Confidence are met.
- The social security number is in a popular format.
- High: The dictionary counts an instance as a violation if:
- The requirements of Medium Confidence are met.
- The social security number is accompanied by any of the dictionary’s default or custom high confidence phrases.
[]This dictionary detects social security numbers (AHV) from Switzerland.
The popular format for an AHV number is a 13-digit number. The AHV number has the form of 756.XXXX.XXXX.XY, where 756 is the ISO 3166-1 code for Switzerland, XXXX.XXXX.X is a random number, and Y is an EAN-13 check digit.
This dictionary uses the *Luhn variation *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the AHV number matches a valid range. | The number formats that can trigger the dictionary are:756.52--30.6913.27756.88 85.8748.24756.3594.2833.18@7.56.7811.8967.63@A number format like 756.2...487.40cc93.09 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The AHV number is in a popular format. | The number formats that can trigger the dictionary are:756.3594.2833.18756.2487.4093.09@7.56.7811.8967.63@The number formats that do not trigger the dictionary are:756.52--30.6913.27756.88 85.8748.24 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The AHV number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *identifiant national*, *insurance number*, *national identifier*, *national insurance number*, *AHV number*, *AHV-Nummer*, *Personenidentifikationsnummer*, *Schweizer Registrierungsnummer*, *Swiss registration number*, or *AVS*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:756.3594.2833.18@7.56.7811.8967.63@The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:756.52--30.6913.27756.88 85.8748.24A756.2487.4093.09A |
[]This dictionary detects Social Security Numbers (SSN) from the United States.
When you add the Social Security Numbers (US) dictionary to a DLP engine, you must configure the match count. To learn more, see [Configuring the Match Count](/zia/understanding-dlp-engines#match-count).
[See image.](#DLP-Engine-SSN-Match-Count)
The popular format for an SSN is a 9-digit number.  It can contain periods, hyphens, or spaces as delimiters.
The following are examples of popular formats:
-
- NNNNNNNNN
- NNN-NN-NNNN
- NNN.NN.NNNN
- NNN NN NNNN
This dictionary does not use a checksum.
You can also specify whether to include or exclude specific SSNs. You can configure up to 512 SSNs to include or exclude. To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).
To use this dictionary to detect SSNs, the following guidelines apply:
These guidelines might not apply to certain use cases. You can adjust your dictionary configurations according to your DLP needs.
- To catch a small exfiltration of numbers in documents:
- Set a **Confidence Score Threshold** of **High** for the dictionary.
- When adding a dictionary to an engine, set a low value for the dictionary's match count.
- To catch a large exfiltration of numbers in spreadsheets or other file types:
- Set a **Confidence Score Threshold** of **Medium** for the dictionary.
- When adding a dictionary to an engine, set a high value for the dictionary’s match count.
- In general, configuring a dictionary with a **Low Confidence Score Threshold** and a low match count value results in too many false positives. Zscaler recommends setting a **Confidence Score Threshold** of **High** when its match count value is low.
- Rich Text Format (RTF) files contain formatting code that can mimic credit card and social security numbers, affecting when a DLP rule is triggered. Plain text files do not contain this formatting code, therefore the DLP rule triggers as expected. So that the DLP policy triggers if confidential numbers are leaked in RTF files, do one of the following steps:
- Set any value greater than **1** for the dictionary’s match count in the engine.
- Set a **Confidence Score Threshold** value of **High**.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
- [](https://www.ssa.gov/employer/ssnweb.htm)
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if:The SSN is issued regardless of formatting. You can confirm that the group number is within the range issued for a given area at https://www.ssa.gov/employer/ssnweb.htm.The SSN matches a valid range. | The number formats that can trigger the dictionary are:SA_332831997@@##SA408456050@15...21----587---44---23527 1165...688781663... |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The SSN number is in a popular format. | The number formats that can trigger the dictionary are:SA_332831997@@SA@408456050@...688781663...??292108209//269865658The number formats that do not trigger the dictionary are:15...21----587---44---23527 1165 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The SSN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *date of birth*, *social security number*, or *tax payer*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:SA_332831997@@408456050292108209//269865658The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:15...21----587---44---23527 1165 |
If a violation is enough to trigger a DLP policy and you have configured a [DLP email notification](/zia/about-dlp-notification-templates), your auditors receive an email. If you have also included the ${DLPTRIGGERS} macro, the email includes what content triggered the violation.
[]![The Match Count for the Social Security Numbers (US) DLP Dictionary](/downloads/zia/policies/data-loss-prevention/editing-predefined-dlp-dictionaries/ZIA_Add_DLP_Rule_Social_Security_Numbers_Match_Count.png)
[]This dictionary detects content related to source code. It detects typical source code and programming phrases such as class implements, class extends, and private void.
This dictionary does not trigger unless the data size of the detected content is at least 1 KB.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold.](/zia/editing-predefined-dlp-dictionaries#confidence)
[]This dictionary detects Standardized Bank Code numbers (CLABE) from Mexico.
The popular format for a Standardized Bank Code number is an 18-character number. The Standardized Bank Code number has the following structure:
- 3 digits: Bank Code
- 3 digits: Brach Office Code
- 11 digits: Account Number
- 1 digit: Control Digit
This dictionary uses the *Luhn variation *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Standardized Bank Code number matches a valid range.The Standardized Bank Code number can contain:A period, hyphen, or space as delimiters. Multiple periods are allowed.An alphabetical boundary. | The number formats that can trigger the dictionary are:01402700000555555800201007--777777-7771A number format like 032180aaa000118359719 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Standardized Bank Code number is in a popular format.The Standardized Bank Code number must contain a non-alphanumeric boundary. The starting delimiter and ending delimiter can not be an alphabet. | The number formats that can trigger the dictionary are:014027000005555558002010077777777771A number format like A032180aaa000118359719S does not trigger the dictionary. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Standardized Bank Code number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *CLABE*, *CLABE interbancaria*, or *standardized bank code*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:014027000005555558002010077777777771A number format like @032180aaa000118359719A does not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases. |
[]This dictionary detects tax documents, such as 1040 forms, 1099 forms, 1998-T forms, 3921 forms, etc.
Zscaler supports only the following document types for tax documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a tax document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects Tax File Numbers (TFN) from Australia. The TFN is issued by the Australian Taxation Office (ATO) to each taxpaying entity such as an individual, company, superannuation fund, partnership, or trust.
The popular format for a TFN is a unique 8-digit or 9-digit number.
This dictionary uses the *Mod 11 Check Digit *checksum. This checksum is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the TFN matches a valid range.The TFN can contain a period, hyphen, or space as delimiters. | The number formats that can trigger the dictionary are:371 186 29459 - 599- .-230112.474-08256505160385655805''123456782A number format like 23456782 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The TFN is in a popular format. | The number formats that can trigger the dictionary are:371 186 29d459599230565051603*'123456782The number formats that do not trigger the dictionary are:112.474-082D85655805D |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The TFN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *australian business number*, *marginal tax rate*, *medicare levy*, *portfolio number*, *service veterans*, *withholding tax*, *individual tax return*, or *tax file number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:371 186 29d459599230565051603*'123456782The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:112.474-082D85655805D |
[]This dictionary detects Austrian Tax Identification Numbers (ATTIN), which are 9-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Luhn *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the number matches a valid range. | The number formats that can trigger the dictionary are:93-173-658193/173/658193--173/6581A number format like 931736582 does not trigger the dictionary because it uses an invalid checksum. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The number is in a popular format. | The number formats that can trigger the dictionary are:93173658193-173/6581The number formats that do not trigger the dictionary are:93-173-658193/173/658193--173/6581 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The ATTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *österreich*, *Steuernummer*, *TIN*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:93173658193-173/6581The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:93-173-658193/173/658193--173/6581 |
[]This dictionary detects Belgian Tax Identification Numbers (BTIN), which are 11-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 97* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the BTIN matches a valid range. | The number formats that can trigger the dictionary are:00.0125-111.1900.01.2511.1.480001251111-9The number formats that do not trigger the dictionary are:00.01.25-111.18 (invalid checksum)00.67.25-111.48 (invalid month) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The BTIN is in a popular format. | The number formats that can trigger the dictionary are:00.01.25-111.1900012511119The number formats that do not trigger the dictionary are:00.0125-111.1900.01.2511.1.480001251111-9 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The BTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *belasting aantal*, *numéro d'identification fiscale*, *bnn#*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:00.01.25-111.1900012511119The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:00.0125-111.1900.01.2511.1.480001251111-9 |
[]This dictionary detects Danish Tax Identification Numbers (DTIN), which are 10-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 11* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the DTIN number matches a valid range. | The number formats that can trigger the dictionary are:010-111-111301016011-11A number format like 010111-1116 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The DTIN number is in a popular format. | The number formats that can trigger the dictionary are:010111-11130101601111The number formats that do not trigger the dictionary are:010-111-111301016011-11 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The DTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *centrale personregister*, *civilt registreringssystem*, *cpr*, *cpr#*, *gesundheitskarte nummer*, *gesundheitsversicherungkarte nummer*, *TIN*, *TAX ID*, *skat id*, *skattenummer*, *skat identifikationsnummer*, and* skat kode*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:010-111-111301016011-11The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:010111-11130101601111 |
[]This dictionary detects Finland Tax Identification Numbers (FITIN), which are 10-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Modulo 31* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the FITIN number matches a valid range. | The number formats that can trigger the dictionary are:13 1052-308T1310 52-308T13 10 52-308TThe number formats that do not trigger the dictionary are:131052-308U (bad checksum)131352-3087 (invalid birth month)321052-3082 (invalid birth date) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The FITIN number is in a popular format. | The number formats that can trigger the dictionary are:131052-308T131052+308T131052a308T131052A308TThe number formats that do not trigger the dictionary are:13 1052-308T1310 52-308T13 10 52-308T |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The FITIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Tunnus Kod*, *tunnistenumero*, *tunnus numero*, *tunnusluku*, *tunnusnumero*, and *TIN*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:131052-308T131052+308T131052a308T131052A308TThe number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:13 1052-308T1310 52-308T13 10 52-308T |
[]This dictionary detects French Tax Identification Numbers (FRTIN), which are 13-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 511* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the FRTIN number matches a valid range. | The number formats that can trigger the dictionary are:3 023 217 600 05330--23-217-600-05330 23-217.600/053A number format like 3 023 217 600 054 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The FRTIN number is in a popular format. | The number formats that can trigger the dictionary are:302321760005330 23 217 600 05330-23-217-600-05330.23.217.600.05330/23/217/600/053The number formats that do not trigger the dictionary are:3 023 217 600 05330--23-217-600-05330 23-217.600/053 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The FRTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *tax identification number* and *numéro SPI*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:30 23 217 600 05330-23-217-600-05330.23.217.600.05330/23/217/600/053The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:3 023 217 600 05330--23-217-600-05330 23-217.600/053 |
[]This dictionary detects German Tax Identification Numbers (GTIN), which are 11-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 11* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the GTIN matches a valid range. | The number formats that can trigger the dictionary are:65929 970 48986-095742-719A number format like 65 929 970 480 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The GTIN is in a popular format. | The number formats that can trigger the dictionary are:65 929 970 48965929970489The number formats that do not trigger the dictionary are:65929 970 48986-095742-719 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The GTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *identifikationsnummer*, *steueridentifikationsnummer*, and *steuernummer*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:302321760005330 23 217 600 05330-23-217-600-05330.23.217.600.05330/23/217/600/053The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:3 023 217 600 05330--23-217-600-05330 23-217.600/053 |
[]This dictionary detects Greek Tax Identification numbers (GRTIN).
This dictionary uses a variation of the *Modulo 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the GRTIN number matches a valid range. | The number formats that can trigger the dictionary are:19 86 02 35519 86-0235519 8602355A number format like 198602356 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The GRTIN number is in a popular format. | A number format like 198602355 can trigger the dictionary.The number formats that do not trigger the dictionary are:19 86 02 35519 86-0235519 8602355 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The GRTIN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *afm*, *afm#*, *tax identification number*, and *tin*. | A number format like 198602355 can trigger the dictionary.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:19 86 02 35519 86-0235519 8602355 |
[]This dictionary detects Hungarian Tax Identification Numbers (HUTIN), which are 10-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 97* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the HUTIN matches a valid range. | The number formats that can trigger the dictionary are:80 71 592 153807159215 38 071592153A number format like 8071592154 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The HUTIN is in a popular format. | A number format like 8071592153 triggers the dictionary.The number formats that do not trigger the dictionary are:80 71 592 153807159215 38 071592153 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The HUTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *adószám* and *adóazonosító szám*. | A number format like 8071592153 triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:80 71 592 153807159215 38 071592153 |
[]This dictionary detects Tax Identification numbers (NPWP) from Indonesia.
The popular format for a Tax Identification number is a 15-digit number. The Tax Identification number has the following structure:
- The first 9 digits (1-9) are the unique identity of the taxpayer.
- The next 3 digits (10-12) are the code for the tax office where the taxpayer registered for the first time.
- The last 3 digits (13-15) are the code for central or branch status.
This dictionary uses the *Luhn variation *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
-
-
-
-
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | The dictionary counts an instance as a violation if the Tax Identification number matches a valid range. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Tax Identification number is in a popular format. |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Tax Identification number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *npwp*, *indonesia tax number*, and *indonesian tax number*. |
[]This dictionary detects Irish Tax Identification Numbers (IETIN), which are 8- or 9-character unique identifiers issued by the Department of Social Protection. The IETIN is also used by the Revenue Commissioners to identify taxpayers.
This dictionary uses the *Modulo 23* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the IETIN matches a valid range. | The number formats that can trigger the dictionary are:1234567 T1234567 TWThe number formats that do not trigger the dictionary are:1234567Y (bad checksum)123456-7TW (doesn't match regex) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The IETIN is in a popular format. | A number format like 1234567T triggers the dictionary.The number formats that do not trigger the dictionary are:1234567 T1234567 TW |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The IETIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Personal Public Service Number*, *PPS num*, *Tax Identification Number*, *TIN*, *pps number*, *ppsn*, *ppsno*, *uimhir phearsanta seirbhíse poiblí*, *pps uimh*, and *Uimhir aitheantais phearsanta*. | A number format like 1234567T triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:1234567 T1234567 TW |
[]This dictionary detects Luxembourg Tax Identification Numbers (LUTIN), which are 11- or 13-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Luhn *and *Mod 11* checksums.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the LUTIN matches a valid range. | The number formats that can trigger the dictionary are:189 312 010 57321 893120105732189312010573 281 738 480 12081 738 480.12081 -738/ .4 80...-120The number formats that do not trigger the dictionary are:189312010573261432208511 (bad checksum) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The LUTIN is in a popular format. | The number formats that can trigger the dictionary are:189312010573281.738.480.12081-738-480-12081738480120The number formats that do not trigger the dictionary are:189 312 010 57321 893120105732189312010573 281 738 480 12081 738 480.12081 -738/ .4 80...-12081 738 480.120 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The LUTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *sécurité sociale*, *zinn nummer*, *carte sécurité sociale*, *étain*, *numéro d'étain*, *étain non*, *Numéro d'identification fiscal luxembourgeois*, *tin*, *zinn*, *Luxembourg Tax Identifikatiounsnummer*, and *steier*. | The number formats that trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:189312010573281.738.480.12081-738-480-12081738480120The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:189 312 010 57321 893120105732189312010573 281 738 480 12081 738 480.12081 -738/ .4 80...-12081 738 480.120 |
[]This dictionary detects New Zealand Tax Identification Numbers (NZTIN), which are 8- or 9-digit unique identifiers issued by the Inland Revenue Department (IRD).
This dictionary uses the *Mod 11 algorithm* for validation.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the NZTIN matches a valid range. | The number formats that can trigger the dictionary are:136-410132136-4-10-13249091 850A number format like 136-410-134 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The NZTIN is in a popular format. | The number formats that can trigger the dictionary are:49 091 850136410132136-410-132The number formats that do not trigger the dictionary are:136-410132136-4-10-13249091 850 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The NZTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *IRD Number* and *Inland Revenue Department*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:49 091 850136410132136-410-132The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:136-410132136-4-10-13249091 850 |
[]This dictionary detects Tax Identification numbers (PERUC) from Peru.
This dictionary uses a variation of the *Modulo 11* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the PERUC number matches a valid range. | The number formats that can trigger the dictionary are:20 503644-96820--503644-9682 -05/ .036 449...- 68A number format like 20503644969 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The PERUC number is in a popular format. | The number formats that can trigger the dictionary are:2050364496820 503644 968The number formats that do not trigger the dictionary are:20 503644-96820--503644-9682 -05/ .036 449...- 68 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The PERUC number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Registro Unico Contribuyentes*, *tax identification number*, *peru tax identification number*, *peruvian tax identification number*, *peru tin*, and *peruvian tin*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:2050364496820 503644 968The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:20 503644-96820--503644-9682 -05/ .036 449...- 68 |
[]This dictionary detects Tax Identification numbers (PLTIN) from Poland, which are 10- or 11-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a Member State.
This dictionary uses the *Modulo 11* checksum for the 10-digit number, and the *Luhn* checksum for the 11-digit number.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the PLTIN number matches a valid range. | The number formats that can trigger the dictionary are:2234 5678950207080 3628A number format like 2234567894 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The PLTIN number is in a popular format. | The number formats that can trigger the dictionary are:223456789502070803628The number formats that do not trigger the dictionary are:2234 5678950207080 3628 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The PLTIN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *nip*, *nip#*, *numer identyfikacji podatkowej*, *numeridentyfikacjipodatkowej*, *tax identification number*, *tax number*, and *tin*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:223456789502070803628The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:2234 5678950207080 3628 |
[]This dictionary detects Portuguese Tax Identification Numbers (PTIN), which are 9-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Mod 11 algorithm* for validation.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the PTIN number matches a valid range. | The number formats that can trigger the dictionary are:299 9999982544964.402544.96350A number format like 299999991 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The PTIN number is in a popular format. | A number format like 299999998 triggers the dictionary.The number formats that do not trigger the dictionary are:640130.3331640823 3234640 8233234 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The PTIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *cpf#*, *cpf*, *nif#*, *nif*, *numero fiscal*, and *tin*. | A number format like 299999998 triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:640130.3331640823 3234640 8233234 |
[]This dictionary detects Tax Identification numbers (CIF) from Spain.
This dictionary uses the *Luhn* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the CIF number matches a valid range. | A number format like A58818501 can trigger the dictionary.The number formats that do not trigger the dictionary are:A 58818501A588 18501A588185-01A58818502 (bad checksum) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The CIF number is in a popular format. | A number format like A58818501 can trigger the dictionary.The number formats that do not trigger the dictionary are:A 58818501A588 18501A588185-01 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The CIF number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *tax identification code*, *Código identificación fiscal*, *CIF*, and *CIF número*. | A number format like A58818501 can trigger the dictionary.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:A 58818501A588 18501A588185-01 |
[]This dictionary detects Swedish Tax Identification Numbers (STIN), which are 10-digit unique identifiers issued by the Directorate-General Taxation and Customs Union (DG TAXUD) to all taxpaying individuals of a member state.
This dictionary uses the *Luhn *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the STIN matches a valid range. | The number formats that can trigger the dictionary are:640130.3331640823 3234640 8233234A number format like 640823-3235 does not trigger the dictionary. |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The STIN is in a popular format. | The number formats that can trigger the dictionary are:640130-33316408233234The number formats that do not trigger the dictionary are:640130.3331640823 3234640 8233234 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The STIN is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *personnummer*, *skatt identifikation*, *skattebetalarens*, *identifikationsnummer*, and *sverige tin*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:640130-33316408233234The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:640130.3331640823 3234640 8233234 |
[]This dictionary detects Tax Identification numbers (USITIN) from the United States.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the USITIN number matches a valid range. | The number formats that can trigger the dictionary are:927 70-5828927 70 5828927 70 58 28A number format like 827705828 does not trigger the dictionary (first digit must be a 9). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The USITIN number is in a popular format. | A number format like 927705828 can trigger the dictionary.The number formats that do not trigger the dictionary are:927 70-5828927 70 5828927 70 58 28 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The USITIN number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *ITIN*, *USITIN*, *tax identification number*, and *taxpayer identification number*. | A number format like 927705828 can trigger the dictionary.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:927 70-5828927 70 5828927 70 58 28 |
[]This dictionary detects technical documents, like computer user manuals, white papers, technical publications, etc.
Zscaler supports only the following document types for technical documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a technical document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary detects transportation and motor department documents, like sale or transfer of a vehicle, license forms, driving records, etc.
Zscaler supports only the following document types for transportation and motor department documents: RTF, PDF, MSG, DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTM, PPT, PPTX, PPSX, PPTM, POTM, POTX, and IWORK (pages, numbers, and keynote). To detect sensitive content, this dictionary requires at least 1 KB of extracted content from a transportation and motor department document file.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
| Confidence Score | Threshold Criteria |
| ---------------- | ------------------ |
| **Low** | This dictionary counts an instance as a violation if the Machine Learning (ML) match score is 50 or more. |
| **Medium** | This dictionary counts an instance as a violation if the ML match score is 70 or more. |
| **High** | This dictionary counts an instance as a violation if the ML match score is 90 or more. |
[]This dictionary uses phrase matching to detect content related to treatments information. It does not use a checksum.
You can specify an Action to configure how the dictionary evaluates matching treatment names:
- **Count All**: The dictionary counts all matches of the treatment name, including identical treatment names, toward the match count.
- **Count Unique**: The dictionary counts each unique match of the treatment name toward the match count only once, regardless of how many times the treatment name appears.
[]This dictionary detects the 13-digit Unique Master Citizen Number.
This dictionary uses the *Mod 11 *checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the Unique Master Citizen Number matches a valid range. | The number formats that can trigger the dictionary are:0407 9894 0465504.0798-940 465504 -07/ .989 404...-655A number format like 0407989404651 does not trigger the dictionary (bad checksum). |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The Unique Master Citizen Number is in a popular format. | A number format like 0407989404655 triggers the dictionary.The number formats that do not trigger the dictionary are:0407 9894 0465504.0798-940 465504 -07/ .989 404...-655 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The Unique Master Citizen Number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *JMBG*, *ЈМБГ*, *ЕМБГ*, *Jedinstveni matični broj građana*, and *EMŠO*. | A number format like 0407989404655 triggers the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases.The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:0407 9894 0465504.0798-940 465504 -07/ .989 404...-655 |
[]This dictionary detects Austrian value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses a variation of the *Mod 10* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:AT U10223006AT-U10223006AT.U10223006AT -. U10223006The number formats that do not trigger the dictionary are:ATU10223007 (invalid checksum)A TU10223006ATU 10223006ATU10 223 00 6 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:ATU10223006AT U10223006The number formats that do not trigger the dictionary are:AT U10223006AT-U10223006AT.U10223006AT -. U10223006 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by phrases such as: *Umsatzsteuer-Identifikationsnummer*, *Ust-Identifikationsnummer*, *umsatzsteuer*, *vat number*, *vat num*, and *vat*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:ATU10223006AT U10223006The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:AT U10223006AT-U10223006AT.U10223006AT -. U10223006 |
[]This dictionary detects Belgian value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses the *Mod 97* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:BE 0776091951BE-0776091951BE.0776091951BE -. 0776091951The number formats that do not trigger the dictionary are:BE0776091952 (invalid checksum)B E0776091951BE0 776091951BE077 609 195 1 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:BE0776091951BE 0776091951The number formats that do not trigger the dictionary are:BE 0776091951BE-0776091951BE.0776091951BE -. 0776091951 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *vat number* and *vat num*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:BE0776091951BE 0776091951The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:BE 0776091951BE-0776091951BE.0776091951BE -. 0776091951 |
[]This dictionary detects French value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses the *Mod 97* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:FR 00300076965FR-00300076965FR.00300076965FR -. 00300076965The number formats that do not trigger the dictionary are:FR00300076964 (invalid checksum)F R00300076965FR0 0300076965FR003 000 769 65 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:FR00300076965FR 00300076965The number formats that do not trigger the dictionary are:FR 00300076965FR-00300076965FR.00300076965FR -. 00300076965 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Numéro TVA intracommunautaire*, *TVA intracommunautaire*, *TVA*, and *vat*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:FR00300076965FR 00300076965The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:FR 00300076965FR-00300076965FR.00300076965FR -. 00300076965 |
[]This dictionary detects German value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses a combination of the *Mod 10* and *Mod 11* checksums.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:DE 111111125DE-111111125DE.111111125DE -. 111111125The number formats that do not trigger the dictionary are:D E111111125DE1 11111125DE 111 111 125 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:DE111111125DE 111111125The number formats that do not trigger the dictionary are:DE 111111125DE-111111125DE.111111125DE -. 111111125 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *mwst*, *mehrwertsteuer identifikationsnummer*, *mehrwertsteuer nummer*, *vat num*, and *vat#*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:DE111111125DE 111111125The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:DE 111111125DE-111111125DE.111111125DE -. 111111125 |
[]This dictionary detects Irish value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses the *Modulo 23* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:IE 8Z49289FIE-8Z49289FIE.8Z49289FIE -. 8Z49289FThe number formats that do not trigger the dictionary are:IE8Z49289G (bad checksum)I E8Z49289F (doesn't match regex)IE8Z 49289F (doesn't match regex)IE8-Z4-92-89F (doesn't match regex) |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:IE8Z49289FIE 8Z49289FThe number formats that do not trigger the dictionary are:IE 8Z49289FIE-8Z49289FIE.8Z49289FIE -. 8Z49289F |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *vat num* and *vat number*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:IE8Z49289FIE 8Z49289FThe number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:IE 8Z49289FIE-8Z49289FIE.8Z49289FIE -. 8Z49289F |
[]This dictionary detects Luxembourg value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses the *Mod 89* checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:LU 13669580LU-13669580LU.13669580LU -. 13669580The number formats that do not trigger the dictionary are:LU13669581 (invalid checksum)L U13669580LU1 3669580LU136 695 80 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:LU13669580LU 13669580The number formats that do not trigger the dictionary are:LU 13669580LU-13669580LU.13669580LU -. 13669580 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *tva*, *vat num*, and *vat*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:LU13669580LU 13669580The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:LU 13669580LU-13669580LU.13669580LU -. 13669580 |
[]This dictionary detects Netherlands value-added tax (VAT) numbers, which are alphanumeric identifiers used to identify taxable persons (business) or non-taxable legal entities.
This dictionary uses the *Mod 11* checksum, which is similar to the Luhn checksum.
The following table lists the confidence score threshold criteria for this dictionary. You can modify the [confidence score threshold](/zia/editing-predefined-dlp-dictionaries#confidence).
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
| Confidence Score | Threshold Criteria | Examples of Data |
| ---------------- | ------------------ | ---------------- |
| **Low** | The dictionary counts an instance as a violation if the VAT number matches a valid range. | The number formats that can trigger the dictionary are:NL 123456782B01NL-123456782B01NL.123456782B01NL -. 123456782B01The number formats that do not trigger the dictionary are:NL123456783B01 (invalid checksum)N L123456782B01NL1 23456782B01NL123 456 78 2B0 1 |
| **Medium** | The dictionary counts an instance as a violation if:The requirements of Low Confidence are met.The VAT number is in a popular format. | The number formats that can trigger the dictionary are:NL123456782B01NL 123456782B01The number formats that do not trigger the dictionary are:NL 123456782B01NL-123456782B01NL.123456782B01NL -. 123456782B01 |
| **High** | The dictionary counts an instance as a violation if:The requirements of Medium Confidence are met.The VAT number is accompanied by any of the dictionary’s default or custom high confidence phrases. For example, *Btw-nummer*, *Btw-num*, *vat num*, and *vat*. | The number formats that can trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:NL123456782B01NL 123456782B01The number formats that do not trigger the dictionary if accompanied by any of the dictionary’s default or custom high confidence phrases are:NL 123456782B01NL-123456782B01NL.123456782B01NL -. 123456782B01 |
[]This dictionary detects content related to weapons. It detects weapons such as firearms and other military weapons.
This dictionary does not use a checksum.
You can modify the Confidence Score Threshold. Confidence scores inform the dictionary how high it must raise the bar, or threshold, for identifying violations and triggering them. To learn more, see [Configuring the Confidence Score Threshold.](/zia/editing-predefined-dlp-dictionaries#confidence)