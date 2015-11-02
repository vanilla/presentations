# [fit] Single Sign On
# [fit] Concepts, workflow, and _troubleshooting_

---

# Federated identity

---

# [fit] Flavors

* _Identity owner:_ Customer or third-party
* _Protocols:_ OpenID, OAuth, SAML, AD, jsConnect

---

# Use cases
^ very broadly speaking

* Products use OAuth (supplants OpenID)
* Enterprises use SAML & AD

**jsConnect is our solution for _indies_  
to easily authenticate over the _web_.**

^ If Vanilla was an authentication provider we'd be using OAuth, but that's very difficult for small shops to set up correctly on their own. Typically no 2 OAuth implementations are compatible.

^ jsConnect is designed to offset the work to our side.

---

# [fit] How The Web Works 
# **In A Nutshell**

* Sent _request_ receives a _response_.
* Browser > server **-or-** server > server.
* Browser requests always include _**cookies**_.

^ Response has: code, headers, payload

^ This is how jsConnect fundamentally works - sending a request from your browser.

---

# Social SSO Plugins

Twitter, Facebook, LinkedIn,   
Google+, Steam, Disqus, Gigya

# Integrations with OAuth

Salesforce, Zendesk, GitHub, Pega

---
# [fit] Let's talk about
# [fit] jsConnect

---

# You have a web login system!

2. You create a _special web page_ from our instructions.
3. Vanilla makes a request _from your browser_ to that page.
4. Your page _knows if you're logged in_ (of course).
5. Your page responds yes/no & _gives the secret handshake_.

---

# [fit] Making the sale

1. A developer should be able to integrate in _2-4 hours_.
1. We have [great docs](http://docs.vanillaforums.com/features/sso/) + examples in PHP, Java, .NET, & Ruby.
1. We are _SSO experts_. Solution is highly tested & flexible.

---

# [fit] Restrictions apply

2. We _never_ do this integration work on their behalf.
2. This is for _web-based_ systems only.
2. Client must _own_ the web server (no third-party).

---

# About that special webpage

```
test({
	"name": "Lincoln", 
	"email": "lincoln@vanillaforums.com", 
	"photourl": "", 
	"uniqueid": "123456789", 
	"clientid": "jsconnect",
	"signature": "94fbac847a78561ba9744bf7c649f4f5"
});
```
---
# **Get Set Up**

* Mapping users & Autoconnect
* Username overwriting & uniqueness
* "Connect" method & /entry/password
* Required data
* Test mode & response signing

---
# **Tighten It Up**

* Seamless sign-in & sign-out
* Profile editing & emails
* Role setting
* Embedded SSO

---
# **Caveats**

* Not an identity provider.
* Do not use API in tandem.
* Can only map on unique email.

---
# [fit] Try it yourself

Terrible Login System in the _internal_ repo.