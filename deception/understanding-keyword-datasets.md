# Understanding Keyword Datasets
Source: https://help.zscaler.com/deception/understanding-keyword-datasets
PDF: https://help.zscaler.com/pdf/com/en/1531516.pdf

Zscaler Deception allows you to configure a set of keywords that can be used to autogenerate recommendations for decoy parameters, such as hostnames, file and folder names, network decoy names, etc. Zscaler uses a proprietary algorithm to randomly generate recommendations for decoy parameters.
When keywords are configured, Zscaler generates recommendations that include the keywords in addition to randomly generated recommendations. When generating keyword-based recommendations, the keyword is part of the generated texts and is not exclusively used to avoid conflicts. For example, if "admin" is a configured keyword, keyword-based recommendations can be admin-pc, adminlog, etc., and cannot be "admin" alone. Also, when multiple keywords are configured, keywords are chosen randomly to generate a recommendation.
Only one keyword is used for each keyword-based recommendation.
To learn how to configure keyword datasets, see [Configuring Keyword Datasets](/deception/configuring-keyword-datasets).