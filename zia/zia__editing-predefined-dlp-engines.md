# Editing Predefined DLP Engines
Source: https://help.zscaler.com/zia/editing-predefined-dlp-engines
PDF: https://help.zscaler.com/pdf/com/en/1400091.pdf

The Zscaler service provides 5 predefined Data Loss Prevention (DLP) engines to all customers:
- **HIPAA**: This engine is designed to detect Health Insurance Portability and Accountability Act (HIPAA) violations, using the Social Security Numbers (US) and Medical Information dictionaries.
- **GLBA**: This engine is designed to detect violations of the Gramm-Leach-Bliley Act (GLBA), using the Social Security Numbers (US) and Financial Statements dictionaries.
- **PCI**: This engine is designed to detect Payment Card Industry (PCI) compliance violations, using the Credit Cards and Social Security Numbers (US) dictionaries.
- **Offensive Language**: This engine is designed to detect offensive language, using the Adult Content dictionary.
- **Self-Harm & Cyberbullying**: This engine is designed to detect violations of student safety, using the Self-Harm & Cyberbullying dictionary.
The Self-Harm & Cyberbullying engine is intended for use by K-12 educators. If you’re an educator, contact your Zscaler Account team to enable this feature.
The following engines are available by default for customers with tenants enabled on April 4, 2025, or later. To request access to these engines, contact Zscaler Support.
- [Additional predefined DLP engines](#Additional-Engines)
You can edit a predefined DLP engine to detect content that is relevant to your organization. To edit a predefined DLP engine:
- Go to **Administration** >** DLP Dictionaries & Engines**.
- In the **DLP Engines **tab, click the **Edit** icon for the predefined DLP engine.
The **Edit DLP Engine** window appears.
- For **Engine Builder**: Add operators and DLP dictionaries to [build an expression](/zia/understanding-dlp-engines#building-expressions). You can see your expression in the **Expression Preview**.
[See image.](#DLP-engine-builder-image)
Under **Expression**:
- Select an operator to build your expression. The operators include **All** (AND), **Any** (OR), **Exclude **(AND NOT), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the DLP engine.
For the root expression, only the **All** (AND), **Any **(OR), and **Sum** operators are allowed.
- Click **Add** to add a **Dictionary** or a **Subexpression**. Click the **Remove** icon (![dlp-engine-remove-icon.png](/downloads/zia/policies/data-loss-prevention/adding-dictionaries-predefined-dlp-engine/dlp-engine-remove-icon.png)
) to delete dictionaries or subexpressions.
- If you use the **Sum** operator, select two or more predefined or custom DLP dictionaries. You must set a value for the [match count](/zia/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
- If you use the **All**, **Any**, or **Exclude** operators, you must select a predefined or custom DLP dictionary. Certain dictionaries require you to set a value for the [match count](/zia/understanding-dlp-engines#match-count). You can enter any value less than 1,000.
[See image.](#DLP-match-count-image)
- If you click **Subexpression**, you must select an operator. The operators include **All** (AND), **Any** (OR), **Exclude **(AND NOT), and **Sum**. The **Sum** operator is available for count-based DLP dictionaries (i.e., Credit Cards, Social Security Numbers, etc.) and allows you to specify the sum total of matches that trigger a group of dictionaries specified in the subexpression.
You can use the **Sum** operator as part of a subexpression; however, you cannot add a subexpression to an expression or subexpression that uses the **Sum** operator.
[See image.](#DLP-subexpression-image)
- Continue adding dictionaries and operators to the expression as needed. At each level, you can create up to 4 subexpressions, use up to 4 operators, and add up to 16 dictionaries per operator.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
You can also add a custom DLP engine. To learn more, see [Adding Custom DLP Engines](/zia/adding-custom-dlp-engine).
[]
- **CCPA**: The following engines are designed to detect California Consumer Privacy Act violations, using the Social Security Numbers (US), Tax Identification Number (US), Names (US), Medical Information, Diseases Information, Drugs Information, and Credit Cards dictionaries.
- **CCPA - High Volume**: This engine detects CCPA violations at a high threshold (i.e., more than 25 matches).
- **CCPA - Low Volume**: This engine detects CCPA violations at a low threshold (i.e., more than one match).
- **Credentials and Secrets**: This engine is designed to detect credentials and secrets violations, using the Credentials and Secrets dictionary.
- **DPDPA**: This engine is designed to detect Digital Personal Data Protection Act violations, using the Aadhaar Card Number (India) dictionary.
- **Finance**: This ML-based engine is designed to detect financial violations, using the Financial Statements, ABA Bank Routing Number, Credit Cards, and International Bank Account Number (IBAN) dictionaries.
- **FISMA**: The following engines are designed to detect Federal Information Security Modernization Act violations, using the Credit Cards, Diseases Information, Drugs Information, and Social Security Numbers (US) dictionaries.
- **FISMA - High Volume**: This engine detects FISMA violations at a high threshold (i.e., more than 25 matches).
- **FISMA - Low Volume**: This engine detects FISMA violations at a low threshold (i.e., more than one match).
- **GDPR**: The following engines are designed to detect General Data Protection Regulation violations, using the Unified Civil Number (Bulgaria), Citizen Service Number (Netherlands), National Economic Registry Number (Poland), National Identification Number (France), National Identification Number (Poland), National Identification Number (Spain), Passport Number (European Union), Social Security Number (Austria), Social Security Number (Spain), Social Security Number (Switzerland), Tax Identification Numbers (Austria), Tax Identification Number (Belgium), Tax Identification Number (Denmark), Tax Identification Number (Finland), Tax Identification Numbers (France), Tax Identification Number (Germany), Tax Identification Number (Greece), Tax Identification Numbers (Hungary), Tax Identification Number (Ireland), Tax Identification Numbers (Luxembourg), Tax Identification Number (Poland), Tax Identification Number (Portugal), Tax Identification Number (Spain), Tax Identification Number (Sweden), Unique Master Citizen Number, VAT Numbers (Austria), VAT Numbers (Belgium), VAT Numbers (France), VAT Numbers (Germany), VAT Number (Ireland), VAT Numbers (Luxembourg), and VAT Numbers (Netherlands) dictionaries.
- **GDPR - High Volume**: This engine detects GDPR violations at a high threshold (i.e., more than 25 matches).
- **GDPR - Low Volume**: This engine detects GDPR violations at a low threshold (i.e., more than one match).
- **Legal**: This ML-based engine is designed to detect legal violations, using the Legal Document dictionary.
- **LGPD**: The following engines are designed to detect General Personal Data Protection Law violations, using the CNPJ Number (Brazil) and Individual Taxpayer Registry ID (Brazil) dictionaries.
- **LGPD - High Volume**: This engine detects LGPD violations at a high threshold (i.e., more than 25 matches).
- **LGPD - Low Volume**: This engine detects LGPD violations at a low threshold (i.e., more than one match).
- **Medical**: This ML-based engine is designed to detect medical violations, using the Medical Information, Diseases Information, Drugs Information, National Provider Identifier Number (US), NDC Number (Package), NDC Number (Product), and Treatments Information dictionaries.
- **NIST (RMF for DoD IT)**: The following engines are designed to detect National Institute of Standards and Technology Risk Management Framework for Department of Defense IT violations, using the Credit Cards, Diseases Information, Drugs Information, Social Security Numbers (US), Names (US), and Medical Information dictionaries.
- **NIST (RMF for Dod IT) - High Volume**: This engine detects NIST (RMF for Dod IT) violations at a high threshold (i.e., more than 25 matches).
- **NIST (RMF for Dod IT) - Low Volume**: This engine detects NIST (RMF for Dod IT) violations at a low threshold (i.e., more than one match).
- **PDPA**: The following engines are designed to detect Personal Data Protection Act violations, using the NRIC Numbers (Singapore) and Credit Cards dictionaries.
- **PDPA - High Volume**: This engine detects PDPA violations at a high threshold (i.e., more than 25 matches).
- **PDPA - Low Volume**: This engine detects PDPA violations at a low threshold (i.e., more than one match).
- **PII (US)**: The following engines are designed to detect Personally Identifiable Information violations, using the Social Security Numbers (US) and Tax Identification Number (US) dictionaries.
- **PII (US) - High Volume**: This engine detects PII (US) violations at a high threshold (i.e., more than 25 matches).
- **PII (US) - Low Volume**: This engine detects PII (US) violations at a low threshold (i.e., more than one match).
- **PIPEDA**: The following engines are designed to detect Personal Information Protection and Electronic Documents Act violations, using the Names (Canada), Social Insurance Number (Canada), ABA Bank Routing Number, and Credit Cards dictionaries.
- **PIPEDA - High Volume**: This engine detects PIPEDA violations at a high threshold (i.e., more than 25 matches).
- **PIPEDA - Low Volume**: This engine detects PIPEDA violations at a low threshold (i.e., more than one match).
[]![The DLP Engine Expression Builder](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/editing-predefined-dlp-engines/DLP-Predefined-Engine-Builder-Updated.png)
[]![The Match Count for DLP Dictionaries in the Engine](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/editing-predefined-dlp-engines/ZIA-DLP-Engine-Builder-Match-Counts.png)
[]![Operators for the DLP Engine Expression](/downloads/zia/policies/data-loss-prevention/dlp-dictionaries-engines/editing-predefined-dlp-engines/ZIA-DLP-Predefined-Engine-Operators.png)