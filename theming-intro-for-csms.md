footer: © 2017 Vanilla Forums
slidenumbers: true

# [fit] Theming Process Presentation
___

# Part 1: Client Mockups and Setting Expectations

---

# [fit] Reviewing mockups

Vanilla's not a CMS.  We need to be careful reviewing mockups, since if we don't catch problems early, the client's expectation will not match what we'll deliver.

---

# [fit] Reviewing mockups

If we set their expectation early of the functionality they're getting, they're much more likely to be happy with the end result. 

---

# [fit] Reviewing mockups

The more familiar with client is at the start with the product the better. If a client has a staging site, set up some modules for them to try out before they start designing. You can set sub communities, categories and plugins long before development starts. 


---

# [fit] Customizations

**We need to tell the client we may not match their mockups exactly.**

We can't customize every part of our software. It would make it difficult or impossible to update the client with any new features. We ideally want to only do a *paint job* in CSS and some minor tweaks to the template.

---

#[fit] Setting expectations with the customer

Once we make customizations, we're also responsible to support those themes going forward.

Some companies are very picky about their branding. It might be difficult to swallow for some, but if they want to have access to all our features and updates, that's how it must be. 

---

#[fit] Setting expectations with the customer

Although we can do a lot with our platform, we're only interested in development related to forums.  If a client wants custom pages that are not related to forums, it may be a better idea for them to self host those pages. A good example of this is [EA's landing page](https://forums.ea.com). 

---

#[fit] Setting expectations with the customer

If they really want full control, they can make customizations themselves. (More on this in part 3).


---

#[fit] Checking Modules and Features

When reviewing mockups, make sure the "modules" in the mockup are real Vanilla modules. Sometimes the client has similar modules that aren't exactly like the existing ones. 

---

#[fit] Checking Modules and Features

Note that Vanilla's **theming service does not provide new features**. If a client wants to add custom plugins or modules, it needs to be estimated on seperately.


---

# [fit] Providing customer design guidance

It's a good idea to explain to them why a certain idea won't work instead of only telling them no. When possible, offer a few different options to the client. It is their forum and they want to feel they have ownership over it.

---

# [fit] Part 2: Feedback

---

# [fit] How to get good feedback from the customer

Feedback documents can be very long. **Clear, concise** reports will help in solving issues faster. Point form is encouraged. Keep only the minimum steps necessary to reproduce a bug. When multiple rounds of feedback are needed, please only include what's left to do. There can be a lot of information to read through.

---

# [fit] How to get good feedback from the customer

We've made a spreadsheet for client feedback. Often times clients will give very vague descriptions. Here's what we ask for bug reports:

---

# [fit] Feedback form

**Title** 
  
A good title should describe the bug enough to recognize it, without too much info. (That's what the description is for)

---

# [fit] Feedback form

**Description** 

Be specific here. Don't use relative terms. Instead of saying **"Font is too small"**, say **"The font size should be 20px"**.

---

# [fit] Feedback form

**Steps to reproduce** 

Please provide a series of concise steps of how to duplicate the issue. *(If it's simply a display problem with no actions required, this step is unnecessary.)*

---

# [fit] Feedback form

**Where was the problem?**

  * **URL** 
  * **Browser and Version** 
  * **Device** 
  * **OS**

---

# [fit] Feedback form

* **Screen Cap** (Optional)

---

# Part 3: Custom Themes

---

# [FIT] Base Themes

These are themes that come with Vanilla. Many of them are outdated and we don't really want to base any new themes off of them. We are working on getting a new base theme, but it's still a ways off. 

Can be used as is, or as a base for a custom theme.

---

# [fit] A few important themes to know:


* **+Baseline**: *Almost all themes still have these baseline styles and the rest of the styles are layered on top.*

* **Bootstrap3**: *Very popular theme. Many clients that want to customize their own theme use this one.*

* **Deflector**: *Very good theme. Often used as a base since it's using modern development tools.*

---

# [fit] Steps to make a new theme

*(In this example, we're talking about a theme, but these steps could be for adding a new module, a feature, a bug fix or anything else that requires an update to the code.)*

---

# [fit] Local development

When making a new them, we don't want to redo *everything*, so we'll make a **branch** of an existing theme. We'll modify it to match the client's mockups. 

---

# [fit] Staging Environment

Once the theming dev is satisfied with the theme, we'll push it to **staging**. This site is not intended for the general public. It's a place where the client can test out their forum before it goes live on the **production** site.

*Note: that not all clients have their own staging, but most clients asking for a custom theme do*.

---

# [fit] Production Environment

When the client has approved the theme on the **staging**, the theme will be in **PR**. This basically means that another dev must review the work before it gets accepted into the main **branch** of code we use on production sites. Once the PR is merged, we can update the production site.

---

# [fit] Steps for developping a new feature in Vanilla:

* Make a new branch
* Make desired modifications locally
* Update staging
* Get feedback (from client)
* Make PR
* Get feedback (internal feedback)
* Merge to master
* Push to production

---

# [fit] Note about tight deadlines

When a dev makes a PR, they won't really know how long it'll take for it to complete. First of all the dev reviewing the work may have other, more important tasks to do. 

---

# [fit] Note about tight deadlines

Second, when you make a PR, you don't know how much feedback you'll get. If you really need to push anything to production, it's good to let the dev know sooner than later. 

---

# Updating Pockets

**Pocket** content is not in the source code for the theme. It's in the database of the Vanilla Instance. You need to directly add them to an envionment, they won't get updated automatically.

---

# Updating Pockets

If new pockets are added with an update, you can set them up prior to the push to production. This will avoid rushing after an update to enter all the pocket information.


---

# Updating Pockets

If a client has a staging site **always test them on staging first!** 

---


# Part 3: Alternate workflows for DIY themes & those expectations

Vanilla is open source. A client could make their own custom theme from scratch. However, if they're hosting their forum with us, they will need to have VIP status to access the code. If a client is tech savvy enough, they may be able to use the **customize theme plugin**, but use with caution.

---

#[fit] Customize Theme Plugin

**Our business is not to be a CMS and we're not a "CSS Help Hotline".** It has happened in the past that a client has made their own theme, then hired us to fix just a few issues and we ended up needing to fix their whole theme. 

---

#[fit] Customize Theme Plugin

Clients that decide to make their own theme need to be aware that if they get stuck or build their theme poorly, they may need to pay the equivalent of a full theme for us to fix it. Debugging a client's theme can take longer than making it from scratch, and can potentially cost us a lot of money in support.

---

#[fit] Customize Theme Plugin

Customize theme **should not** be available by default to the clients. They need to be aware that they can break their theme with the Customize Theme plugin. Once they've used Customize Theme, updates to their proprietary theme become more complicated. 

---

#[fit] Customize Theme Plugin

It's very difficult to estimate the consequences of the clients CSS if they've written a lot of it. Once we've touched it, the line is blurry between what we support and don't support. If a client has made customizations to their theme and we're asked to work on it, they need to **stop** making modifications. We don't want a moving target. 

---

#[fit] Customize Theme Plugin

Ultimately, it's the dev's call if the changes are benign enough to be integrated into a proprietary theme or not. If the client is using a stock theme, we can't integrate their changes.

---

#[fit] Customize Theme Plugin

If they are using customize theme, they need too know what they're getting into.

---

#[fit] Questions?
