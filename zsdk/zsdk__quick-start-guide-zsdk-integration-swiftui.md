# Quick Start Guide for ZSDK Integration with SwiftUI
Source: https://help.zscaler.com/zsdk/quick-start-guide-zsdk-integration-swiftui
PDF: https://help.zscaler.com/pdf/com/en/1530993.pdf

This guide provides steps on how to integrate ZSDK using SwiftUI so that you can quickly test and validate the security benefits of the Zscaler Zero Trust Exchange (ZTE) without requiring your own custom back end.
Prerequisites
Before starting, make sure you have:
- If you are using Xcode, Xcode version 16 or later
- If you are using an iOS device, iOS version 15.0 or later
- Auth0 client credentials
- Internet access to call the Zscaler-provided sample API endpoint at `https://zsdksample.n4rt.com`
ZSDK Integration Configuration
To integrate ZSDK using SwiftUI:
- [Step 1: Test an API Call without ZSDK](#create_swiftui)
- [Step 2: Add ZSDK via Swift Package Manager](#add_swiftui)
- [Step 3: Fetch a JSON Web Token (JWT) Access Token](#fetch)
- [Step 4: Start a Zero Trust Tunnel](#zerotrusttunnel)
- [Step 5: Retry the API Call](#retry)
- [Step 6: (Optional) Verify Mutual Transport Layer Security (mTLS) in Wireshark](#validate)
You’ve completed validating ZSDK’s client-side integration and the security benefits of ZTE. You can:
- Replace the sample IdP with your production IdP.
- Integrate real authentication flows to obtain tokens dynamically.
- Handle tunnel lifecycle events (e.g., reconnects, errors).
- Deploy your ZSDK integration to production environments.
To learn more, see [Zscaler SDK Developer Guide](/zsdk/zscaler-sdk-developer-guide).
[][]Attempt to call the protected endpoint without ZSDK. This test confirms that the API is inaccessible until the Zero Trust tunnel is established.
Failure is the expected response because Zscaler's ZTE hides protected endpoints from unauthorized apps. Since you have not established a Zero Trust tunnel, the DNS resolution and connection to `zsdksample.n4rt.com` fails.
`import SwiftUI
struct ContentView: View {
@State private var message: String = ""
var body: some View {
VStack(spacing: 20) {
Text("Zscaler SDK Demo").font(.title)
Button("Test Connection") {
testConnection()
}
Text(message).foregroundColor(.gray)
}
.padding()
}
func testConnection() {
guard let url = URL(string: "https://zsdksample.n4rt.com") else { return }
// Attempt to fetch the protected URL without Zscaler SDK
URLSession.shared.dataTask(with: url) { data, response, error in
if let error = error {
message = "Request failed: \(error.localizedDescription)"
print(message)
} else if let httpResponse = response as? HTTPURLResponse {
message = "Response status: \(httpResponse.statusCode)"
print(message)
}
}.resume()
}
}`
After running a test connection upon the request, the expected result is that the request fails with a network error or an **HTTP 4XX/5XX** status.
[]You can add ZSDK to your Swift Package Manager as a project:
- In Xcode, go to **File** > **Swift Packages** > **Add Packages**.
- Enter the repository URL: [`https://github.com/zscaler/zscaler-sdk-ios`](https://github.com/zscaler/zscaler-sdk-ios).
- Select the latest version or main branch.
- Add the package to your targeted app.
[]Use the Zscaler-provided sample Auth0 identity provider (IdP) to get a temporary JWT that expires after 24 hours.
`curl --request POST \
--url https://zdk-test.us.auth0.com/oauth/token \
--header 'content-type: application/json' \
--data '{"client_id":"JG0lm5eMqqegK3ZHgu3VDjjE0Cnz5p9X","client_secret":"wdA1BWpM_e7YvQAOmRH2F0_SLGmTdqZc3shFVO4bx6gvxplZwYfSUJjzB2O--sR-","audience":"https://zsdk-sample.app","grant_type":"client_credentials"}'`
This request uses Zscaler's demo Auth0 tenant with client credentials. A successful call returns a JSON with a JWT ``access_token``. Copy the value without quotes. The token expires after 24 hours, but you can refresh it by rerunning the command.
[]Start a Zero Trust tunnel using the provided app key from Zscaler, your device's universally unique identifier (UUID) from the OS, and access token.
-
Use the provided [app key](/zsdk/about-registered-apps):
`eyJhcHBfaWRlbnRpZmllcl9naWQiOjcyMDU3NjE2NjAzMjgzNDYzLCJvbmVfaWRlbnRpdHlfZnFkbiI6ImRlbW8uenNka3N0YWdpbmcuenNsb2dpbmFscGhhLm5ldCIsImhtYWNfc2VjcmV0IjoiYXQrTzR6ZmhoY1d0Tk9WR2xjVXYzNjNiSTBBamxObEdnT1poendkdjdITT0ifQ==`
-
Add the app key, UUID, and access token to start a Zero Trust tunnel as follows:
`import ZscalerSDK
import UIKit // for UIDevice
func connectZeroTrustTunnel(accessToken: String) {
let appKey = "eyJhcHBfaWRlbnRpZmllcl9naWQiOjcyMDU3NjE2NjAzMjgzNDYzLCJvbmVfaWRlbnRpdHlfZnFkbiI6ImRlbW8uenNka3N0YWdpbmcuenNsb2dpbmFscGhhLm5ldCIsImhtYWNfc2VjcmV0IjoiYXQrTzR6ZmhoY1d0Tk9WR2xjVXYzNjNiSTBBamxObEdnT1poendkdjdITT0ifQ=="
let deviceId = UIDevice.current.identifierForVendor?.uuidString ?? "UNKNOWN"
Task {
do {
try await ZscalerSDK.sharedInstance().startZeroTrustTunnel(
appKey: appKey,
deviceUdid: deviceId,
accessToken: accessToken
)
print("Zero Trust tunnel connected!")
} catch {
print("Failed to start tunnel: \(error)")
}
}
}`
Use the `@State` variable to display the connection status in your SwiftUI.
You can set `@State var status` and configure it when the tunnel connects to show a **Connected** status in the UI. The following example is a basic approach to how you can set `@State var status`. Depending on your own environment, it can differ.
- [Basic Approach Example](#basic)
[]
`import SwiftUI
import Combine
import Zscaler
struct TunnelView: View {
@State var status: String = ""
var cancellables: [AnyCancellable] = []
init() {
let notificationNames: [NSNotification.Name] = [
.ZscalerSDKTunnelDisconnected, .ZscalerSDKTunnelConnected, .ZscalerSDKTunnelResourceBlocked,
.ZscalerSDKTunnelReconnecting, .ZscalerSDKTunnelAuthenticationRequired
]
for name in notificationNames {
NotificationCenter.default.publisher(for: name)
.receive(on: DispatchQueue.main)
.sink { _ in
status = ZscalerSDK.sharedInstance().status().tunnelConnectionState
}
.store(in: &cancellables)
}
}
var body: some View {
Text(status)
}
}`
[]With the Zero Trust tunnel active, try [calling the sample API again](#call_again):
If the request is successful, the response is:
`Hey there! Congratulations, your connection to the web server at zsdksample.n4rt.com is secured by Zscaler with end-to-end mTLS :-)`
If the request failed:
- Verify and validate the access token and app key.
- Check the Xcode console output for error messages from ZSDK.
- Check [ZSDK error messages](/zsdk/developer-reference#zscalererror).
[]To confirm that traffic is encrypted with end-to-end mTLS:
- Run the app in the iOS Simulator or on a device on the same network as your macOS device.
- Start a packet capture in [Wireshark](https://www.wireshark.org/).
- Filter for `tls` and `tcp;port==443`.
- Verify that only encrypted TLS traffic is visible. For example, ensure no plaintext hostnames (i.e., `zsdksample.n4rt.com`) or payload data.