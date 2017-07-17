# Editing the Docs for CSMs

---

# Overview

**What do I need to know?**

  * What are the docs made with
  * Tools I need
  * File formats I need to know
  * Actually making changes on Git Hub


---

# What's a Static Site Generator?

* A tool for making websites (i.e. It's a style of CMS)
* Converts simple text files into HTML
* We use Hugo **[https://gohugo.io/content/](https://gohugo.io/content/)**

---

# Get a "REAL" text editor

re·al
ˈrē(ə)l
adjective

*A proper text editor for writing code.*


**synonyms**: Submlime Text Editor **[https://www.sublimetext.com/](https://www.sublimetext.com/)**

**antonyms**: Microsoft Word, Google Docs, Text Edit

---

# Markdown Editor

You might also want to get a markdown editor. 

(More on this later)

I suggest **[https://typora.io/](https://typora.io/)**

---

# File Formats : **YAML**

Used for "meta" information about page 

**[http://gohugo.io/content/front-matter/#yaml-example](http://gohugo.io/content/front-matter/#yaml-example)**

```
---
title: Services
tags:
- Services
menu:
  internal:
    identifier: services
    weight: 100
---
```

---

# File Formats : **YAML**

For more info about menus see: 

**[https://gohugo.io/extras/menus#advanced](https://gohugo.io/extras/menus#advanced)**

*Keep in mind a lot of examples on Hugo's site are in TOML*

---

# File Formats : **Markdown**

Markdown is used for the page's content. 

Use Typora to test out your styles

Use this as a general guide: **[https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)**

---

# File Formats : **Markdown**

There are a lot of flavous of markdown floating around. Hugo might not support everything you find online

*Don't set an H1 (**#**), since it's added automatically.*

---

# Making Changes

Make sure you're on the right repo!

For **https://internal.vanillaforums.com/**:
*https://github.com/vanilla/process-docs*

And for **http://docs.vanillaforums.com/**
*https://github.com/vanilla/docs*

___

![newBranch](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/newBranch.png)

___



# Editing or creating content



The site's content is all under the **/content** folder.

Find the file you want to edit and edit the edit button.



___



![edit](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/edit.png)



___



# Commit Changes **i.e. Saving**

Make sure to add a title and description of what you're doing, and then "commit changes". You're saving your changes to your branch, you haven't yet modified the production code. Leave radio button to default option.



___



![commitchanges](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/commitChanges.png)



___

# New file

Creating a new file is very similar.



* Go to desired folder

* Click **Create New File**

* Commit changes

  ​

___

![newFile](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/newFile.png)

---

# Making a PR **Branches**

1. Go to the root of the project
2. Click on branches

___



![branches](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/branches.png)



___

# Create new Pull Request



Find your branch, click the Create new Pull Request button. 

_______

![New Pull Request](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/New Pull Request.png)

___

# Create new Pull Request: **details**

Then give it a title and a description and create it. 

___

![OpenPR](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/OpenPR.png)



___

# Create new Pull Request: **Review**

Ask other for their opinion. You can **assign** that PR amongst yourselves for feedback. 

Once you're happy, assign it to a dev to merge it. They may have feedback for you.

You can see the list of PRs, by clicking on the "Pull requests" link at the top of GitHub's page

___

# Pull Requests: **Finding Them**

If you want get back to a PR, they're always available on GitHub in the **Request Tab**. Make sure everytime you're on the right branch.



___

![PR_List](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/images/editing-docs-for-CSMs/PR_List.png)



---

# Resources

Don't forget Hugo has a lot of documentation.


You can also always ask your friendly neighbourhood programmer!
