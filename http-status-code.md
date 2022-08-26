# HTTP Status Codes Explained

In a Client-Server architecture, you (the Client end) receives various types of responses and to identify each of them, these HTTP Status Codes are divided into various categories. Each status code is a 3 digit number of which, the first digit determines the category and the rest two digits really gives the meaning to these HTTP Status Codes.

* [1XX - Informational](#1xx---informational)
* [2XX - Success](#2xx---success)
* [3XX - Redirection](#3xx---redirection)
* [4XX - Client Error](#4xx---client-error)
* [5XX - Server Error](#5xx---server-error)

## 1xx - Informational

| http Status Code        | description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| 100 Continue            | It means that the client should continue with its request and is used to give an interim response to the client that the request has been received and has not been rejected by the server. |
| 101 Switching Protocols | When the client requests for a change in the application protocol being used on this connection, the server responds with this status code if Server is willing to change the protocol as per request. |

## 2xx - Success

| HTTP Status Code                  | Description                                                  |
| --------------------------------- | ------------------------------------------------------------ |
| 200 OK                            | It means that the request from the client is OK.             |
| 201 Created                       | It means that the request is complete, and a new resource is created, where the newly created resource can be referenced through the URL(s). |
| 202 Accepted                      | It means that the request from clients accepted for processing, but the processing is not yet complete. |
| 203 Non-authoritative Information | It means that the returned set of meta information in the entity-header is not the same as the set as available from the origin server, but is obtained from a local or a third-party copy. The set presented MAY be a subset or superset of the original version. |
| 204 No Content                    | It means that the server returns a status code and a header is given in the response, but there is no entity-body in the response whatsoever. |
| 205 Reset Content                 | It means that the server successfully processed the request, but is not returning any content. This response requires that the client reset the document view. |
| 206 Partial Content               | It means that the server is returning partial data of the size requested by the client. |

## 3xx - Redirection

| HTTP Status Code      | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| 300 Multiple Choices  | It means that the server responds with a link list. The client can then select a link and go to that location. Maximum five such addresses are allowed. |
| 301 Moved Permanently | It means that the URL requested by the client has now been moved to a new URL. |
| 302 Found             | It means that the URL requested by the client has been TEMPORARILY moved to a new URL. |
| 303 See Other         | It means that the response to the request can be found under a different URI and should be retrieved using a GET method. The new URI is not a substitute reference for the originally requested resource. |
| 304 Not Modified      | It means that this is the HTTP Status code to an "If-Modified-Since" or "If-None-Match header", where the URL has not been modified since the specified date in the request from the client. |
| 305 Use Proxy         | It means that the requested URL must be accessed through the proxy as being mentioned in the Location header. |

## 4xx - Client error

| HTTP Status Code                    | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| 400 Bad Request                     | It means that the Server did not understand the request from Client. |
| 401 Unauthorized                    | It means that the requested resource is username/password protected. |
| 402 Payment Required                | *This code is reserved for future use.*                      |
| 403 Forbidden                       | It means that accessing the requested page is forbidden.     |
| 404 Not Found                       | It means that the Server is unable to find the requested page. |
| 405 Method Not Allowed              | It means that the method sepcified in the request (Get or Post) is not at all allowed. |
| 406 Not Acceptable                  | It means that the server can only generate a response entities that is not accepted by the client as client always specifies them under accept headers. |
| 407 Proxy Authentication Required   | It means that the client must authenticate via a proxy server well before this request can be served by server. |
| 408 Request Timeout                 | It means that the request from Client took time greater than the Server was configured to wait. |
| 409 Conflict                        | It means that the server can not complete the request because of a conflict. |
| 410 Gone                            | It means that the requested resource by the client is no longer available at the server and no forwarding address is known to the server. |
| 411 Length Required                 | It means that the client has not defined the "Content-Length". |
| 412 Precondition Failed             | It means that the precondition as specified by the client has been evaluated as false by the server. |
| 413 Request Entity Too Large        | It means that the request entity is too large and hence the server will not accept the request. |
| 414 Request-url Too Long            | It means that the URL is too long that the Server can not accept the request. It arises majorly when the client tries to convert a POST request to a GET request. |
| 415 Unsupported Media Type          | It means that the media type is not supported and hence the server will not process the request. |
| 416 Requested Range Not Satisfiable | It means that the requested byte range is out of bounds now. |
| 417 Expectation Failed              | It means that the contents of Expect request-header can not be met by the server. |

## 5xx - Server error

| HTTP Status Code               | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| 500 Internal Server Error      | It means that the request can not be served as the server met with an Exception. |
| 501 Not Implemented            | It means that the request can not be served as the server itself does not support the functionality requested by the client. |
| 502 Bad Gateway                | It means that request can not be served as the server has received an invalid response from upstream server itself. |
| 503 Service Unavailable        | It means that the request can not be served as the server is down or may be temporarily overloaded. |
| 504 Gateway Timeout            | It means that request can not be served as the gateway has timed out. |
| 505 HTTP Version Not Supported | It means that the request can not be served as the server does not support the requested version of "http protocol" |
