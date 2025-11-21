# Alternative Options to Caching Web Traffic
Source: https://help.zscaler.com/unified/alternative-options-caching-web-traffic
PDF: https://help.zscaler.com/pdf/com/en/1495296.pdf

Proxies have been employing caching techniques to minimize bandwidth usage and improve latency on web browsing traffic in companies for over a decade. In the Web 1.0 days, caching was a useful technique because most web pages were relatively static. Today’s websites have evolved to provide much more dynamic content, session-based connections, streaming media, and the utilization of HTTPS to encrypt a large segment of traffic. In addition, there are now alternative techniques you can use to realize some of the same goals as caching, but in a more effective manner.
To learn more about some of the changing trends that affect web proxy, see:
- [Dynamic Content](#Dynamic)
- [HTTPS](#HTTPS)
- [Browser Caching](#Browser)
- [File Size Limits](#File)
- [Streaming Media](#Streaming)
Alternatives to Caching
The primary goal of caching is to reduce bandwidth usage and improve user experience. Below are some alternative solutions that will effectively reduce bandwidth usage, leaving more bandwidth for business applications and improving user experience. The number one category responsible for bandwidth usages is Streaming Media.
- Prioritize Traffic. Set a policy in place that will prioritize business related traffic over Streaming Media, Large File downloads, or other high bandwidth/less critical sites.
Having a product that can do traffic shaping can effectively limit any impact from high bandwidth sites/users.
- Enforce network quotas on Streaming Media sites per user. For example, each user gets 50 MB of Streaming Media per day. This allows the average user to access Streaming Media sites, while putting a cap on the high bandwidth usage users.
- Use the [URL Filtering policy](/unified/about-url-filtering) to block access to Streaming Media or specific popular non-business streaming media sites like YouTube or Vimeo.
- Direct to Net. By using local Internet connections and not backhauling traffic over a WAN, latency is considerably reduced and user experience is improved. This helps user experience from both a performance perspective and a localized content perspective.
[]Most web traffic today includes dynamic content. From news to searches and web applications, content is created on the fly and delivered to specific users. Caching provides no benefit for such content. The HTTP header, Cache-Control, was introduced to allow web developers to determine if and for how long a page should be cached. You will see many sites that use *Cache-Control: no cache* or *Cache-Control: no-store*, indicating that these resources should not be cached.
[]If you are not decrypting HTTPS connections, you are not caching content from HTTPS connections because proxies cannot cache encrypted data.
If you are decrypting HTTPS on your proxy, then it is possible in some products to cache that data. But from a security standpoint, this can open up a potential risk that you are now storing sensitive data on a multiuser machine (with virtually no control or visibility to who receives that potentially sensitive data).
[]All modern browsers provide caching at the client level, both in memory and to disk. A caching proxy server would only provide a secondary level of caching.
[]Due to limited memory and disk space, proxies are configured to only cache files up to a certain size. If the max file size is too small (for example 1 MB), the gains from caching will be minimal since most files will not be cached. If the max file size is too large, then the cache will be limited to the number of files it can cache, which will reduce the cache hits. Even with all the time and expertise at your disposal to tune the max file size, the optimal setting could change from day to day, or even hour to hour, based on browsing patterns.
[]With the prevalence of Streaming Media and Content Delivery Networks (CDNs), many sites store the same content at multiple URLs or hosts. This makes caching less effective because a single video can be cached multiple times, filling your cache and reducing cache hits. Additionally, changing resolution (which often happens dynamically) can trigger a video to be cached in multiple resolutions, which will also fill your cache and reduce cache hits.