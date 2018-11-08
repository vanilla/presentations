footer: Variations on SSO
slidenumbers: false

#Lunch and Learn
## Variations on SSO
#### Out-of-the-box is just not good enough for some people.

---

## Goal

 - Know the common themes of customizations.
 - Developers: What to look for when something goes wrong.
 - CSMs: Know the dangers and benefits of going off the reserve.

---

## Top Four Most Common Types of SSO Customizations

 - Meddling with Profile Data.

---

## Top Four Most Common Types of SSO Customizations

 - Meddling with Profile Data.
 - Monkeying with the Workflow Logic.

---

## Top Four Most Common Types of SSO Customizations

 - Meddling with Profile Data.
 - Monkeying with the Workflow Logic.
 - Hacking the UX.

---

## Top Four Most Common Types of SSO Customizations

 - Meddling with Profile Data.
 - Monkeying with the Workflow Logic.
 - Hacking the UX.
 - Jimmying with OAuth2.

---

## Meddling with the Profile Data.
### Why would anyone want to do that?

 - Organization that wants to add extra dimensions to user profile. (DMAI)
 - Integrated logic if they have a custom plugin: 
  - Pass the language, changes the locale of the user.
  - Complex assignment of Roles based on products owned by user (SEGA).

 
---

## Monkeying with the Workflow Logic.
### Why would anyone want to do that?

 - Organization that has an authentication system set up for multiple purposes already and cannot modify it for one service provider.
 	- Pass the language of the forum to the Log in page.
 	- Proprietery system, cannot format data (nested data in Salesforce).

---

### Monkeying with the Workflow Logic. (cont'd)
- Legal constraints:
 	- Terms of Use when signing in. (Acer)
- Security constraints:
	- Require nonce, RefreshToken, revoke Tokens (SEGA) 

---

## Hacking the UX.
### Why would anyone want to do that?

 - Company that seeks a more seamless UX.
 - Company that want to avoid using `/entry/sso` endpoints.
 - Usually employs Javascript and/or iFrame to detect if a User has an active session on the parent site.

 
---

## Jimmying with OAuth2.
### Why would anyone want to do that?
 - Implicit Flow vs. Authorization Code
 - Zyxel vs. Zyxel
 
---
### And on the subject of OAuth2.

 - Old School vs. New School
  
---

## Conclusion
### If we don't learn from history we are doomed to repeat it.

- Some are regrettable.
- Many customizations are now core features.
