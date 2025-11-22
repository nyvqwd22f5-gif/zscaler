# Defining Regular Expression Values
Source: https://help.zscaler.com/unified/defining-regular-expression-values
PDF: https://help.zscaler.com/pdf/com/en/1493681.pdf

When [configuring custom controls](/unified/configuring-custom-controls), some allow you to define with regular expressions (regex) values. The characters and limitations are:
- [Metacharacters Supported by Zscaler](#Metachar)
- [Shorthand Character Classes Supported by Zscaler](#Char-class)
- [No Nested Repeats](#Nested)
- [Base Token Requirement](#Token)
[]
| Metacharacter (POSIX ERE) | Definition | Supported by Zscaler? |
| ------------------------- | ---------- | --------------------- |
| . | Matches any single character | Supported |
| [] | Matches a single character from those given between the brackets, matches character ranges (e.g., [a-z]) | Supported |
| [^ ] | Matches a single character not from those given between ^ and ] | Supported |
| ^ | Matches the starting position within the string | Not Supported |
| $ | Matches the ending position within the string | Not Supported |
| () | Defines a capture group | Capture groups are not supported. Parentheses can be used for bounding subexpressions. |
| \*n* | References a capture group | Not Supported |
| * | Repeats the preceding element 0 or more times | Supported |
| {*m*,*n*} | Matches the preceding element at least *m* times and not more than *n* times. Requires *m* is less than or equal to *n*. | Both *m* and *n* must be between 0 and 100. A value for *n* is required, but *m* can be omitted (0 is assumed). |
| ? | Repeats the preceding element 0 or 1 times | Supported |
| + | Repeats the preceding element 1 or more times | Supported |
| | | Matches either the expression before or the expression after the operator (e.g., "abc|def" matches "abc" or "def") | Supported |
[]
| Character class | Definition | Supported by Zscaler? |
| --------------- | ---------- | --------------------- |
| \d | Matches any single character that is a digit (i.e. [0-9]) | Supported |
| \D | Matches any single character that is a non-digit | Supported |
| \s | Matches any single horizontal whitespace character across a single line (i.e. a space " " or tab) | Supported |
| \S | Matches any single non-whitespace character | Supported |
| \w | Matches any single word character (i.e. ASCII characters [A-Za-z0-9_]) | Supported |
| \W | Matches any single non-word character | Supported |
| \b | Matches any single word boundary | Supported |
[]A repeat of an expression containing a repeat (*, +, ?, or {*m*,*n*}) is not supported. The prohibited repeated elements are in red text below:
| Incorrect Usage | Correct Usage |
| --------------- | ------------- |
| \d-[A-Z]{2}?X *- Matches "5-X" or "5-GAX"* | \d-([A-Z][A-Z])?X |
| (\d{3}-){1,2}\d{4} *- Matches "555-555-5555" or "555-5555"*\d{3}-(\d{3}-)?\d{4} | \d{3}-(\d\d\d-)?\d{4} |
[]The regex value must begin with a simple sequence of alphabetic and numeric characters of a known length called the "base token."
The first part can only include:
- literal alphabetic characters (e.g., "A")
- literal numeric characters (e.g., "5")
- special characters (e.g., "@", "#")
- classes of only alphabetic characters or numeric characters (e.g., "[A-N]", "\d")
- bounded repeats (e.g., "{3}", "{1,5}")
- 8 or fewer branches
- shorthand characters (e.g., "\b", "\s")
Shorthand characters can be followed by a special character (e.g., "\b%abc", "\s[%@]abc"). A base token can also have up to two nested shorthand characters (e.g., "\b\sabc", "\b[\s\W]abc").
The base token must end with an expression that is non-alphanumeric (e.g., ";"), or with the end of the regex value. The following are examples of valid and invalid base tokens (with the prohibited element in red text):
- The base token must be non-zero length.
Example - US phone numbers:
- *Incorrect Usage*: (1-)?\d{3}-\d{3}-\d{4} *- Starts with an optional expression.*
- *Incorrect Usage: (CA)-\d{6} - Starts with grouping.*
- *Correct Usage*: Use multiple values.
- 1-\d{3}-\d{3}-\d{4} *- Starts with a single-number token.*
- \d{3}-\d{3}-\d{4} *- Starts with a three-number token.*
- The initial sequence must be all alphabetic characters or all numeric characters. It cannot be both.
Example - IPv4 Address in dotted-quad notation:
- *Incorrect Usage*: [0-9.]{7,15} - *Ambiguous mix of numeric characters and punctuation.*
- *Correct Usage*: \d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3} - *Starts with 1-3 numeric characters.*
- Each expression after the initial one can match alphanumeric characters only (i.e., becoming part of the base token) or non-alphanumeric characters only (i.e., marking the end of the base token).
Example - US phone number:
- *Incorrect Usage*: \d{3}-?\d{3}-?\d{4} - *Second expression is optional.*
- *Correct Usage*: Use multiple values.
- \d{10} - Ten numeric characters, no delimiter.
- \d{3}-\d{3}-\d{4} - Delimited with ‘-’.
- The entire regex value can match just the base token.
Example - California driver’s license number:
- *Correct Usage*: [A-Za-z]\d{7} - Alphabetic characters followed by 7 numeric characters.
- Regex values only match at the beginning of a token, i.e., at the first alphabetic or numeric character after a non-alphabetic, non-numeric character.
Example - California driver’s license number:
- [A-Za-z]\d{7} - Alphanumeric characters followed by seven numeric characters.
- *Matches*: "A1234567", "-B7654321-"
- *Doesn’t Match*: "AA1234567"