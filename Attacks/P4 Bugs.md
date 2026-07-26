---
tags:
  - Attack
  - Bugs
---
https://youtu.be/Rm8PwWsYKxo?si=okZbZymg-hNr9m3O

**SESSION NOT EXPIRED AFTER PASSWORD CHANGE**
--

**HTML INJECTION IN EMAILS**
--
- injecting username with html
- then sending forgot password email.

**HYPER LINK IN EMAIL**
--
- by injecting username with html and then sending forgot password email
- email will show injected html.

**PASSWORD RESET LINK OVER HTTP**
--

**IP ORIGIN BY PASS**
--
- Cloudflare Origin Ip finding

**NO RATE LIMIT**
--
- On forgot password email sending
- 100+ email by sending multiple request.

**INSECURE ACCOUNT DELETION**
--
- No password confirmation while deleting account.

**IDOR**
-- 

## **No Email notification sent after password change**

--

## **2FA Activation does not invalidate current session** 

--

## Improper cache control after logout
--
- Go to a sensative page -> logout 
- click the back btn if you see the sensative data its an issue (p4 bugcrowd vrt)