---
title: Master Urlscan.io Dorking for Bug Bounty Hunting
Type: Video
published: 2026-07-23
Source: https://www.youtube.com/watch?v=I-J5Ht9goyc
Creator: "[[𝙇𝙤𝙨𝙩𝙨𝙚𝙘]]"
date: 2026-07-26
tags:
  - Clippings
  - Video
  - Recon/Dorks
Finished: false
Cover: https://i.ytimg.com/vi/I-J5Ht9goyc/maxresdefault.jpg
Site: YouTube
---
## Highlights
```
page.ip:* AND date:>now-7d
page.ip:49.12.22.106 AND date:[2018 TO 2026]
page.ip:(148.251.0.0\/16 AND NOT 148.251.45.170) AND date:[2018 TO 2019]
```
- Look for every hit in last given number of days

```
page.url.keyword:https\:\/\/www.newegg.com\/*
page.url.keyword:https\:\/\/www.newegg.com\/uploads\/*
```
- Looks for everything after that url

```
domain:newegg.com AND NOT page.domain:newegg.com
```
- Looks for everything that loaded/request newegg.com but not owned by newegg(e.g: 3rd party site loding newegg JS files)

```
page.domain:(newegg.com~ AND NOT newegg.com) 
```
- Looks for domain that are similar to the domain provided but not the same

```
page.domain:(/newe.*/ AND NOT newegg.com)
page.domain:(/newegg-.*/ AND NOT newegg.com)
```
- Looks for every domain that starts with given expression of domain but does not include the domain given

```
page.asn:AS24940 OR page.asnname:newegg
```
- Looks for sites hosted under a ASN provided or by the company name too

```
page.url:"wp-content/uploads/" OR filename:"wp-content/uploads/"
```
- Looks for site that include the path provided

```
hash:{sha256}
```
- Looks for everything that uses the hash provided(e.g: 1. create a js file name hash then pass it here it will list every site using that js, 2. find a favicon hash pass it here and it will look for every site using that favicon, 3. if a perticular file version has a cve copy the file hash and look here you will get that file used by many sites)

```
newegg.* -newegg.ca
```
- with the `-` in query the result will exculde the provided domain

```
page.domain:*.newegg.com AND (page.asnname:"Hetzner" OR page.asnname:"DigitalOcean")
```
- Looks for assest's hosted under a asn (e.g: can exclude cloudflare to find out site before cloudflares)

## Some Advanced Dork by Lostsec 
```
page.url:"/admin"
page.url:"key="
page.url:"token="
page.url:"=="
page.url:"eyJ"
page.url:"/password-reset/"
page.url:"@"
page.url:("reset-password" OR "resetpassword" OR "forget-password" OR "forgetpassword" OR "password-reset" OR "passwordreset")
page.title:"index of /"
page.title:"index of /" AND page.url:backup
page.title:"index of /" AND page.url:uploads
page.title:"index of /" AND page.url:private
page.domain:newegg.com AND page.mimeType:"application/json"
page.domain:newegg.com AND page.mimeType:"application/pdf"
page.domain:newegg.com AND page.status:500
page.domain:newegg.com AND page.status:403
page.domain:newegg.com AND page.status:301
page.title:"Control Panal" OR page.title:"Administrator" page.title:"Sign In"
gov.* page.title:"Control Panal" OR page.title:"Administrator"
mil.* page.title:"Control Panal" OR page.title:"Administrator"
gov.* page.title:"dashboard"
mil.* page.title:"dashboard"
page.title:"index of /" AND page.domain:*.gov
page.title:"index of /" AND page.domain:*.mil
page.title:"index of /" AND page.domain:*.edu
page.url:"/api/"
page.url:"v1/api/" OR "v2/api/" OR "v3/api/" OR "v4/api/"
page.url:"/api/v1/" OR "/api/v2/" OR "/api/v3/" OR "/api/v4/"
page.url:"/graphql/"
page.url:"/graphql/" page.domain:newegg.com
page.domain:newegg.com AND page.ip:*
page.title:"Swagger UI" OR page.url:"swagger" OR page.url:"swagger-ui" AND page.domain:newegg.com
page.url:
```

---
## Full Page Content

![](https://www.youtube.com/watch?v=I-J5Ht9goyc)

IF you Enjoyed the video, don't forget to Like 👍, Subscribe, and turn on the Notification Bell 🔔 to stay updated!  
  
🎭 WHO AM I ?  
  
I'm Coffinxp, a hacker & Security Researcher and aspiring Cybersecurity Specialist and Bug Hunter. With a strong passion for technology and expertise in malware analysis, vulnerability assessment, and bug hunting, my goal is to safeguard digital assets and contribute to a more secure online community..  
  
🐞 If you want to learn bug bounty hunting follow me on medium app: https://coffinxp.medium.com  
  
☕ If you want to support me, you can buy me a coffee: https://www.buymeacoffee.com/coffinxp  
  
  
🍿 WATCH NEXT METHODOLOGY  
  
1️⃣How to Access 404 files of any server https://youtu.be/abk7wT1EMzw?si=euNO3yOlCpoJoGws  
2️⃣JavaScript Recon Masterclass: Turn Bugs into Big Rewards https://youtu.be/FWPXWBh4EFw?si=3f9JZ\_r1rNfRU4wI  
3️⃣The Best XSS Methodology for Bug Bounty Hunters https://youtu.be/cRL9REGSKkM?si=EQ43OkKhE4x9N2FY  
4️⃣Mastering Origin IP Discovery Behind WAF | 11+ method https://youtu.be/R3hmZpkvCmc?si=Y-g0\_jGlmmbPlhPu  
5️⃣How to approach a target in Bug bounty programs https://youtu.be/Ifo1vIdfyhg?si=ahlMMg4WmEROR53M  
  
🧑‍💻MY OTHER SOCIALS:  
  
🌟Github - github.com/coffinxp  
🌟Twitter - @lostsec\_ftw  
🌟Website - comming soon..  
🌟Medium - lostsec.medium.com  
  
Thank you from the bottom of my heart for your incredible love and support! ❤️ You’re the reason this journey is so special! 🌟🙏  
  
Disclaimer ⚠️  
Hacking without permission is illegal.This channel is strictly educational for learning about cyber-security in the areas of ethical hacking and penetration testing & bug hunting.Our goal is to empower the community with knowledge to protect themselves against malicious activities.All content,including videos and tutorials, is created with prior permission from the relevant programs and owners.By engaging with our content,you acknowledge that you will use the information solely for educational and defensive purposes..  
  
LEMMiNO - Moon  
https://youtu.be/vH9SVshLM1g?si=7i17C0Ypqfh7iF-A  
CC BY-SA 4.0  
  
#cybersecurity #bugbounty #Dorking #WebSecurity #infosec

## Transcript

**0:03** · Hi everyone, welcome back. In this video, I'll show you some advanced URL scan dorking \[music\] techniques that can significantly improve your bug bounty hunting. These methods will help you find interesting assets and potential vulnerabilities much more efficiently.

**0:17** · By the end of this video, I'm confident you'll be using these techniques in your daily reconnaissance. So, make sure to watch until the end because you'll miss some valuable tips and techniques if you skip any \[music\] part. As always, remember that ethical hacking requires proper authorization. Make sure you have explicit permission before testing \[music\] any assets. This video is for educational purposes only. Let's get started. First, let me explain what URL scan is. It's a free service that scans and analyzes websites for fishing, malicious content, and other security related information.

**0:47** · It also comes with built-in search and dorking capabilities that make it an excellent tool for bug bounty hunters \[music\] to discover potential targets and vulnerabilities.

**0:57** · Before we dive into the dorking \[music\] techniques, let me walk you through the basic scanning process and the key features of a scan. Once you understand those, we'll move on to the advanced dorking methods and everything will make much more sense. If you're already familiar with the basics, feel free to skip this section and jump straight to the dorking methods. Now, let's begin with the \[music\] scanning process.

**1:16** · Simply visit the URL scan homepage and in the search bar, enter your target URL or domain. Once you submit it, URL scan will open the website in a real browser, visit \[music\] the pages, and analyze everything it can collect. After the scan is complete, you'll see a lot of information. Let's go through it step by step. At the top, you can see the target along with the scan date and time.

**1:39** · \[music\] In the summary section, you'll find the domain IP address, the company or hosting provider it belongs to, the number of IPs it contacted, and their locations. You'll also see how many times this URL has been scanned, \[music\] the scan verdict, and live information such as DNS records, and the domain creation date.

**1:59** · Next, in the domain and IP information section, you can explore IPASN's related domains, the domain tree, links, certificates, and frames. On the right side, you'll \[music\] see a screenshot of the web page, its title, and the technologies the \[music\] website is using.

**2:19** · Below that, you'll find detailed page statistics showing all the requests the website made while it was loading. In the HTTP section, you'll find every request \[music\] made while the page was loading. It contains all the resources requested by the website, including HTML, JavaScript files, \[music\] CSS, images, API requests, and other content. This is especially useful for bug hunting because it helps you discover hidden API endpoints, internal URLs, JavaScript files, and other resources that may not be visible from the website itself.

**2:51** · In the redirect section, you'll see the complete redirect \[music\] chain for the request.

**2:57** · This is useful for identifying open redirects. In the link section, you'll find all the internal and external hyperlinks discovered on the page. This is very useful for finding hidden pages, links, interesting endpoints, and more helpful for finding broken link hijacking.

**3:16** · The behavior section shows everything that happened while Chrome executed the page. This includes JavaScript execution, cookies that were created, local storage, console messages, and more. It's a great place to understand the client side behavior of a website.

**3:31** · In the indicators section, you'll see the domains, IP addresses, and URL scanned security analysis. It checks for suspicious indicators, and \[music\] if nothing malicious is detected, it will mainly display the related domains and IP information. The similar section finds pages that closely resemble your target. It compares HTML DOM content page structure and also looks for pages hosted on the same IP or ASN. This is extremely useful for bug hunting and I'll show you some practical examples later in the dorking section.

**4:07** · In the DOM section, you'll see the final rendered HTML after the page has fully loaded. You can inspect it for hidden \[music\] forms, hidden input fields, CSRF tokens, developer comments, and other information that developers sometimes expose by mistake.

**4:26** · The content section contains every resource downloaded by the browser, including JavaScript files, API \[music\] responses, images, CSS, and other assets. This is especially useful for reviewing JavaScript source code, API responses, and client side data.

**4:44** · The API section exposes the raw JS generated by the scan. Instead of using the visual interface, \[music\] you get structured data that can be used for scripting, automation, or parsing scan results programmatically. \[music\] Finally, in the top right corner, you can click go to to visit the target website directly. You can also quickly open the target in various lookup platforms for additional reconnaissance.

**5:18** · If you discover anything that violates URL scans policies, you can use the report option to report the website directly from there.

**5:26** · Now, let's move on to the dorking methods you've been waiting for. First, I'll explain the default search operators and query syntax supported by URL scan. Once you understand the basics, I'll show you some of my favorite manual dorking techniques that can significantly improve your bug hunting workflow. Before we start, make sure you're logged into the website.

**5:45** · Some search features only work when you're signed in. If you click on the help menu, you'll find several example search queries supported by URL scan.

**5:52** · You can also open the search API reference where you'll see every searchable field, including both free and paid features. Don't worry though, you don't need to learn every field or have a paid plan to perform effective reconnaissance. For bug hunting, we'll focus on the most useful free search operators and learn how to combine multiple query terms to create powerful dorks that help you find interesting assets much faster. Now, let's \[music\] start with the first dor.

**6:18** · This dork helps you find all websites from your target that have been scanned within the last 7 days and successfully resolved to an IP address. It's useful when you want to focus on recently scanned assets instead of outdated results. Always include your target domain in the query. You can also modify the date range to match your needs depending on how broad you want your results. You can click on details to see additional information about the target including their IP address, geoloc, ptr, reverse DNS record, ASN number, web server, and hosting information.

**6:48** · This extra information helps you understand where the target is hosted, who owns the network, and what infrastructure it's running on before you continue your reconnaissance.

**6:58** · Now, let's move on to the second dork prefix search. This search operator finds pages whose URL starts with a specific path and returns everything that comes after it. It's perfect when you want to search within a particular URL prefix instead of scanning the entire domain.

**7:25** · To make it easier to understand, let's look at a quick demo.

**7:34** · For example, take this Tesla URL. Notice that the path ends with slashupload.

**7:40** · Copy that URL prefix into your query.

**7:43** · And remember to escape every forward slash with a backslash when using it in the search.

**7:55** · Once you run the query, you'll see all URLs that begin with that prefix. In other words, rural scan will return every discovered path that appears after the specified URL prefix. This is extremely useful for discovering hidden URLs, additional endpoints, uploaded resources, and other content that shares the same base path but may \[music\] not be directly linked from the website.

**8:22** · Now, let's move on to the third dork.

**8:24** · This search operator finds pages that communicated with PayPal during the scan but are not actually hosted on paypal.com. As you can see in the results, none of the listed domains belong to PayPal. However, if you open any result and view its scan details, you'll notice that the website interacted with PayPal at some point during the page load. This simply means that PayPal appeared somewhere in the request chain, even though the website itself isn't a PayPal domain. For example, the page may have loaded a PayPal JavaScript file, made an API request, embedded \[music\] a PayPal iframe, or fetch other PayPal resources.

**8:57** · This technique is especially useful for identifying thirdparty integrations across \[music\] a large number of websites. From a bug hunting perspective, it can help you discover API integrations, payment flows, and potential COS misconfigurations or trust relationships involving third party services. Now, let's move on to the fourth dork, fuzzy domain search. This operator finds domains that look similar to your target domain, but aren't the actual domain.

**9:21** · Instead of searching for an exact \[music\] match, it searches for names that are close enough to the original, even if they're slightly different. \[music\] For example, when searching for PayPal, it can return domains with misspellings, extra characters, missing letters, or other small variations that resemble the real domain.

**9:39** · This is extremely useful for discovering typos squatting, a lookalike, and fishing domains that may be impersonating your target. It can also help you identify brand abuse, malicious infrastructure, or unofficial domains that closely resemble legitimate assets.

**9:57** · Now, let's move on to the fifth dork, regular expression domain search.

**10:02** · This search operator lets you search domains using regular expressions.

**10:06** · Unlike fuzzy search, which automatically looks for similar domain names, Reax gives you complete control over the matching \[music\] pattern. For example, if your pattern is PP, it means a domain must start with PayP, but anything can come after it. This could match domains such as paypal.com, pay.ample, payal.net, or any other domain that begins with those four letters. Reject searches are much more flexible because you define the exact pattern you \[music\] want to match.

**10:32** · This makes them useful for discovering related domains, internal naming conventions, subdomains, or assets that follow a specific format but \[music\] don't exactly match your target.

**10:44** · Now, let's move on to the sixth dor.

**10:47** · This search operator finds pages that were hosted on a specific IP \[music\] address or IP range and were scanned within the selected date range. Simply enter your target's IP address and URL scan will show you all websites hosted on that \[music\] same IP. You can also search an entire subnet or IP range to discover additional assets that share the same network. This is especially useful during reconnaissance \[music\] because it helps you identify other domains hosted on the same infrastructure.

**11:14** · It can also be used to investigate an entire hosting provider or subnet while excluding specific \[music\] servers, making it easier to map shared infrastructure and uncover related assets.

**11:25** · Now let's move on to the seventh dor asn \[music\] search. The search operator finds pages that are hosted as on a specific autonomous system number. An ASN represents a network \[music\] owned by an ISP cloud provider or hosting company. First find your target organization's ASN using websites like BGP tools.

**11:55** · Copy the ASN number and include the AS prefix in your query. Once you run the search, URL scan will return all domains and pages hosted on the ASN. This is extremely useful when you're researching a company's infrastructure or hunting for assets hosted by the same provider.

**12:12** · If you want to expand your reconnaissance even further, copy the ASN and use tools like ASN map or websites such as MX Toolbox to enumerate all the \[music\] CIR ranges announced by that ASN. You can then scan or investigate those IP ranges for additional assets.

**12:34** · You can also search by the ASN organization name instead of the ASN number by using the ASN name operator.

**12:41** · This returns assets associated with that organization's network, making it another useful way to discover related infrastructure.

**12:51** · To search an entire CI range, use the IP operator and provide the IP address with its subnet mask. Remember to escape the forward slash with a backslash in your query. Once you run the search, URL scan will return all domains and URLs that were scanned and resolved to IP addresses within that CI range. This is a great way to enumerate assets hosted on the same network. Now, let's move on to the eighth dork. This search operator uses the page URL and file name operators to find files uploaded to WordPress sites.

**13:22** · It searches for a specific path in the URL and \[music\] matches files by their file names, making it easy to discover publicly accessible uploads. \[music\] This technique is extremely useful for finding uploaded PDFs, zip archives, backup \[music\] files, images, documents, configuration files, and other resources that may have been unintentionally exposed. \[music\] Now, let's move on to the last but not least, hash search. This search operator lets you search for resources using their SHA \[music\] 256 hash.

**13:54** · For example, you can get a website's favicon hash using an online favin hash tool and search it with the hash operator. It will show you all the websites using that exact same fabicon.

**14:12** · Another example is downloading a JavaScript file with we get calculating his hash using Shaw 256 sum and searching that hash in Earl Scan. It will \[music\] return all the domains and URLs that contain the exact same file.

**14:33** · This is extremely useful for tracking reuse files, identifying identical JavaScript libraries or malware samples, and \[music\] finding websites running the same vulnerable library. If a specific library version is affected by a CVE, you can search its hash to quickly discover other targets using the same file and check whether they're vulnerable as well. If you don't want to use the default search operators, you can simply search your target using a wild card. This will return all related domains, subdomains, and URLs associated \[music\] with the target.

**15:04** · You can also search for domains containing a hyphen, which is useful for discovering subdomain such as dev, test, stage, staging, and other potentially sensitive \[music\] assets. If \[snorts\] you want to exclude a specific domain from your results, simply use a minus before the domain name. Girl Scone will filter it out from the search results.

**15:32** · You can also combine these dorks with your target to find assets hosted \[music\] on BPS providers. This technique is especially useful for discovering a target's origin a by filtering out cloud flare or other WA FCD and protected hosts and focusing on the underlying infrastructure. Now we're entering the most important part of this video.

**15:54** · Everything we've covered so far was just the foundation. From here on, I'll be sharing the manual dorks and reconnaissance techniques that I actually use to uncover hidden assets, \[music\] expand attack surfaces, and find bugs that most hunters completely miss.

**16:08** · So, don't skip this section. Grab a coffee, watch till the very end, and try every dork yourself. Sometimes, a single search query is all it takes to uncover your next valid finding. I'll also be publishing these dorks along with many more advanced techniques on my Medium.

**16:23** · If you haven't followed me there yet, make sure you do so you don't miss future bug hunting content.

**16:46** · Hey, hey, hey.

**17:40** · Heat. Heat.

**18:27** · Heat. Heat.

**18:33** · This is something.

**18:59** · Heat. Heat.

**19:22** · Heat. Heat. N.

**20:51** · Heat.

**21:17** · Heat.

**21:26** · Yeah.

**21:47** · Just for the Come on.

**22:12** · Come on.

**22:28** · Heat up

**23:03** · Hey, hey, hey.

**23:11** · Heat. Heat. N.

**23:34** · Heat. Heat. N.

**24:21** · Heat. Heat.

**24:46** · Heat. Heat. N.

**24:56** · Heat. Heat. N.

**25:23** · Heat. Heat.

**25:30** · Heat. Heat. N.

**25:51** · Hey everybody.

**26:23** · This is everybody.

**26:51** · Heat. Heat.

**26:58** · Heat. Heat. N.

**27:37** · Heat. Heat.

**27:59** · Heat. Heat.

**28:14** · Heat. Heat. N.

**28:24** · Heat. Heat.

**29:54** · Hey, hey, hey.

**30:40** · Heat. Heat.

**31:18** · Just for the day.

**31:57** · Hey, hey, hey.

**32:51** · Hey, hey, hey.

**33:31** · Heat. Heat. N.

**33:38** · Heat.

**33:59** · Heat.

**34:20** · Heat. Heat.

**34:55** · Heat. Heat.

**36:02** · Heat. Heat.

**36:09** · Heat. Heat. N.

**36:31** · Heat. Heat.

**37:30** · Just crazy.

**37:36** · Just Heat. Heat. N.

**37:56** · Heat. Heat.

**38:46** · Heat. Heat.

**39:52** · Heat. Heat.

**40:08** · That's a wrap for today's video. If you're new to the channel, make sure to hit that subscribe button so you're \[music\] always updated with our latest content. Thank you for watching and I'll see you in the next video. Take care.