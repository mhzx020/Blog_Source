---
title: Http Protocol
date: 2018-05-30 18:24:58
tags: Http Headers
categories: Web Foundation
---

### Common request header information
---
Accept:
> Display the resource types that the client can receive

Accept-Encoding:
> Display the compression algorithms that the client supported

<!--more-->
Accept-Language:
> Display the language type that the client wants receive

Cache-Control:
> Display the caching strategy used by the client(max-age=0 indicates that the client does not cache)

Connection:
> Display the type of connection the client wants to open(long or short connection, long connection requires heartbeat to maintain)

Cookie:
> A set of key-value pairs stored on the client to indicate the identity of the user

Host:
> Display the domain name or IP that the client wants to request

User-Agent:
> Discribes the detail of the client

Referer:
> Tell the server which page the request came from

if-modified-since:
> When the client’s cache has timed out, the request is sent. Then the server checks whether the resource has been modified since the last time it was sent to the client.If no changes have been the server returns 304, else it returns the modified resources.

if-none-match:
> Similar to if-modified-since, but it checks the ETag, its priority is higher than if-modified-since

Range:
> Indicates it only requests a part of resource

### Common response headers
---
Cache-Control:
> Display caching rules of server

Connection:
> Display the connection type that the server opens

Content-Encoding:
> Display the compression algorithm used by server

Content-Type:
> Display the resource types provided by the server

Date:
> Display the time sent by the sever

Transfer-Encoding:
> Display resource delivery method

Content-length:
> This field is required when the resource is not transmited in blocks

Cookie:
> A set of key-value pairs stored on the client to indicate the identity of the user

Location:
> When the return code is 302, this value is the URL to be redirected

### Common Response Codes
200 OK:
> Successful request

204 No Content:
> Indicates that the request has been successfully executed but no resources are returned

301 Moved Permanently:
> Indicates that the resource address has been changed forever with a new address returned in the Location field

302 Found:
> Indicates that the resource address has been changed temporarily with a new address returned in the Location field

304 Not Modified:
> Indicates that the requested resource has not changed and the cache can continue to be use

403 Forbidden:
> Indicates that the client does not have access to the resources

404 Not Found:
> Indicates that the resource does not exist

500 Internal ServerError:
> An error occurred on the server

### Cookies field
name:
> Name of the cookies

value:
> value of the cookies

Expires:
> Expiration time of the cookies

Path:
> The web path associated with the cookies

Domain:
> The domain name associated with the cookies

Secure:
> Specifies whether the cookie tranmission process uses a cryptographic protocol(usually https)