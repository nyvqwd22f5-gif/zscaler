# ZSDK Integration Guide for iOS
Source: https://help.zscaler.com/zsdk/zsdk-integration-guide-ios
PDF: https://help.zscaler.com/pdf/com/en/1514276.pdf

This guide provides steps on how to integrate ZSDK into your mobile iOS applications.
Prerequisite
Ensure your application is running on iOS 15 or later.
Import ZSDK
You can import ZSDK in one of the following ways:
- [SwiftPM](#swiftPM)
- [CocoaPods](#cocoapods)
- [Manual Import](#manual)
ZSDK Integration
Ensure that you have imported ZSDK on Xcode.
`import Zscaler`
Initialize a shared instance of the ZSDK interface.
`let zscalerSDK = ZscalerSDK.sharedInstance()`
Start the Prelogin tunnel.
`func startPreLoginTunnel() async throws {
let appKey = "yourAppKey"
let deviceUdid = UIDevice.current.identifierForVendor?.uuidString ?? "Unknown"
await ZscalerSDK.sharedInstance().startPreLoginTunnel(appKey: appKey, deviceUdid: deviceUdid)
}`
Start the Zero Trust tunnel.
`func startZeroTrustTunnel() async throws {
let appKey = "yourAppKey"
let deviceUdid = UIDevice.current.identifierForVendor?.uuidString ?? "Unknown"
let accessToken = "JWT access token"
await ZscalerSDK.sharedInstance().startZeroTrustTunnel(appKey: appKey, deviceUdid: deviceUdid, accessToken: accessToken)
}`
Stop tunnel operations.
`func stopTunnel() async {
ZscalerSDK.sharedInstance().stopTunnel()
}`
Manually configure a `URLSession` or `WebView`.
`func setupSession() -> URLSession {
let config = URLSessionConfiguration.ephemeral
ZscalerSDK.sharedInstance().configure(sessionConfiguration: config)
return URLSession(configuration: config)
}
func setupWebview() async -> WKWebView {
let webView = await WKWebView()
await ZscalerSDK.sharedInstance().setup(websiteDataStore: webView.configuration.websiteDataStore)
return webView
}`
Check the tunnel status.
`func fetchStatus() -> String {
// The status API returns an NSString which is automatically bridged to String in Swift
let status = ZscalerSDK.sharedInstance().status().tunnelConnectionState
return status
}`
Access proxy information.
`func getProxyInfo() {
let proxyInfo = ZscalerSDK.sharedInstance().proxyInfo
let host = proxyInfo.proxyHost
let port = proxyInfo.proxyPort
let username = proxyInfo.username
let password = proxyInfo.password
}`
Export debug logs.
`func exportLogs() {
let destinationDir = URL.documentsDirectory.absoluteString
let logFile = ZscalerSDK.sharedInstance().exportLogs(destination: destinationDir)
// Export a shareable file
}`
Delete debug logs.
`func clearLogs() {
ZscalerSDK.sharedInstance().clearLogs()
}`
[]
- Go to **File** > **Swift Packages** > **Add Package Dependency**.
-
Enter the repository URL for ZSDK.
`http://github.com/zscaler/zscaler-sdk-ios`
- Save your package-dependency configuration.
[]
- Edit or create a Podfile.
-
Enter the following on the Podfile:
`pod 'ZscalerSDK', :git => 'https://github.com/zscaler/zscaler-sdk-ios'`
- Enter `pod install` to begin importing ZSDK.
[]
-
Download a ZIP file of the `ZscalerSDK.xcframework` release from [GitHub](https://github.com/zscaler/zscaler-sdk-ios).
[See image.](#github)
- Unzip the downloaded file.
- Open your Xcode project.
- Go to **Frameworks** > **Libraries** > **Embedded Content**.
- Add the downloaded `ZscalerSDK.xcframework`.
- Select **Embed & Sign** for the **Embed** option.
[]
![Download ZscalerSDK.xcframework File from GitHub](/downloads/zsdk/zscaler-sdk-developer-guide/application-types/zscaler-sdk-integration-guide-ios/zsdk-ios-download-white.png)