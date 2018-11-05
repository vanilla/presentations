# SSO

## Single Sign On

^ This is a review, if you have questions raise your hand, if you've heard it too many times yawn loudly.

SSO is any *framework* of access control where a user logs in with a single ID and password to gain access to a connected system or systems without using different usernames or passwords, or in some configurations seamlessly sign on at each system.

---

## 3 Players in Process

 - Client or Services Provider (*i.e. wonka.vanillacommunity.com*)
 - Resource Owner (*i.e. Joe Schmoe*)
 - Authorization Server or Identity Provider (IDP) (*i.e. Auth0.com*)

---

## 3 Actions in Process

 - Sign On Initiation on Client. (*i.e. Joe Shmoe clicks on Sign In button*).
 - Handshake. Or Fistbump. (*i.e. Wonka.vanillacommunity.com redirects to Auth0.com who determines if Joe Schmoe is signed into their system or needs to be signed in.*)
 - Authentication Response. (*i.e. When Auth0 determines Joe Schmoe is logged in, it redirects Joe back to the forum and communicates in a secure way that this **is** Joe Schmoe and he's all right*) 

---

## Vanilla's Various Flavours

 * OAuth2
 * SAML
 * JSConnect, VanillaConnect
 * JSON Web Token
 * Facebook, Google, LinkedIn, etc.

All do the fistbumping differently. What is the same?

---

## Entry Connect Script

### 90% of the magic happens in /entry/connect

Every difference occurs in `ConnectData` hook. Be on the look out for `function base_connectData_handler($sender, $args)`

---

## What's common

 - All are able to tell if a user exists on our system by checking:
   1. UniqueID
   2. Email
   3. Name  
 - All are able to receive and process Roles.
 - All can capture Profile Extender data.

--- 
## Next Talk

 - Security - How do the parties trust one another.

---

## Questions, Comments, Compliments