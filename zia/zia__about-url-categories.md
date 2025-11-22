# About URL Categories
Source: https://help.zscaler.com/zia/about-url-categories
PDF: https://help.zscaler.com/pdf/com/en/1399361.pdf

[Watch a video about URL Categories.](https://fast.wistia.net/embed/iframe/s0t5xjry8a)
Zscaler organizes URLs into a hierarchy of categories for granular filtering and policy creation. There are six predefined classes, which are then each divided into predefined super categories, and then further divided into predefined categories.
For example, the Bandwidth Loss class includes categories such as video and music streaming because they are typically known to consume more bandwidth than other categories. These classes are also customizable, so if you think that video streaming should not be classified under Bandwidth Loss, you can manually move it to another classification that works best for you and your organization.
The six predefined classes are:
- [Bandwidth Loss](#bandwidth)
- [Business Use](#Business)
- [General Surfing](#Surfing)
- [Legal Liability](#Legal)
- [Productivity Loss](#Productivity)
- [Privacy Risk](#Privacy)
You can download the preceding list: [Download](/downloads/zia/documentation-knowledgebase/policies/url-filtering/about-url-categories/ZIA-URLCategories-02-12-2025.csv)
The URL category provides the following benefits and enables you to:
- Accurately categorize websites based on their content.
- Control access to websites more effectively.
- Properly use URL classification which complements our existing policies (Data Loss Prevention (DLP), Sandbox, Filetype, and SSL Policies).
- Create custom URL categories that provide greater flexibility while creating URL Filtering rules.
You cannot add new classes, nor can you edit or delete the predefined classes. Each class has super categories. You cannot add or delete super categories, but you can move them from one class to another for easier management. For example, your organization is in the entertainment field and your users often visit entertainment sites. You can move the Entertainment/Recreation super category to the Business Use class. You can also add additional custom categories to the super category by clicking the **Add** icon that appears next to the super category in **Administration** > **URL Categories**.
For the predefined categories, you can add URLs or IP addresses, keywords, and IP ranges for websites you want to be included in that category. You can also enter subdomains (for example, `mail.google.com`). This can be done by clicking the **Edit** icon that appears next to it in the list of URL categories found in **Administration** > **URL Categories**. If you manually add a URL or subdomain to an existing super category, category, or custom category, you can also specify whether you want it to retain its original parent category. For example, if you manually add `www.google.com` to a User-Defined category, you can specify whether you want google.com also to retain its original Web Search category. You cannot delete any category that is actively used in a URL Filtering rule. To delete a category, deselect it in the [URL Filtering](/zia/about-url-filtering) rule.
You can look up a URL or IP address's categorization by using [Site Review](https://sitereview.zscaler.com/) or by [looking up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal). Since a single IP address is capable of running multiple hosts or applications, Zscaler does not typically place IP addresses into the predefined URL categories. However, if a SaaS or cloud provider dedicates an IP address or IP range to an application, the Zscaler service categorizes it. For example, 13.107.6.152/31 is used for Office 365 and is categorized as Professional Services and Office 365.
You can also use [Web Insights](/zia/about-insights) and its [filters](/zia/web-insights-logs-filters) to learn more about how URL categories are being used in your network.
[]Custom Categories
In addition to the predefined categories, you can create [custom categories](/zia/adding-custom-url-categories). Custom categories can be based on URLs or IP addresses, keywords, and IP ranges. With URLs or IP addresses, you can block specific websites. With IP ranges, you can block a specific range of IP addresses for websites. With keywords, you can block websites based on any words that may appear in a URL. For example, imagine you want to block all websites with the term "gambling" in the URL. If you create a category with the custom keyword "gambling" and use it in a policy set to **Block**, websites such as www.gambling.com and www.gambling101.com are blocked. As custom keywords are applicable to the entire URI, if you went to www.google.com and searched for "gambling" the search results would also be blocked since the word gambling appears in the URI (https://www.google.com/search?q=**gambling**&oq=**gambling**&aqs=chrome..69i57j0l4.2767j0j8&sourceid=chrome&ie=UTF-8). You can also add custom URLs and keywords to a predefined URL category.
You can add up to 25K custom URLs or IP addresses (across all policies that use custom URLs or IP addresses), and up to 64 custom categories. You can add up to 256 keywords per category, and up to 2,048 across all categories. You can add up to 2,048 custom IP ranges (across all policies that use custom IP ranges). To learn more, see [Ranges & Limitations](/zia/ranges-limitations).
You can also control who creates and manages custom URL categories. You might want to do this if, for example, you have dedicated personnel managing your custom URL categories, or if you would like to enable administrators in specific departments or locations to manage their own categories. These categories can only be managed by super admins, admins with the **Custom URL Management role**, or admins with the** Custom URL Management** and** Override Existing URLs** role. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
When enforcing URL Filtering policy rules containing a wildcard, a Zscaler Internet Access (ZIA) Public Service Edge always looks for a specific match first. For example, you have Custom Category 1 containing the wildcard entries .example.com and .example.com/abc/, and Custom Category 2 containing abc.example.com and example.com/abc/def. Also, your URL Filtering policy rule states, "For Location X, block everything in Custom Category 1". In this example, if a user tries to access abc.example.com or example.com/abc/def from Location X, they won't be blocked because those exact domain names are in Custom Category 2, which is not blocked.
Changing Categorization
If you think that a website has been incorrectly categorized, there are three ways to request its re-categorization.
- Submit a change request Support ticket.
- Use Site Review to look up a URL, then select the **Modify Categories** option. This service is available for all users going through the Zscaler service. To learn more, see [Using Site Review to Lookup URLs](/zia/using-site-review-lookup-urls).
- Submit a review of a URL from the [End User Notification](/zia/about-acceptable-use-policy-and-end-user-notifications).
[]
| Super Category: Entertainment/Recreation |
| ---------------------------------------- |
| Categories and Definitions | Examples |
| **Entertainment**: Sites that provide information on or promote mass entertainment media such as theater, amusement parks, music, comics, fan clubs, and so on. | www.mangahere.co,www.anime-planet.com |
| **Music and Audio Streaming**: Sites that promote music for entertainment purposes related to bands, orchestras, festivals, and so on. It also includes audio streaming websites. | www.itunes.com,www.spotify.com |
| **Other Entertainment/Recreation**: Other sites related to entertainment/recreation that are not included in the defined categories. | rockcreekrvpark.com,destinywateradventures.com |
| **Radio Stations**: Sites that offer streaming or downloadable radio programming. | radioducinema.com,statsradio.com |
| **Video Streaming**: Sites that are related to streaming video. | netflix.com,hotstar.com |
| **Television/Movies**: Sites related to television programming or movies. | imdb.com,movies.com |
| Super Category: News and Media |
| ------------------------------ |
| Categories and Definitions | Examples |
| **News and Media**:** **Sites that report information or commentary on current events or contemporary issues, including newspapers, newswire services, news magazines, and radio news stations. | www.cnn.com,www.asiaone.com |
| Super Category: User-Defined |
| ---------------------------- |
| Categories and Definitions |
| You can populate this category with sub-categories or URLs that you manually create. |
[]
| Super Category: Business and Economy |
| ------------------------------------ |
| Categories and Definitions | Examples |
| **Classifieds**: Sites that display advertisements for sale or purchase of goods and services. It also includes sites like the marriage bureau, etc. | www.craigslist.com,www.gumtree.com |
| **Corporate Marketing**: Sites that offer corporate and product information but do not sell products. | www.adobe.com,www.apple.com |
| **Finance**: Sites that provide information related to financial investment and firms that offer financial services. It doesn't include websites that are related to insurance. | www.hsbc.com,www.citibank.com |
| **Insurance**: Sites that allow users to compare and buy insurance policies and resources explaining specific types of insurance (e.g., life insurance, health insurance). This category includes company websites that provide self-service options for managing policies. | www.tataaig.com,www.unitedhealthgroup.com |
| **Online Trading and Brokerage**: Sites that provide trading of securities and management of investment assets. This category includes sites that offer financial investment strategies, quotes, and news. | ameritrade.com,etrade.com |
| **Other Business and Economy**: Other sites related to business and economy that are not classified in any of the defined categories. | etrind.com.br,dfsafrica.org |
| **Professional Services**: Sites that provide information about or are related to the sale and delivery of technical and professional services. | www.work.co,www.issworld.com |
| Super Category: Education |
| ------------------------- |
| Categories and Definitions | Examples |
| **Continuing Education/Colleges**: Sites related to institutions and colleges offering formal courses of advanced studies for adults. | www.duke.edu,www.ox.ac.uk |
| **History**: Sites that offer a systematic recording of past events or analysis and commentary on causes and effects, motives, or connections relating to events. | www.hyperhistory.com,www.besthistorysites.net |
| **K-12**: Sites related to the education of children. | www.k12.com,www.ilacademy.net |
| **Other Education**: Other sites related to education that is not included in the defined categories. | students-tut.ru,formasup-npc.org |
| **Reference Sites**: Sites that offer scholars and academics source documents and research assistance. | www.wikipedia.org,www.dictionary.com |
| **Science/Tech**: Sites related to science and technology. | www.scitechdaily.com,www.livescience.com |
| Super Category: Information Technology |
| -------------------------------------- |
| Categories and Definitions | Examples |
| **Advertising**: Sites that provide service links, banners, or ads for websites. | www.buysellads.com,www.fusionads.net |
| **Generative AI and ML Applications**: Sites that provide tools, services, or information related to generative AI (i.e., a subfield of artificial intelligence that can generate new text, images, videos, or audio.). | openai.com,bard.google.com |
| **CDN**: Sites that use content delivery networks to optimize the delivery of localized content to end users. | cdn.espn.com,bighost.be |
| **Developer Tools**: Sites that provide tools used by developers for coding, debugging, testing and managing software projects. This category includes websites and online platforms related to software development, programming, and IT infrastructure. | rubyonrails.org,github.com |
| **DNS Over HTTPS Services**: Sites that provide DNS resolution over an encrypted and secure connection with the DNS over HTTPS service. This category includes DNS server URLs that support DNS resolution using the HTTPS protocol. | dns.google/dns-query,cloudflare-dns.com/dns-query |
| **File Converters**: Sites and services that allow users to convert files from one format to another. | www.freepdfconvert.com,www.freeconvert.com |
| **FileHost**: Sites that offer hosting, backup, and sharing of files on the internet. It also includes sites that allow you to upload files for online processing, such as file conversion. | www.dropbox.com,www.pdftoimage.com |
| **General AI and ML Applications**: Sites that offer non-generative AI and ML applications and services. This category includes websites for AI research labs, AI-powered solution providers, AI/ML app demonstrations and tutorials, and that enable automation with AI and ML. | aimagazine.com,www.aitrends.com |
| **Image Host**: Sites that provide video or image hosting, linking, or sharing. | www.flickr.com,www.imgur.com |
| **Operating System and Software Updates**: Sites and links that are used for downloading operating systems such as Windows, iOS, etc. and software updates. | swcdn.apple.com,windowsupdate.microsoft.com |
| **Other Information Technology**: Other sites related to information technology that are not included in the defined categories. | kwonnam.pe.kr,bellsouthemailsettings.com |
| **Portals**: Sites that offer multiple web-based services to assist a user's experience on the internet. | qq.com,naver.com |
| **Safe Search Engine**: Sites that provide internet search services geared specifically for families and children and prevent the discovery of objectionable material. | www.safesearchkids.com,fragfinn.de |
| **Shareware Download**: Sites that are related to or offer downloading of a large number of legal third party software. | www.download.cnet.com,www.filehippo.com |
| **Translators**: Sites that offer translation services for web pages, URLs, or other text strings. | translate.google.com,www.freetranslation.com |
| **Web Host**: Sites that offer web hosting services, as well as domain names and web space, to host end-user web pages. | www.siteground.com,www.myown.eu |
| **Web Search**: Sites that offer search services for the internet, indices, and directories. | www.google.com,www.yahoo.com |
| Super Category: Internet Communication |
| -------------------------------------- |
| Categories and Definitions | Examples |
| **Blogs**: Sites related to online journals, diaries, or newsletters that express personal thoughts and opinions about social or political issues. | www.tumblr.com,www.wordpress.org |
| **Discussion Forums**: Sites related to Usenet, Usenet news, forums, newsgroups, or online bulletin board systems. | www.cellar.org,www.wsc-forum.de |
| **Internet Services**: Sites that offer online utility applications or services that assist in internet communication. | www.singnet.com.sg,www.imagin.com |
| **Online Chat**: Sites that offer access to, software for, or participation in any internet chat forum. Chat is defined as any online conversation taking place in real-time. | finnchat.com,msngr.com |
| **Other Internet Communication**: Other sites related to internet communications that are not included in the defined categories. | softyupdates.com,ipixo.com |
| **Peer-to-Peer Site**: Sites that provide client software to enable peer-to-peer file sharing and transfers. | www.bittorrent.com, www.limewire.com |
| **Remote Access Tools**: Sites that provide information or software to enable authorized access to a desktop computer or private network from a remote location. | www.teamviewer.com,www.logmein.com |
| **Webmail**: Sites that provide email accounts, free or otherwise. | www.mail.google.com,www.hotmail.com |
| **Web Conferencing**: Sites that assist in conducting video conferencing or provide software to enable virtual meetings. | www.webex.com,www.zoom.us |
| **Zscaler Proxy IPs**: This category includes IP addresses owned by Zscaler's data centers and services such as IP addresses of the Public Service Edge on a cloud and global VIP service. |  |
| Super Category: Job/Employment Search |
| ------------------------------------- |
| Categories and Definitions | Examples |
| **Job/Employment Search**: Sites that provide employment services, assistance in finding employment, or tools for locating employers. | www.monster.com,www.indeed.com |
| Super Category: Microsoft Office 365 (Applicable only for SSL Inspection Policy) |
| -------------------------------------------------------------------------------- |
| Categories and Definitions | Examples |
| **MS O365 Allow**: Sites that are required but are not as sensitive to network performance and latency as those in the Optimize category.Microsoft recommends bypassing these sites from SSL inspection and authentication. | smtp.office365.com |
| **MS O365 Default**: Sites that do not require any optimization and can be treated as regular Internet traffic. | ssw.live.com,storage.live.com |
| **MS O365 Optimize**: Sites that are required for connectivity to every Office 365 service. These sites are very sensitive to network performance, latency, and availability.Ensure to bypass these sites from SSL inspection and authentication. | outlook.office.com,outlook.office365.com |
[]
| Super Category: Government and Politics |
| --------------------------------------- |
| Categories and Definitions | Examples |
| **Government**: Sites related to governments and their agencies or militaries. | www.usa.gov,www.gov.sg |
| **Military**: Sites related to military or armed forces, excluding those that discuss or sell weapons. | www.af.mil,www.army.mil |
| **Other Government and Politics**: Other sites related to government and politics that are not included in the defined categories. | wec24.org,covid-sb.org |
| **Politics**: Sites related to, or sponsored by, organizations that seek to influence viewpoints, change or reform public policy, public opinion, or government practices. | www.nrsc.org,www.pap.org.sg |
[](/zia/configuring-advanced-url-policy-settings)
| Super Category: Miscellaneous |
| ----------------------------- |
| Categories and Definitions |
| **Miscellaneous or Unknown**: Sites that have not yet been classified by Zscaler. |
| **Newly Registered and Observed Domains**: Sites whose domains were created in the last 30 days and are currently not categorized by Zscaler. This category also includes domains that we encounter for the first time. Domains under this category are considered suspicious until they are categorized or better understood by Zscaler.This category is a subset of the Miscellaneous category. To determine if a Miscellaneous or Unknown URL belongs in the Newly Registered and Observed Domain (NROD) category, when a URL is found in the Miscellaneous or Unknown category, it is checked against Zscaler's NROD database. If there’s a match, the URL is categorized as a Newly Registered and Observed Domain. To enable the use of this category, select **Enable Suspicious New Domains Lookup** in your Advanced URL Policy Settings.This category can only be used in URL Filtering rules. |
| **Non Categorizable**: Sites that Zscaler has not been able to categorize. Some of the reasons a site may appear here are that the site is a login page without any other details, it no longer exists, it is parked or available for sale, or it is unresolvable on the internet. |
| **Other Miscellaneous**: Other sites that are not included in the defined categories. |
| Super Category: Travel |
| ---------------------- |
| Categories and Definitions | Examples |
| **Travel**: Sites related to travel planning, information, or activities, including reservation services, destination listings, and special event promotion. | www.contiki.com,www.singaporeair.com |
| Super Category: Vehicles |
| ------------------------ |
| Categories and Definitions | Examples |
| **Vehicles**: Sites that provide information about or promote vehicles, or offer for purchase vehicle parts or maintenance. | www.toyota.com,www.volkswagen.com |
[]
| Super Category: Adult Material |
| ------------------------------ |
| Categories and Definitions | Examples |
| **Adult Sex Education**: Sites related to sex education and targeted at adult readers. | www.plannedparenthood.com,www.itsyoursexlife.com |
| **Adult Themes**: Sites related to adult content not covered by more specific categories, for example, penile enlargement, erectile dysfunction, adult entertainment, and so on. | www.yourtango.com/sex,www.singlebrides.com |
| **Body Art**: Sites that provide information about artistic sexual expression or information about or images of body piercing, tattoos, and any form of body art. | kicktattoo.com,tattoogrid.net |
| **K-12 Sex Education**: Sites associated with sex education for children, including sites that offer information about sex, human reproduction, or any other sexually oriented material used to educate. | www.teensource.org,www.sexetc.org |
| **Lingerie/Bikini**: Sites that display or are dedicated to lingerie or swimsuits that could be considered inappropriate for teenagers and younger children. | www.wacoal.com,www.agentprovocateur.com |
| **Nudity**: Sites that provide either artistic or non-artistic nude images in any medium (sculpture, photographs, paintings, and so on). | nakedsipandpaint.com,prostitutkimoskvyxxx.com |
| **Other Adult Material**: Other sites related to adult material that are not in the defined categories. | teamcrazy.za.net,smilemakerscollection.com |
| **Pornography**: Sites related to soft- and hard-core pornography, regardless of medium (written, images, movies, and so on). | www.playboy.com,www.sex.com |
| **Social Networking Adult**: Sites that provide social networking for adults, such as dating sites. | www.okcupid.com,www.ashleymadison.com |
| Super Category: Drugs |
| --------------------- |
| Categories and Definitions | Examples |
| **Other Drugs**: Sites associated with the use or advocacy of illegal drugs or the illegal use of prescribed drugs, except those sites related to Marijuana. | livwell.com,buyecstasy.com |
| **Marijuana**: Sites that promote or discuss the cultivation, manufacture, distribution or sale of marijuana for recreational or medicinal purposes. It includes web pages on legalizing marijuana, using marijuana for medicinal purposes, marijuana facts and info pages, and sites that mention hemp, cannabis, blunts, panama red, etc. | www.leafly.com,thcbiomed.com |
| Super Category: Gambling |
| ------------------------ |
| Categories and Definitions | Examples |
| **Gambling**: Sites that provide online gambling or are related to gambling assistance, training information, or advocacy. | www.casino.com,www.singaporepools.com.sg |
| Super Category: Illegal or Questionable |
| --------------------------------------- |
| Categories and Definitions | Examples |
| **Anonymizer**: Sites that allow users to surf the internet or send email anonymously by providing proxy bypass functionality or information or instructions on how to do so. | www.anonymizer.com,www.your-freedom.net |
| **Computer Hacking**: Sites related to the promotion of illegal tools and mechanisms to crack passwords, generate and distribute malicious software, or gain unauthorized access to computer systems. | www.cellphonehacks.com,www.hayy.net |
| **Copyright Infringement**: Sites related to bootlegged or otherwise illegally available copyrighted material, such as program, DVD movies, and CD or MP3 music. | sci-hub.tw,bingemachine.com |
| **Mature Humor**: Sites that contain humor and mature themes unsuitable for teenagers and children, but no pornography or strong profanity. | thejokeyard.com,badmovies.org |
| **Other Illegal or Questionable**: Other sites related to illegal or questionable activities that are not classified in the defined categories. | salesreceiptstore.com,katcr.co |
| **Profanity**: Sites that contain generally acknowledged profanity but do not fall under a more specific category such as "Pornography." | www.yourfuckingpollingplace.com |
| **Questionable**: Sites that are generally related to illegal activities but do not fall under a more specific category. | www.joyofsatan.org,www.satanicchurch.com |
| Super Category: Militancy/Hate Extremism |
| ---------------------------------------- |
| Categories and Definitions | Examples |
| **Militancy/Hate and Extremism**: Sites that promote divisive rhetoric or action, describe certain populations as dangerous, evil, or promote intolerance of individuals or groups. | www.newnation.org,www.klanparenthood.com |
| Super Category: Tasteless |
| ------------------------- |
| Categories and Definitions | Examples |
| **Tasteless**: Sites related to torture, human and animal degradation, and other behavior generally considered too inappropriate for a public audience such as actively aggressive, attacking content, and so on. | www.morticom.com, www.gore2gasm.com |
| Super Category: Violence |
| ------------------------ |
| Categories and Definitions | Examples |
| **Violence**: Sites that depict, promote, or feature violence. | stranakrovi.com,serienkillers.de |
| Super Category: Weapons/Bombs |
| ----------------------------- |
| Categories and Definitions | Examples |
| **Weapons/Bombs**: Sites that promote the use, making, or distribution of weapons. | dsparmory.co,nragungiveaway.org |
[]
| Super Category: Games |
| --------------------- |
| Categories and Definitions | Examples |
| **Online and Other Games**: Sites related to online games and other websites related to games that are not included in the defined categories. | www.worldofwarcraft.com,agame.com |
| **Social Networking Games**: Sites that reside on social networking sites and contain material that merits categorization into the Games super category. | www.facebook.com/games |
| Super Category: Health |
| ---------------------- |
| Categories and Definitions | Examples |
| **Health**: Sites related to an individual’s physical and mental well-being. | multiformelegym.com,ochsstaywell.com |
| Super Category: Religion |
| ------------------------ |
| Categories and Definitions | Examples |
| **Alt/New Age**: Sites related to non-traditional or nonreligious spiritual belief systems, or related to the practice or advocacy of affecting events through supernatural means. | thetarotguide.com,mirsularii.com |
| **Cult**: Sites related to groups or movements whose membership is marked by zeal, passion, and obedience to a degree generally considered excessive by the mainstream. | theflatearthsociety.org,medaglia-miracolosa.it |
| **Other Religion**: Other sites related to religion that is not classified in the defined categories. | stmarkstn.org,qcforjesus.com |
| **Traditional Religion**: Sites related to traditionally organized religious activities, participation, and belief. | www.chc.org.sg,www.buddhanet.net |
| Super Category: Shopping and Auctions |
| ------------------------------------- |
| Categories and Definitions | Examples |
| **Online Auctions**: Sites that offer participation in online auctions or support the offer and purchase of goods between individuals. | www.quibids.com,www.onlineauction.com |
| **Online Shopping**: Sites that provide, or advertise ways to purchase products or services over the internet or by telephone. | www.overstock.com,www.amazon.com |
| **Other Shopping and Auctions**: Other sites related to shopping and auctions that are not included in the defined categories. | thecholmeleyarms.co.uk,shoppiego.com |
| **Real Estate**: Sites that offer information or services related to buying, selling, renting, or financing a property. | www.redas.com,www.propnex.com |
| Super Category: Social and Family Issues |
| ---------------------------------------- |
| Categories and Definitions | Examples |
| **Family Issues**: Sites related to issues specific to the family such as divorce, adoption, infertility, domestic violence, and so on. | maritallaws.com,resetting-the-family.com |
| **Other Social and Family Issues**: Other sites related to social and family issues that are not classified in the defined categories. | hopecle.org,familiesforfamilies.net |
| **Social Issues**: Sites related to issues generally considered to engender controversies, such as abortion, euthanasia, legalization of drugs, and so on. | kandoo.me,robindiangelo.com |
| Super Category: Society and Lifestyle |
| ------------------------------------- |
| Categories and Definitions | Examples |
| **Alcohol/Tobacco**: Sites related to the use of alcohol and tobacco products, excluding those that inform on the hazards of alcohol and tobacco. | www.martell.com,melbournehookah.com.au |
| **Lifestyle**: Sites related to lifestyle activities such as parties and so on for all orientations. | www.lambda.org,www.clubmask.com |
| **Art/Culture**: Sites related to the mores, activities, organizations, and collective behavior of peoples that define various cultures around the world. | www.artandculture.com,www.metmuseum.org |
| **Dining/Restaurant**: Sites that list, discuss, review, advertise, or promote dining and restaurants. | www.mcdonalds.com,www.hungrygowhere.com |
| **Hobbies/Leisure**: Sites related to hobbies and leisure, or pursuits or interests engaged in for pleasure and relaxation. | jenniemasterson.com,takemefishing.org |
| **Other Society and Lifestyle**: Other sites related to society and lifestyle that are not classified in the defined categories. | carolineandmichael2020.com,ashlandandblake.com |
| **Social Networking**: Sites that enable the creation of online communities or the facilitation of personal introductions, dating, and networking. | www.facebook.com,www.linkedin.com |
| Super Category: Special Interests/Social Organizations |
| ------------------------------------------------------ |
| Categories and Definitions | Examples |
| **Special Interests/Social Organizations**: Sites related to charitable organizations, community or environmental interest groups, or social advocacy. | www.greenpeace.org,www.audi-denkwerkstatt.de |
| Super Category: Sports |
| ---------------------- |
| Categories and Definitions | Examples |
| **Sports**: Sites related to sports or recreation. | espn.go.com,www.nba.com |
[]
[](/zia/configuring-advanced-url-policy-settings)
| Super Category: Security |
| ------------------------ |
| Categories and Definitions | Examples |
| **Custom Encrypted Content**: Sites that use custom encryption for protecting users’ data. Zscaler can inspect the HTTP headers of such sites but not the body content. | mask.icloud.com,app.stupendo.co |
| **Dynamic DNS Host**: Sites that dynamically update the IP address of the hostname and provide DNS resolution. This category includes DNS server URLs that support Dynamic DNS resolution. | dyndns.com,no-ip.com |
| **Newly Revived Domains**: Sites that were reactivated after a brief period of inactivity for about 10 days. Some of these websites were originally active with a legitimate reputation.To enable the use of this category, select **Enable Suspicious New Domains Lookup** in your Advanced URL Policy Settings. |  |
| **Other Security**: Other sites related to security that are not included in the defined categories. | trustwave.ctscloud.com,microsoftinternetsafety.net |
| **Spyware/Adware**: Sites that are known to distribute or contain code that displays unwanted advertisements or that gathers user information without the user’s knowledge. | www.spywareremove.com,www.virusspy.com |
About the URL Categories Page
On the URL Categories page (Administration > URL Categories), you can do the following:
- See the maximum limit of custom URLs or TLDs that are allowed and the number of custom URLs or TLDs used in your policies. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations).
- See the number of **Predefined** and **Custom** URL categories that are available.
The count of the **Predefined** and **Custom** URL categories dynamically changes based on the number of URL categories that match the search term.
- [Configure a Custom URL category](/zia/adding-custom-url-categories).
- Expand or collapse all** **URL categories.
- Filter the URL categories based on the following filters:
- **URL**: Select this filter to view the list of URL categories that contain the matching term in the **No. of Custom URLs** or **No. of URLs Retaining Parent Category** field.
- **Keyword**: Select this filter to view the list of URL categories that contain the matching term in the **No. of Custom Keywords** or **No. of Keywords Retaining Parent Category** field.
- **URL Category Name**: Select this filter to view the list of URL categories that contain the matching term in the **Name** field.
- **All**: Select this filter to view the list of URL categories that contain the matching term in any of the fields.
- **IP Ranges**: Select this filter to view the list of URL categories that contain the matching term in the **No. of Custom IP Ranges** or **No. of IP Ranges Retaining Parent Category** field.
- Search for a term.
The search term must contain at least 3 characters.
- View a list of all configured URL categories. For each URL category, you can view the following information:
- **Name**: The name of the URL category listed under the respective super category.
- **No. of Custom URLs**: The number of custom URLs or IP addresses in the category.
- **No. of URLs Retaining Parent Category**: The number of URLs or IP addresses that retain their parent category.
The Custom URLs and URLs Retaining Parent Category fields support IPv6 addresses.
- **No. of Custom Keywords**: The number of custom keywords in the category.
- **No. of Keywords Retaining Parent Category**: The number of keywords that retain their parent category.
- **No. of Custom IP Ranges**: The number of custom IP ranges in the category.
- **No. of IP Ranges Retaining Parent Category**: The number of IP ranges that retain their parent category.
The number under each column displays up to 20 values when you click it. You can view the complete list of values in the edit mode of the URL category page.
- Add a URL category under the super category.
- Edit a predefined URL category.
![The ZIA URL Categories page](/downloads/zia/policies/url-filtering/about-url-categories/About-URL-Categories_v2.png)