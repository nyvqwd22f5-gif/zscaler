# Understanding and Building Queries
Source: https://help.zscaler.com/deception/understanding-and-building-queries
PDF: https://help.zscaler.com/pdf/com/en/1531515.pdf

Zscaler Deception uses a purpose-built rule engine to evaluate queries used to build user-defined conditions and filters across different modules. The rules are built using Boolean expressions based on a custom query language. You can use the query language to build custom conditions or filters in the following modules:
- [Filter](/deception/viewing-and-managing-zscaler-deception-dashboard#filter-alert-queries) in Dashboard
- Conditions in [Orchestration Rules](/deception/about-orchestration-rules)
- Event Filters in [SIEM Integrations](/deception/about-siem-integrations)
- [ThreatParse rules](/deception/configuring-threatparse-rule) in Miragemaker
Query Syntax
[]In Deception, the queries for conditions and filters are built using Boolean expressions. The syntax is modeled based on [Python Boolean expressions](https://docs.python.org/3/reference/expressions.html). A simple Boolean expression has the following syntax:
`<operand> <comparison_operator> <operand> <boolean_operator> <operand> ... `
where,
- `operand `can be an identifier, constant, or an expression that evaluates to a value. Examples of operands: `x`, `5`, `true`, and `false`.
- `comparison_operator` is used to compare two operands and returns a Boolean value (`true` or `false`) based on the comparison result. Comparison operators: == (equal to), `!=` (not equal to), `>` (greater than), `<` (less than), `>=` (greater than or equal to), and `<=` (less than or equal to).
- `boolean_operator` is used to combine multiple Boolean expressions and returns a Boolean value based on the combination. Boolean operators: `and`, `or`, and `not`.
In addition, you can use parentheses to group sub-expressions and establish the order of evaluation. They are useful when combining multiple Boolean expressions to create complex expressions. The following example is a complex expression:
(attacker.ip is "192.168.1.1" and attacker.port > 200) or decoy.port > 200
where,
- `attacker.ip `is an identifier.
- `is `is a comparison operator.
- `"192.168.1.1"` is a constant.
- `attacker.ip is "192.168.1.1"` is an expression.
- `attacker.port > 200` is also an expression.
- `decoy.port > 200` is also an expression.
These three expressions are combined together using Boolean operators `and/or` to create a complex Boolean expression. In this example, the expression evaluates to true if the `attacker.ip` field is equal to `"192.168.1.1"` and` attacker.port` is greater than `200 `or just `decoy.port` is greater than `200`.
Building a Query
Based on your requirements, you can construct queries by using the appropriate values for each component, [conforming to the syntax](#zd-query-language-syntax).
- [Fields](#zd-query-language-fields)
- [Operators](#zd-query-language-operators)
- [Operator Precedence](#zd-query-language-operator-precedence)
- [Constants](#zd-query-language-constants)
[]Fields are used as operands in the query. A field is always placed on the left side of a simple Boolean expression. Depending on the module, Deception provides a list of supported values for fields. The fields can be of different data types. To fetch a list of supported values, type a relevant text in the query editor, and a list of all possible fields is shown in a drop-down menu.
The query editor is available in the following sections in Deception:
-
Under **Investigate**, an interactive query builder is located on the top of the dashboard to filter dashboard items.
[See image.](#zd-image-investigate-query-language)
-
Under the **General **section of the **Rule Details** window to create rule conditions: To access the **Rule Details** window, go to **Orchestrate > Rules**, and add (by clicking **Add Rule**) or edit (by clicking the edit icon) a rule.
[See image.](#zd-image-orchestration-query-language)
-
Under the **General **section of the SIEM integration details window to create filters for various SIEM integrations: To access the respective SIEM integration details window, go to **Orchestrate > SIEM Integrations**, and add a new integration (by clicking **Add Integration** and choosing a preferred solution) or edit (by clicking the edit icon) an existing integration.
[See image.](#zd-image-siem-query-language)
The availability of fields varies between each module.
[]![A screenshot capturing the query language editor on the Ivestigate page](/downloads/deception/investigate/query-language/zscaler-deception-investigate-query.jpg)
[]![A screenshot capturing the query language editor in the Orchestrate Rules window](/downloads/deception/investigate/query-language/zscaler-deception-rule-details-query.jpg)
[]![A screenshot capturing query language editor in SIEM integration](/downloads/deception/investigate/query-language/zscaler-deception-siem-details-query.jpg)
[]The rule engine in Deception provides different types of operators to perform different operations, such as binary comparisons, bound tests, regular expression tests, and membership tests. You can build complex conditions and filters based on your requirements by using different supported operations.
- [Binary Comparisons](#zd-query-language-binary-comparisons)
- [Bound Tests](#zd-query-language-bound-tests)
- [Regular Expression Operators](#zd-query-language-regex)
- [Membership Tests](#zd-query-language-membership-tests)
- [Logical Operators](#zd-query-language-boolean-logical-operators)
[]Binary comparisons are operations in which two operands are compared using different operators and a truth value is established. All comparison operators are binary operators. The general syntax of binary comparison expressions is:
<operand> <comparison_operator> <operand>
The following table lists all supported comparison operators with examples:
| Operation | Operator | Alternative Keywords | Description |
| --------- | -------- | -------------------- | ----------- |
| Equality (comparison) | `==` | `is` | Checks if two values are equal or the same. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`attacker.ip is "192.168.1.1"` |
| Lesser than or earlier (comparison) | `<` | `less than` or `before` | Checks if the value of the left side of the operator is lesser or occurs before the value on the right side of the operator. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`attacker.port less than 128` |
| Lesser than or equal to/before or equal to (comparison) | `<=` | Not applicable | Checks if the value of the left side of the operator is equal/lesser or occurs before the value of on the right side of the operator. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`attacker.score < 50` |
| Greater than or after | `>` | `greater than` or `after` | Checks if the value of the left side of the operator is greater or occurs after the value on the right side of the operator. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`decoy.port > 100` |
| Greater than or equal to/after or equal to (comparison) | `>=` | Not applicable | Checks if the value of the left side of the operator is equal/greater or occurs after the value on the right side of the operator. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`decoy.port >= 100` |
| Non-equality (comparison) | `!=` | `is not` | Checks if two values are not the same. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`decoy.type is not "recon"` |
[]Bound tests are performed using ternary operators to check whether a given field (identifier) occurs (or does not occur) between two values (constants). The constants can be integers, fractional numbers, or dates. The general syntax of bound test expressions is:
<operand> <bound_operator> <constant_1> and <constant_2>
where,
- `operand` is a field.
- `bound_operator` is either `between` or` not between` based on the bound test.
- `constant_1` and `constant_2` are any two [supported constants](/deception/query-language#zd-query-language-constants).
The following table lists all supported bound test operators with examples:
| Operation | Operator | Description |
| --------- | -------- | ----------- |
| Is within range? | `between`/`and` | Checks if the field value occurs between two constants. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`timestamp between '2023-10-12 12:22' and '2023-11-3 12:22'` |
| Is outside range? | `not between`/`and` | Checks if the field value is outside the range of two constants. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`decoy.port not between 50 and 100` |
Symbols in binary comparison operators can be used as an alternative to keyword-based bound test operations. The binary comparison operators (<=` `and >=) can be used to define the range limits.
| Operation | Keyword-based bound test expression | Equivalent Expression |
| --------- | ----------------------------------- | --------------------- |
| Is within range? | `timestamp between '10am' and '8pm'` | `timestamp >= '10am' and timestamp <= '8pm'` |
| Is outside range? | `network.orig_bytes not between 2000 and 3000` | `network.orig_bytes >= 2000 and network.orig_bytes <= 3000` |
[]The regular expression test allows you to compare a field value against a regular expression constant. The general syntax of the regex test expressions is:
identifier regex_operator regex_expression
where,
- `identifier `is always a [supported field](#zd-query-language-fields).
- `regex` operator is `~` or `like`.
- `regex_expression` is any standard regular expression string.
Regular expressions can only be compared to string-type fields.
The `regex` operator checks if the field value on the left side of the operator matches with the regular expression on the right side of the operator.
For example, consider the following regex test expression:
web.method like /.*get.*/I
The expression checks if the value of `web.method` matches with the `get` string irrespective of the text case. An equivalent expression using the symbol is:
web.method ~ /.*get.*/I
- The regular expressions are built using the JavaScript regex notation.
- The regular expression constant follows the JavaScript notation of forward slashes at the beginning and the end. Example: `/[0-9a-b]+(a|b)/`.
- The expression accepts flags that have the same meaning as [Python's re flags](https://docs.python.org/2/library/re.html#re.I).
- `I`: Performs case-insensitive matching. Expressions like `[A-Z]` will match lowercase letters, too. This is not affected by the current locale configured in the Zscaler Deception Admin Portal. To achieve this effect on non-ASCII Unicode characters such as `ü` and `Ü`, add the UNICODE flag. This flag is not supported in the [Filters](/deception/viewing-and-managing-zscaler-deception-dashboard#filter-alert-queries) in Dashboard. However, you can use it in regular expression queries in conditions in [Orchestration Rules](/deception/about-orchestration-rules), event filters in [SIEM Integrations](/deception/about-siem-integrations), and [ThreatParse rules](/deception/configuring-threatparse-rule) in Miragemaker.
- `L`: Makes `\w`, `\W`, `\b`, `\B`, `\s`, and `\S` dependent on the current locale configured in the Deception Admin Portal.
- `M`: When specified, the pattern character `^` matches at the beginning of the string and at the beginning of each line (immediately following each newline), and the pattern character `$` matches at the end of the string and at the end of each line (immediately preceding each newline). By default, `^` matches only at the beginning of the string, `$` only at the end of the string, and immediately before the newline (if any) at the end of the string.
- `S`: Makes the '`.`' special character match any character at all, including a newline; without this flag, '`.`' will match anything except a new line.
[]The membership operation is used to check whether a value is within a `string` or `list` constant. The membership operators are binary operators and can have a constant or a field on either of the sides. However, at least one of the operands must be a field (identifier). The general syntax of the membership test expressions is:
operand_1 membership_operator operand_2
where,
- `operand_1` and `operand_2` are either an identifier or a constant.
- `membership_operator` is either `in` or `not in`.
-
-
| Operation | Operator | Description |
| --------- | -------- | ----------- |
| Is a member? | `in` | Checks if a value is part of another string or list constant. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Examples:`windows.Version in [5, 2]``"powershell" in windows.CommandLine` |
| Not a member? | `not`/`in` | Checks if a value is not a part of another string or list constant. If yes, the expression evaluates to `true`. Otherwise, the expression evaluates to `false`.Example:`attacker.ip not in ["10.10.2.2", "10.10.2.1"]` |
[]The Boolean logical operators are used to combine two or more simple expressions to build compound Boolean expressions. The general syntax of Boolean expressions is:
expression_1 logical_operator expression_2
where,
- `expression_1` and `expression_2` are simple Boolean expressions that independently evaluate to `true` or `false`.
- `logical_operator` is either `logical AND` or `logical OR`.
The following table lists all supported logical operators with examples:
| Operation | Operator | Description |
| --------- | -------- | ----------- |
| Logical AND | `and` | Checks if both sides of the operator evaluate to `true`. If yes, the expression evaluates to true. Otherwise, the expression evaluates to `false`.Example:`attacker.ip is "192.168.1.1" and attacker.port > 200` |
| Logical OR | `or` | Checks if either of the sides of the operator evaluates to `true`. If yes, the expression evaluates to true. Otherwise, the expression evaluates to `false`.Example:`attacker.ip is "192.168.1.1" or decoy.port > 200` |
| Logical NOT | `not` | Inverts the truth value of a constant or an expression. If an expression or a constant evaluates to true, then the logical NOT operation changes the truth value to false and vice versa.Example:`attacker.ip is not "192.168.1.1"` |
[]When building a compound Boolean expression, the rule engine must evaluate the expression starting from one of the operators. The rule engine uses the operator precedence to determine the order of evaluation as described in the following table:
| Precedence (Rank) | Operators | Description |
| ----------------- | --------- | ----------- |
| 1 | `between`...`and`... | Ternary comparisons, including membership tests and identity tests |
| 2 | `>`, `after`, `greater than`, `>=`, `<`, `before`, `less than`, `<=`, `==`, `is`, `!=`, `is not`, `in`, `not in`, `~`, `like` | Binary comparisons, including membership tests and identity tests |
| 3 | `and` | Logical AND |
| 4 | `or` | Logical OR |
Within a compound expression, the rule engine evaluates expressions from the highest-ranked operations and then proceeds to evaluate lower-ranked expressions.
[]Deception supports different types of constants to build expressions for filters and rule conditions. The following table lists all types of supported constants:
| Constant | Description |
| -------- | ----------- |
| `True, true` | Boolean True |
| `False, false` | Boolean False |
| `null` | Represents an undefined value |
| `1`, `2`,`-3`,... | Integer constant |
| `1`, `0.1`, `-.2`,... | Decimal constant |
| `"something"` | String constant |
| `'2016-10-12T6:7:8Z'` | DateTime constant |
| `'2016-10-9'` | Date constant |
| `'6:7:8Z'`, `'7am'` | Time constant |
| `[1,2,"test",0.1]` | List constant |
- String constants are enclosed in double quotation marks.
- Date, Time, and DateTime constants are enclosed in single quotation marks.
- Dates cannot be extracted from the `timestamp` identifier in the Investigate module.
- The format for date constant is `timestamp::date is '2016-10-24'`.
- `12 AM` denotes midnight and `12 PM` denotes noon.
- List constants are enclosed in square brackets. Lists can be heterogeneous (containing items of different data types) or homogeneous (containing items of the same data type). However, heterogeneous lists are supported only in the [Orchestrate module](/deception/about-orchestration-rules).
- Lists cannot contain identifiers. However, it allows all constants including `null`. You can also have nested lists (lists within a list) and recursive lists (lists containing the same items). Example: `[["Get-Alias", "Out-Default"], ["Get-Alias"], "Set-StrictMode"]`.
- The keyword `now` can be used with date and time constants to add or subtract values relative to the current date or time. Example: `timestamp after 'now - 7 days' and timestamp between 'now - 2 hours' and 'now + 2 hours'`.
Single Constant or Identifier Expressions
The simplest expressions you can write can contain simple constants such as:
- `true` returns all events.
- `0` evaluates to false and returns nothing.
- `1` evaluates to true and returns all events.
- `"Hello"` evaluates to false and returns all events.
- `false` returns nothing.
- `[1,2,3]` evaluates to `true` and returns all events.
- `null` returns nothing.
While single constant expressions have no identifiers, they are still valid and are checked against all events. The evaluation of a single constant expression depends on whether the constant is truthful. The truthfulness of single constants is determined as follows:
- Boolean `true` evaluates to `true`.
- `null `is always `false`.
- Integers other than `0` evaluate to `true`.
- Decimals other than `0` evaluate to `true`.
- Strings evaluate to `true` for non-empty strings.
- Dates/times are always `true`.
- Lists evaluate to `true` for non-empty lists.