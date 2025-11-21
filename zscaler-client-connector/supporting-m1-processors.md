# Supporting M1 Processors
Source: https://help.zscaler.com/zscaler-client-connector/supporting-m1-processors
PDF: https://help.zscaler.com/pdf/com/en/1374111.pdf

Zscaler Client Connector [version 2.2.4](/zscaler-client-connector/client-connector-app-release-summary-2020?applicable_category=macOS&applicable_version=2.2.4) is compatible with M1 processors in Mac devices by using the [Rosetta translation process](https://developer.apple.com/documentation/apple_silicon/about_the_rosetta_translation_environment?language=objc). New installations on M1 systems are fully supported through the Mac device's user interface.
Currently, for version 2.2.4, new installations are not fully supported using the command line. However, you can install version 2.2.4 from the command line by using one of the following workaround options:
sudo Zscaler-osx-2.2.4.0-installer.app/Contents/MacOS/osx-x86_64 <Pass Additional Installation Arguments as Needed>
arch -x86_64 /bin/sh
Zscaler-osx-2.2.4.0-installer.app/Contents/MacOS/installbuilder.sh <Pass Additional Installation Arguments as Needed>