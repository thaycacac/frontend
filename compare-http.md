<table class="table" width="100%" cellspacing="0" cellpadding="0">
<tbody>
<tr class="trhead">
<td>Differentiator</td>
<td>HTTP/1.0</td>
<td>HTTP/1.1</td>
<td>HTTP/2</td>
</tr>
<tr>
<td>Year</td>
<td>1991</td>
<td>1997</td>
<td>2015</td>
</tr>
<tr>
<td>Key Features</td>
<td>For every TCP connection there is only one request and one response.<br>
<img alt="HTTP1 Protocol" width="265" height="300" data-srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1.png 373w" data-src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png" data-sizes="(max-width: 265px) 100vw, 265px" class="alignright size-medium wp-image-416 lazyloaded" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png" sizes="(max-width: 265px) 100vw, 265px" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1.png 373w"><noscript><img class="alignright size-medium wp-image-416" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png" alt="HTTP1 Protocol" width="265" height="300" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http1.png 373w" sizes="(max-width: 265px) 100vw, 265px" /></noscript></td>
<td>It supports connection reuse i.e. for every TCP connection there could be multiple requests and responses, and pipelining where the client can request several resources from the server at once. However, pipelining was hard to implement due to issues such as head-of-line blocking and was not a feasible solution.<br>
<img alt="HTTP2 Protocol" width="265" height="300" data-srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2.png 376w" data-src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png" data-sizes="(max-width: 265px) 100vw, 265px" class="alignright size-medium wp-image-417 lazyloaded" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png" sizes="(max-width: 265px) 100vw, 265px" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2.png 376w"><noscript><img class="alignright size-medium wp-image-417" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png" alt="HTTP2 Protocol" width="265" height="300" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2-265x300.png 265w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http2.png 376w" sizes="(max-width: 265px) 100vw, 265px" /></noscript></td>
<td>Uses multiplexing, where over a single TCP connection resources to be delivered are interleaved and arrive at the client almost at the same time. It is done using streams which can be prioritized, can have dependencies and individual flow control. It also provides a feature called server push that allows the server to send data that the client will need but has not yet requested.<br>
<img alt="HTTP3 Protocol" width="283" height="300" data-srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png 283w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3.png 351w" data-src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png" data-sizes="(max-width: 283px) 100vw, 283px" class="alignright size-medium wp-image-418 lazyloaded" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png" sizes="(max-width: 283px) 100vw, 283px" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png 283w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3.png 351w"><noscript><img class="alignright size-medium wp-image-418" src="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png" alt="HTTP3 Protocol" width="283" height="300" srcset="https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3-283x300.png 283w, https://cheapsslsecurity.com/p/wp-content/uploads/2019/07/http3.png 351w" sizes="(max-width: 283px) 100vw, 283px" /></noscript></td>
</tr>
<tr>
<td>Status Code</td>
<td>Can define 16 status codes; the error prompt is not specific enough.</td>
<td>Introduces a warning header field to carry additional information about the status of a message. Can define 24 status codes, error reporting is quicker and more efficient.</td>
<td>Underlying semantics of HTTP such as headers, status codes remains the same.</td>
</tr>
<tr>
<td>Authentication Mechanism</td>
<td>Uses basic authentication scheme which is unsafe since username and passwords are transmitted in clear text or base64 encoded.</td>
<td>It is relatively secure since it uses digest authentication, NTLM authentication.</td>
<td>Security concerns from previous versions will continue to be seen in HTTP/2. However, it is better equipped to deal with them due to new TLS features like connection error of type Inadequate_Security.</td>
</tr>
<tr>
<td>Caching</td>
<td>Provides support for caching via the If-Modified-Since header.</td>
<td>Expands on the caching support by using additional headers like cache-control, conditional headers like If-Match and by using entity tags.</td>
<td>HTTP/2 does not change much in terms of caching. With the server push feature if the client finds the resources are already present in the cache, it can cancel the pushed stream.</td>
</tr>
<tr>
<td>Web Traffic</td>
<td colspan="2">HTTP/1.1 provides faster delivery of web pages and reduces web traffic as compared to HTTP/1.0. However, TCP starts slowly and with domain sharding (resources can be downloaded simultaneously by using multiple domains), connection reuse and pipelining, there is an increased risk of network congestion.</td>
<td>HTTP/2 utilizes multiplexing and server push to effectively reduce the page load time by a greater margin along with being less sensitive to network delays.</td>
</tr>
</tbody>
</table>
