# ZSDK Integration Guide for Android
Source: https://help.zscaler.com/zsdk/zsdk-integration-guide-android
PDF: https://help.zscaler.com/pdf/com/en/1514266.pdf

This guide provides steps on how to integrate ZSDK into your mobile Android applications. ZSDK supports Java or Kotlin when you are importing ZSDK into an Android application.
Prerequisites
To begin installing ZSDK in a mobile Android application, ensure:
- You're running Android 9 or later (i.e., minimum API Level 28).
- Your Android application works on both 32-bit and 64-bit devices that are ARM-based (i.e., armeabi-v7a or arm64-v8a).
Import ZSDK
To begin importing ZSDK by using Android Studio or your Integrated Development Environment (IDE) of choice:
- Ensure `gpr.user` and `gpr.key` are set to your GitHub username and access token in the `local.properties`.
-
Add the following `dependencyResolutionManagement` repository to the GitHub repository in the `settings.gradle`:
`dependencyResolutionManagement {
repositories {
maven {
name = "ZscalerSDKAndroid"
url = uri("https://maven.pkg.github.com/zscaler/zscaler-sdk-android")
credentials {
username = settings.extra.get("gpr.user") as String ?: System.getenv("GITHUB_USERNAME")
password = settings.extra.get("gpr.key") as String ?: System.getenv("GITHUB_TOKEN")
}
}
}`
-
Add the following dependencies section to your `build.gradle`:
`dependencies {
implementation("com.zscaler.sdk:zscalersdk-android:latest.release")
}`
Manual Import of ZSDK
Alternatively, you can import ZSDK through manual integration:
-
On [ZSDK's GitHub](https://github.com/zscaler/zscaler-sdk-android/), click the latest **Package URL** under **Packages**.
[See image.](#img_githubpkg)
- Download the latest ZSDK `.aar` file at the bottom of **Assets**.
- Launch Android Studio or your selected IDE.
- Open an existing project or create a new project in **Project View** where you intend to integrate ZSDK.
- Create a `libs` directory adjacent to your app's `SRC` directory or use an existing one.
- Add the ZSDK `.aar` file into the **libs** directory. Rename the file to `zscalersdk.aar` for easier reference.
- Open the `build.gradle(:app)` file to configure the implementation pathway.
-
Add the following line to include the ZSDK library for your project:
`// Add Path to the ZscalerSDK .aar file
implementation(files("libs/zscalersdk.aar"))`
- Execute **Gradle Sync** to ensure all configurations are properly loaded and the ZSDK library is integrated into your project build.
ZSDK Integration
Ensure that you have imported ZSDK and its methods.
`import com.zscaler.sdk.android.ZscalerSDK`
Initialize ZSDK in your custom application's or `MainActivity`'s `onCreate()` to pass your application instance.
`override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
binding = ActivityMainBinding.inflate(layoutInflater)
try {
ZscalerSDK.init(application, ZscalerSDKConfiguration.DEFAULT_CONFIGURATION)  // you may provide custom configuration
} catch (e: ZscalerSDKException) {
Log.e(TAG, "Got exception while initializing ZscalerSDK = $e")
// Tunnel won't work after this
return
}
}`
Start the Prelogin tunnel.
`// Define function to start the PreLogin tunnel
fun startPreLoginTunnel(zdkId: String,
udid : String,
onErrorOccurred: (errorCode: Int) -> Unit) {
viewModelScope.launch(Dispatchers.IO) {
try {
ZscalerSDK.startPreLoginTunnel(appKey = appKey, deviceUdid = udid)
Log.d(TAG, "startPreLoginTunnel completed")
} catch (e: Exception) {
Log.e(TAG, "startPreLoginTunnel() failed with exception :: ${e.message}")
}
}
}`
Start the Zero Trust tunnel.
`// Define function to establish Zero Trust tunnel
fun startZeroTrustTunnel(
zdkId: String,
accessToken: String,
udid: String,
onErrorOccurred: (errorCode: Int) -> Unit
) {
viewModelScope.launch(Dispatchers.IO) {
try {
ZscalerSDK.startZeroTrustTunnel(appKey = appKey, deviceUdid = udid, accessToken = accessToken)
Log.d(TAG, "startZeroTrustTunnel completed")
} catch (e: Exception) {
Log.e(TAG, "startZeroTrustTunnel() failed with exception :: ${e.message}")
}
}
}`
Stop tunnel operations.
`fun stopTunnel(resetStatusText:()-> String): Unit {
Log.d(TAG, "stopTunnel() called")
try {
val retVal = ZscalerSDK.stopTunnel()
if (retVal == 0) zdkStatus.value = resetStatusText()
} catch (e: Exception) {
Log.e(TAG, "stopTunnel() failed with exception :: ${e.message}")
}
}`
Check the tunnel status.
`fun getStatus() {
val zscalerSDKTunnelStatus = ZscalerSDK.status()
Log.d(TAG, "getStatus() called tunnelType:${zscalerSDKTunnelStatus.tunnelType} status:${zscalerSDKTunnelStatus.tunnelConnectionState}")
}`
Export debug logs.
`//destination is URI of an empty zip file path where you want the logs
fun exportLog(destination: String): String {
val exportLogDestination = ZscalerSDK.exportLogs(destinationFolder = destination).toString()
Log.d(TAG, "exportLog() called with: destination = $exportLogDestination")
return exportLogDestination
}`
Delete debug logs.
`fun clearLogs(onSuccess: () -> Unit) {
viewModelScope.launch(Dispatchers.IO) {
ZscalerSDK.clearLogs()
withContext(Dispatchers.Main) {
onSuccess()
}
}
}`
Managing Network Configurations
You can manage network configurations with Semi-Automatic or Manual mode by setting `automaticallyConfigureRequests` or `automaticallyConfigureWebViews` to **false**.
Semi-Automatic Mode
For Semi-Automatic mode, you can set up ZSDK to custom retrofit the client or WebView with the following code sample:
`fun loadWithSemiAutomaticConfig(url: String) {
val apiService = ZscalerSDK.setUpClient(null, url)?.create(ApiService::class.java)
viewModelScope.launch(Dispatchers.IO) {
try {
val response = apiService?.getData(url)?.execute()
// parse the response data based on your app's logic
} catch (e: IOException) {
//Print exception
e.printStackTrace()
}
}
}
fun loadInWebViewWithSemiAutomaticConfig(url: String) {
val zscalerSDKWebView = ZscalerSDK.setUpWebView()
zscalerSDKWebView?.loadUrl(url)
}`
Manual Mode
For Manual mode, if you are using WebView and after you start a tunnel, you must configure the WebView proxy settings to route traffic over the tunnel. The following code sample shows how you can do this for `retrofit` by creating your app's own custom `OkHttpClient`:
`object ManualRetrofitApiClient {
private var TAG = "ManualRetrofitApiClient"
private var retrofit: Retrofit? = null
private var baseUrl: String = ""
fun getRetrofit(baseUrl: String): Retrofit? {
if (retrofit == null || ManualRetrofitApiClient.baseUrl != baseUrl) {
val zscalerClient = getZscalerOkHttpClient() // this is required to send traffic via ZscalerSDK
ManualRetrofitApiClient.baseUrl = baseUrl
retrofit = Retrofit.Builder()
.baseUrl(baseUrl)
.client(zscalerClient)
.addConverterFactory(GsonConverterFactory.create())
.build()
}
return retrofit
}
private fun getZscalerOkHttpClient(): OkHttpClient {
// call ZscalerSDK.proxyInfo() to fetch proxy details
val proxyInfo = ZscalerSDK.proxyInfo()
// set proxy using proxyHost and proxyPort
ProxySelector.setDefault(object : ProxySelector() {
override fun select(uri: URI?): MutableList<Proxy> {
val proxyList = mutableListOf<Proxy>()
proxyList.add(Proxy(Proxy.Type.HTTP, InetSocketAddress(proxyInfo.proxyHost, proxyInfo.proxyPort)))
return proxyList
}
override fun connectFailed(uri: URI?, sa: SocketAddress?, ioe: IOException?) {
Log.d(TAG, "connectFailed : with: uri = $uri, SocketAddress = $sa, IOException = ${ioe?.message}")
}
})
val builder = OkHttpClient.Builder()
// set authenticator using username and password present in proxyInfo
val username = proxyInfo.username
val password = proxyInfo.password
if (username?.isNotEmpty() == true && password?.isNotEmpty() == true) {
val authenticator = Authenticator { _: Route?, response: Response ->
val credential = Credentials.basic(username, password)
response.request.newBuilder()
.header("Proxy-Authorization", credential)
.build()
}
builder.proxyAuthenticator(authenticator)
}
return builder.build()
}
}`
WebView Proxy Settings
After starting any tunnel, you must configure the WebView proxy settings to route network traffic over the tunnel.
WebView network connections are not guaranteed to use new proxy settings immediately when applied. Wait for a successful listener callback before loading a page. To learn more about Android's ProxyController, refer to [Android Documentation](https://developer.android.com/reference/androidx/webkit/ProxyController).
`fun setWebViewProxy(proxyInfo: ZscalerSDKProxyInfo) {
if (isWebKitClassAvailable()) {
if (WebViewFeature.isFeatureSupported(WebViewFeature.PROXY_OVERRIDE)) {
val proxyConfig = ProxyConfig.Builder()
.addProxyRule("${proxyInfo.proxyHost}:${proxyInfo.proxyPort}")
.build()
ProxyController.getInstance().setProxyOverride(proxyConfig,
{
//on success
Log.d(TAG, "setProxyInWebView: setProxyOverride success")
},
{
Log.e(TAG, "setProxyInWebView: Failed to set proxy in WebView")
})
} else {
Log.e(TAG, "setProxyInWebView: WebView proxy override not supported")
}
} else {
Log.e(TAG, "setProxyInWebView: Androidx Webkit dependencies not found")
}
}
private fun isWebKitClassAvailable(): Boolean {
try {
Class.forName("androidx.webkit.WebViewFeature")
Class.forName("androidx.webkit.ProxyController")
return true
} catch (e: Exception) {
Log.e(TAG, "isWebKitClassAvailable: Androidx Webkit dependencies not found")
}
return false
}`
ProxyAuth Override
If `ProxyAuth` is enabled, then you need to override the `ReceivedHttpAuthRequest()` method in your `WebViewClient`.
`class WebViewClientWithProxyAuthSupport(private val proxyInfo: ZscalerSDKProxyInfo) : WebViewClient() {
override fun onReceivedHttpAuthRequest(view: WebView?, handler: HttpAuthHandler?, host: String?, realm: String?) {
if (proxyInfo.username?.isNotEmpty() == true && proxyInfo.password?.isNotEmpty() == true) {
handler?.proceed(proxyInfo.username, proxyInfo.password)
}
super.onReceivedHttpAuthRequest(view, handler, host, realm)
}
}`
[]
![Click the Package URL](/downloads/zsdk/zscaler-sdk-developer-guide/application-types/zscaler-sdk-integration-guide-android/ZSDK-Android-GitHub-Packages-1.png)