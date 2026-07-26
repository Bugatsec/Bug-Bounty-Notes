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

NO RATE LIMIT
--
- On forgot password email sending
- 100+ email by sending multiple request.

INSECURE ACCOUNT DELETION
--
- No password confirmation while deleting account.

IDOR
-- 

## No Email notification sent after password change

--

## 2FA Activation does not invalidate current session

--

## Improper cache control after logout
--
- Go to a sensative page -> logout 
- click the back btn if you see the sensative data its an issue (p4 bugcrowd vrt)

## Unverified acc can enable 2fa before email verification
--

## Email/Password change without any auth/verification
--

## 2fa bypass
--
- enable 2fa -> logout
- login with oauth if 2fa is missed it might be a vuln 

## Email Verification confusion
- a site asks for email verification you give attacker@test.com recive the verification email link
- going to settings page is allowed you go and change email to victim@test.com now this mail will recive the email verification email too 
- now go to attacker@test.com inbox click the verification link verify acc with that.
- check if yr acc email is changed to victim@test.com 