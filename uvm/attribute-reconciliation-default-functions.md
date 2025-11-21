# Attribute Reconciliation Default Functions
Source: https://help.zscaler.com/uvm/attribute-reconciliation-default-functions
PDF: https://help.zscaler.com/pdf/com/en/1528021.pdf

Attribute reconciliation is the process of resolving conflicts that arise when merging duplicate entities during entity unification. This process ensures that the most accurate and up-to-date data is retained across your system, eliminating inconsistencies and inaccuracies. To learn more, see [What Is Data Unification?](/uvm/what-data-unification) and [Configuring Entity Unification](/uvm/configuring-entity-unification).
For example, when merging multiple Asset records into a single asset, the Asset Operating System field might contain multiple values. In such cases, the system automatically selects the value that appears most frequently among the merged records.
By default, every field has system-defined reconciliation logic based on industry best practices. These defaults can be adjusted upon request or manually replaced with Priority By Source reconciliation logic in field unification. To learn more, see [Configuring Field Unification](/uvm/configuring-field-unification).
Default Functions by Field Type
The following table outlines the system's default functions for determining field values during entity deduplication conflict resolution, categorized by field type.
![f01b2f46-bdd1-4511-8eaf-f646f97511df.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/f01b2f46-bdd1-4511-8eaf-f646f97511df.png)
![02c0d920-33d7-40ae-8ef2-67ac274b463f.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/02c0d920-33d7-40ae-8ef2-67ac274b463f.png)
![e02217f1-12ad-43c7-9652-724b0663d9e2.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/e02217f1-12ad-43c7-9652-724b0663d9e2.png)
![27834c75-68e2-4d0c-ad8b-d81d83dcf0f4.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/27834c75-68e2-4d0c-ad8b-d81d83dcf0f4.png)
![beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png)
![039dead8-b6e6-405c-ad78-d9f4d43a67b6.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/039dead8-b6e6-405c-ad78-d9f4d43a67b6.png)
![e39e3770-a3ba-421c-9122-1e419558a618.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/e39e3770-a3ba-421c-9122-1e419558a618.png)
| Icon | Field Type | Default Function | Populated Value | Examples |
| ---- | ---------- | ---------------- | --------------- | -------- |
|  | Text | MAJORITY | The most frequent value from the set of values | Asset Owner IDTicket Assignee |
|  | Repeated (all types) | COLLECT_DISTINCT_FLAT | A list of distinct values | Ticket Sources |
|  | Number | MAX | The maximum value for number type fields MAX is the highest value | Ticket Severity Score |
|  | Boolean | MAX | The maximum value for Boolean fields is TRUE if at least one value is TRUE | Asset Is Behind FirewallAsset Is Critical Asset |
|  | Date | MAX | The most recent date | Ticket SLA |
|  | IP | COLLECT_DISTINCT_FLAT | A list of distinct IP addresses | -- |
|  | Fix | COLLECT_DISTINCT_FLAT | A list of distinct fixes | Optimal Fix |
Commonly Used Fields
The following table shows the default functions for commonly used fields:
![beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png)
![beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png](/downloads/uvm/configure/data-unification/attribute-reconciliation-defaults/beaa3da3-d8a8-4f35-94d3-b463e9a058f6.png)
| Icon | Field | Default Function | Populated Value | Examples |
| ---- | ----- | ---------------- | --------------- | -------- |
|  | First Seen (for all entity types) | MIN | The earliest date value | Finding First Seen |
|  | Last Seen (for all entity types) | MAX | The** **most recent date value | Asset Last Seen |