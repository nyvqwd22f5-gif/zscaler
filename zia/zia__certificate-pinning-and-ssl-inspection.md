# Certificate Pinning and SSL Inspection
Source: https://help.zscaler.com/zia/certificate-pinning-and-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1400776.pdf

Certificate pinning is a process in which a non-browser desktop/mobile application validates that the TLS certificates presented by the application's back end TLS web servers match a known set of certificates pinned or hardcoded in the application. This process helps secure applications from man-in-the-middle (MITM) attacks. In such attacks, a MITM can respond to the client SSL handshake request with a forged server certificate issued by a trusted certificate authority (CA), blindsiding the client.
Zscaler dynamically issues trusted MITM certificates signed by the Zscaler intermediate CA or by the customer's specific intermediate CA to intercept the TLS traffic. The certificate-pinned clients might not be able to match those certificates to the pinned application certificates, leading to a termination of the connection.
Impacts of Certificate Pinning and SSL Inspection
ZIA Public Service Edges cannot detect certificate pinning as there is no specific messaging from the client indicating that it has a pinned certificate. In this situation, there is no response to the Server Certificate sent to the client, and the connection fails. There might be situations where the client closes the connection with a FINISH (FIN) or a RESET (RST) flag, but this is not sufficient to detect pinning and take corrective action.
As certificate pinning is a client-side function, the failure of the SSL connection happens between the client and the proxy. There is no standard behavior that is seen across clients while terminating a connection due to certificate pinning. The client might choose to close the connection any time after the Server Certificate is received, either by terminating the handshake with a fatal error stating the reason as “Unknown CA” or by generating an Encrypted Alert (close notify) after the SSL handshake followed by a FIN. In some cases, the client just resets the connection without the exchange of any application data. Whatever the behavior, the SSL connection fails.
Options When Encountering Certificate Pinning and SSL Inspection
To prevent applications that use certificate pinning from breaking in these circumstances, exempt the applications from SSL Inspection. You can achieve this by exempting either the cloud application from [SSL Inspection](/zia/about-ssl-inspection) or the individual domains from [SSL Inspection](/zia/about-ssl-inspection) using the [Custom URL categories](/zia/adding-custom-url-categories).
Native Applications That Use Certificate Pinning
The following table shows native applications that use certificate pinning:
[](https://helpx.adobe.com/enterprise/kb/network-endpoints.html#main-pars_header_474584398)
[](https://helpx.adobe.com/enterprise/kb/network-endpoints.html#main-pars_header_125062885)
[](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/endpoints.html#feature-endpoints)
[](https://docs.aws.amazon.com/workspaces/latest/adminguide/workspaces-port-requirements.html#gateway_IP)
[](https://support.apple.com/en-us/HT210060)
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
[](https://support.goto.com/webinar/help/optimal-firewall-configuration-g2w060025)[](/zia/configuring-advanced-url-policy-settings#ucaas)
[](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-proxy-internet?view=o365-worldwide#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)
[](https://support.signal.org/hc/en-us/articles/360007320291-Firewall-and-Internet-settings)
| Name | Platform | Domains | Error Message | Notes |
| ---- | -------- | ------- | ------------- | ----- |
| Adobe Acrobat Reader (Fill & Sign) | All | .acrobat.com.echosign.com.echocdn.com.bam.nr-data.net.newrelic.com | N/A | To learn more about the FQDNs that are required for Adobe Acrobat Services, refer to the Adobe product support page. |
| Adobe Creative Cloud | All | N/A | N/A | To learn more about the non-browser-based FQDNs, refer to the Adobe product support page. |
| Adobe Updates | All | platformdl.adobe.comfpdownload.adobe.comsstats.adobe.comget3.adobe.comget.adobe.comstats.adobe.comdlmping3.adobe.comdlmping2.adobe.com | N/A | To learn more, refer to the Adobe product support page. |
| AirBnB | Mobile - All | N/A | Unfortunately, a connection error prevented your request from being sent | N/A |
| Amazon Alexa | Mobile - iOS | N/A | Blank screen | N/A |
| Amazon Workspaces | All | .amazonaws.com.amazonworkspaces.com.awsapps.com.cloudfront.net | N/A | On the Firewall, define a network service, "Allow connection to PCoIP - Amazon Workspaces" to allow the destination ports 4172 and 4195. To learn more, refer to the Amazon Workspace support page. |
| Apple iMessage | All | p24-keyvalueservice.icloud.com | No error | iMessage on OSX and iOS fails to send or receive messages unless this URL is bypassed. |
| Apple iTunes and App Store | All | .apps.apple.com.itunes.apple.com.mzstatic.comgs-loc.apple.comgsa.apple.comsecuremetrics.apple.comswscan.apple.comxp.apple.com.icloud.comppq.apple.comakadns.net | Various errors stating server not available | Without bypasses, iTunes and App Store partially work, but many icons don't appear and apps cannot be downloaded or purchased unless these URLs are bypassed. To learn more, refer to the Apple product support page. |
| Apple Mail App | All | .mail.me.com | N/A | Bypass the Apple site for your email app to use an iCloud email account. |
| Blizzard Online Games | All | .battle.net.blizzard.comblzddist1-a.akamaihd.netblzddist2-a.akamaihd.net | N/A | Game updates and Battle.net updates are not download. No error message. |
| Chase | Mobile - All | N/A | Temporarily unable to connect | N/A |
| Circa | Mobile - All | N/A | Offline error | N/A |
| Dropbox | All | N/A | Cannot log in | N/A |
| Evernote | All | announce.evernote.comcd1.evernote.comevernote-a.akamaihd.netwww.evernote.com | Cannot log in | Evernote sites require bypass in order for the application to work natively. Without the bypass, it will not work for native apps but will work through a browser. Alternatively, select the Evernote Application instead of URLs. |
| Facebook | Mobile - All | N/A | Connection error | N/A |
| Facebook Messenger | Mobile - All | N/A | Connection error | Facebook App bypass can be used. For web only there is also a Facebook - Web IM. |
| Google - Shared Services, Drive, etc. | All | .clients.google.com.googleapis.comaccounts.gstatic.comaccounts.google.comaccounts.youtube.comclient3.google.comclients1.google.comclients2.google.comclients3.google.comclients4.google.comclients5.google.comclients6.google.comconnectivitycheck.gstatic.comcros-omahaproxy.appspot.comomahaproxy.appspot.comdl-ssl.google.comdl.google.comm.google.comsafebrowsing-cache.google.comsafebrowsing.google.comssl.gstatic.comtools.google.compack.google.comwww.gstatic.com | N/A | Google Drive can be configured to ignore its certificate pinning with the following CLI switch - `googledrivesync.exe --unsafe_network`Google does certificate pinning for various services, but it is platform dependent. Only bypass all URLs if the app is breaking.For example, in order to get the Google Drive agent to work properly, you need to bypass some of these shared services like the accounts.google.com. |
| Google Hangouts | All | Minimum:accounts.google.com.accounts.google.com.client-channel.google.com.googleusercontent.comapis.google.com.googleapis.comconnectivitycheck.gstatic.com.clients.google.com.clients1.google.com.clients2.google.com.clients3.google.com.clients4.google.com.clients5.google.com.clients6.google.com.gstatic.comOptional:.appspot.com.client-channel.google.com.googleusercontent.com.video.google.comIf Hangouts still doesn't work, also add these Apps to SSL bypass:Google HangoutsGoogle VideoGoogle+Google App for BusinessGoogle Groups | Video won't load | Behavior is inconsistent. Zscaler recommends only doing the Google shared services bypasses (in the Google Shared Services entry) if the performance is lacking or Hangouts doesn't work. If this is the case, add all these URLs to bypass list. |
| Google Play store | Android | .gvt1.com.gvt2.com.vzw.com.ggpht.complay.googleapis.comandroid.clients.google.com.googleapis.com.googleusercontent.com.ggpht.com.google-analytics.com.googlesyndication.com.doubleclick.net.android.clients.google.com.play.googlezip.netconnectivitycheck.gstatic.com | N/A | N/A |
| Hype Machine | Mobile - All | N/A | Network Failure | N/A |
| Instagram | Mobile - All | .instagram.com | Couldn't Refresh Feed | N/A |
| iOS App Store | Mobile - All | N/A | Cannot connect to App Store | N/A |
| Join.me | All | N/A | App hangs while trying to connect | N/A |
| GoTo Applications | Browser - All | N/A | Connection fails | To learn more about the recommended FQDNs that can be bypassed, refer to the GoTo Support page. To learn more about GoTo one-click option, see Unified Communications as a Service (UCaaS). |
| Microsoft Defender | All | N/A | N/A | To learn more about the Microsoft Defender ATP service domains, refer to the Microsoft product support page. |
| MyFitnessPal | Mobile - All | N/A | N/A | The app seems to run but large portions of content are missing. |
| Netflix | Mobile - All | N/A | Currently Unavailable | Can browse the catalog, but streaming fails. |
| Microsoft 365 | All | N/A | N/A | Use Office365 One-Click Configuration in Policy > URL & Cloud App Control > Advanced Settings. |
| Overcast | Mobile - All | N/A | No Internet Connection | N/A |
| PayPal | Mobile - All | N/A | Cannot log in | N/A |
| People Graph | Windows | appsforoffice.microsoft.com | Blank Graph | Auth Bypass needed as well: .oaspapps.com |
| Periscope | Mobile - All | N/A | N/A | You cannot find any live broadcasts and fails to load any video content. |
| Signal | All | .whispersystems.org.signal.org | N/A | To learn more about the non-browser-based domains that are required for Signal, refer to the Signal product support page. |
| Snapchat | Mobile - iOS | app.snapchat.com | Could not refresh. Try again. | N/A |
| SoundCloud | Mobile - All | N/A | Loading error. Something went wrong. | N/A |
| Southwest Mobile App | Mobile - iOS | mobile.southwest.comsmetrics.southwest.com | Cannot connect | N/A |
| Spotify | Mobile - All | N/A | An error occurred, though locally-stored music can still be played | N/A |
| Timehop | Mobile - All | N/A | N/A | The app loads but fails to pull in iCloud photos and Facebook content. |
| TrainingPeaks | Mobile - All | N/A | No Internet Connection | N/A |
| X | Mobile - All | N/A | N/A | The app loads but cannot pull in new content. |
| Vimeo | Mobile - All | N/A | Something strange occurred. Sorry about that. | N/A |
| Windows Store | Windows | eus-streaming-video-msn.com.akamaized.net.wns.windows.com.live.com.clientconfig.passport.net.wustat.windows.com.windowsupdate.com.msftncsi.com.microsoft.com | N/A | The Windows Store and various apps built into Windows 8.x/10 do not load properly, allow sign in, and various other issues if these URLs do not get bypassed. |
| Xbox Live | Windows | device.ra.live.comlogin.live.comaccounts.live.comdevice.auth.xboxlive.comtitle.mgt.xboxlive.comtitle.auth.xboxlive.comuser.auth.xboxlive.comxsts.auth.xboxlive.comdlassets.xboxlive.comimages-eds.xboxlive.compf.directory.live.comprivacy.xboxlive.comprofile.xboxlive.com | N/A | Native Xbox Live on Windows 8.x/10 does not work or allow login if these URLs are not bypassed |
| Yahoo Weather | Mobile - All | N/A | Cannot Get Weather | N/A |
| Yelp | Mobile - All | N/A | An SSL error has occurred and a secure connection to the server cannot be made | N/A |
| Yik Yak | Mobile - All | N/A | No Yaks | N/A |