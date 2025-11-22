# Recommended File Type Control Policy
Source: https://help.zscaler.com/zia/recommended-file-type-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1398801.pdf

When [configuring](/zia/how-do-i-configure-file-type-control-policy) the [File Type Control policy](/zia/about-file-type-control), Zscaler recommends using:
- Caution action for Executable downloads from websites under any URL category
- Block action for Executable uploads to websites under any URL category
If you have Advanced Sandbox, you can configure your Sandbox policy to [quarantine](/zia/configuring-sandbox-policy#first-time-action) executable downloads for the first-time action.
Depending on your corporate policy, you can also add additional rules to block downloads from specific URL categories, such as Adult Material, Drugs, Gambling, Illegal or Questionable, Militancy/Hate and Extremism, Tasteless, Violence, and Weapons/Bombs, etc.
Example File Type Control Rules
The following are examples of the File Type Control policy rules that Zscaler recommends:
File Type Control Rule #1
- **Rule Order**: 1
- **Rule Status**: Enabled
- **File Types**: Executable
- **URL Categories**: Any
- **Users**: Any
- **Groups**: Any
- **Departments**: Any
- **Locations**: Any
- **Location Groups**: Any
- **Time**: Always
- **Protocols**: Any
- **Action**: Caution
- **Upload/Download**: Download
File Type Control Rule #2
- **Rule Order**: 2
- **Rule Status**: Enabled
- **File Types**: Select all file types
- **URL Categories**: Any
- **Users**: Any
- **Groups**: Any
- **Departments**: Any
- **Locations**: Any
- **Time**: Always
- **Protocols**: Any
- **Action**: Allow
- **Upload/Download**: Download