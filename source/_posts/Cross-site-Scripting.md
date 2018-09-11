---
title: Cross-site Scripting
date: 2018-09-12 01:41:46
tags: XSS
categories: Injection
---

## Common occurrences of vulnerabilities
The data is included in dynamic content(web request requently) that enters a Web application and then is sent to a web user.

## Type
* Stored XSS Attacks
These are those where the injected script is permanently stored on the target servers, such as in a database, in a message, in a message forum, visitor log, comment field, etc.
* Reflected XSS Attacks
These are those where the injected script is reflected directly off the web server when the request is sent.
* DOM XSS Attacks
DOM Based XSS is a form of XSS where the entire tainted data flow from source to sink takes place in the browser, i.e., the source of the data is in the DOM, the sink is also in the DOM, and the data flow never leaves the browser. For example, the source could be the URL of the page(e.g., document.location.href or the value of an element of the HTML), and the sink is sensitive method call that causes the execution of the malicious data(e.g., document.write).
