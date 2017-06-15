footer: © 2017 Vanilla Forums
slidenumbers: true

# [fit] Theming Process Presentation
___

# Part 1: Client Mockups and Setting Expectations

---

# [fit] Reviewing mockups

* Vanilla's not a CMS
* Catch problems early if possible
* Get client to use software
	* Staging site
	* Try modules
	* Better documentation

---

# [fit] Customizations

**We need to tell the client we may not match their mockups exactly.**

* We can't change everything
* Updating is harder with modifications to core
* Responsible for our work
* Check available functionality

---

#[fit] Setting expectations with the customer

Although we can do a lot with our platform, we're only interested in development related to forums.  

Other options:
* Self hosting pages like [EA's landing page](https://forums.ea.com)
* Customize theme
* Pay for plugins or new features
* VIP

---

#[fit] Checking Modules and Features

Note that Vanilla's **theming service does not provide new features**. If a client wants to add custom plugins or modules, it needs to be estimated on seperately.


---

# [fit] Providing customer design guidance

* Give them options (they want ownership of their form)
* Ask them what their goal is
* Explain problems

---

# [fit] Part 2: Feedback

---

# [fit] How to get good feedback from the customer

Feedback documents can be very long. **Clear, concise** reports will help in solving issues faster. 


* Point form is encouraged
* Minimum steps necessary to reproduce a bug 
* Simplify feedback sheet as tasks are complete

Use and improve new spreadsheet


---

# [fit] Feedback form

* Title
* Description
	* Be specific, no relative terms
* Steps to reproduce

---

# [fit] Feedback form

* Problem location
	* *URL*
	* Browser and version
	* Device
	* OS
* Screen cap (optionnal)

---

# Part 3: Custom Themes

---

# [FIT] Base Themes

* Standard themes that come with vanilla
* Many are outdated
* New base themes coming

---

# [fit] A few important themes to know:


* **+Baseline**: *Almost all themes still have these baseline styles and the rest of the styles are layered on top.*

* **Bootstrap3**: *Very popular theme. Many clients that want to customize their own theme use this one.*

* **Deflector**: *Very good theme. Often used as a base since it's using modern development tools.*

---

# [fit] Steps to make a new theme

Also applicable to :
* New modules
* Features
* Bug fixes

---

# [fit] Local development

* Make a *branch*
* Work on it loally

---

# [fit] Staging Environment


Once the theming dev is satisfied with the theme, we'll push it to **staging**. 

* Testing
* Sharing work
* Trying stuff out

*Note: that not all clients have their own staging, but most clients asking for a custom theme do*.

---

# [fit] Production Environment

When the client has approved the theme on the **staging**, the theme will be in **PR**. This basically means that another dev must review the work before it gets accepted into the main **branch** of code we use on production sites. Once the PR is merged, we can update the production site.

---

# [fit] Steps for developping a new feature in Vanilla:

* Make a new branch
* Make desired modifications locally
* Update staging
* Get feedback (from client and possibly internally)
* Make PR
* Get feedback (internal feedback)
* Merge to master
* Push to production

---

# [fit] Note about tight deadlines

* PRs are hard to estimate
* They can be long to complete
* You can bug your dev to get them done earlier than later in the day

---

# [fit] Note about updating Pockets


**Pocket** content is not in the source code for the theme. 

* New ones can be done ahead of time
* Existing ones need to be updated with the update

If a client has a staging site **always test them on staging first!** 

---


# Part 3: Alternate workflows for DIY themes & those expectations

* Open Source (Self host)
* VIP access
* Customize theme

**Our business is not to be a CMS and we're not a "CSS Help Hotline".**

---

#[fit] Customize Theme Plugin

* Can easily snowball
* Sometimes better to start from scratch, difficult to estimate consequences
* Can cost us money for support
* Should not be available by default
* Keep them responsible

---

#[fit] Questions?
