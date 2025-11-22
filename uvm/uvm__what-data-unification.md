# What Is Data Unification?
Source: https://help.zscaler.com/uvm/what-data-unification
PDF: https://help.zscaler.com/pdf/com/en/1527676.pdf

Data unification is a fundamental process of transforming disparate data into actionable business insights. It involves correlating data from multiple sources, merging duplicate records, and establishing data consistency by applying standardized rules and conditions to yield a reliable and accurate unified record.
![diagram illustrating the three steps of data unification](/downloads/uvm/configure/data-unification/what-data-unification/blobid0.png)
Key Features and Benefits
Data unification provides the following features and benefits:
- Data Integrity: Unifying data from multiple sources creates a single, accurate view of key business objects like assets, components, and findings. This consolidated view helps reduce operational inefficiencies caused by fragmented or duplicated data, fills information gaps, and supports more reliable decision making.
- Deduplication:
Entity unification ensures that redundant or conflicting records are automatically resolved through configurable logic. This results in a single source of truth while preserving raw data for lineage tracking and audit purposes.
- Attribute-Level Conflict Resolution:
Field unification incorporates robust attribute reconciliation processes that address inconsistencies between merged records. This ensures data integrity at the attribute level, enhancing the quality and trustworthiness of the unified dataset.
- Flexible Business Rule Application:
Attribute transformation enables the application of organization-specific business rules to enrich and standardize data. This flexibility supports diverse use cases across analytics, compliance, and operational workflows.
- Data Lineage and Transparency:
Maintaining access to raw, source-level data alongside unified records provides visibility into the data's origin and transformation steps, which are essential for traceability, compliance, and troubleshooting.
How Data Unification Works
Unification involves standardizing data from multiple sources by identifying duplicate entities, resolving attribute conflicts, and applying business logic. The process consists of two main components: Entity Unification and Field Unification.
Entity Unification
Ingesting data from multiple sources often results in duplicate records for the same entity. Entity unification is the data normalization process that merges (i.e., deduplicates) these duplicate records, creating a single trusted source of truth for your organization's data, while still maintaining raw data for lineage and visibility. To learn more, see [Configuring Entity Unification](/uvm/configuring-entity-unification) and [Managing Entity Unification](/uvm/managing-entity-unification).
Field Unification
Field unification includes two steps:
- Attribute Reconciliation: During entity unification, conflicts can arise between the values of the merged entities' attributes (e.g., discrepancies in the asset's type format, or a finding's severity score). These conflicts are typically reconciled (i.e., resolved) using system defaults, or through applying Priority By Source logic. To learn more, see [Configuring Field Unification](/uvm/configuring-field-unification) and [Attribute Reconciliation Default Functions](/uvm/attribute-reconciliation-default-functions).
- Attribute Transformation: After your data is properly deduplicated and reconciled, the next step is applying business logic rules to classify and enrich the data through field unification rules. To learn more, see [Configuring Field Unification](/uvm/configuring-field-unification) and [Managing Field Unification](/uvm/managing-field-unification).