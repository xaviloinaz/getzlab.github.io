# The Getz Lab main website

Our website, http://www.getzlab.org, is a [GitHub Pages](https://pages.github.com/) site built with [Jekyll](https://jekyllrb.com/) (a static site generator written in ruby) and [Bootstrap](http://getboostrap.com).  The software framework was forked from [Alan Drummond's site](http://drummondlab.org), which was originally pulled from [Trevor Bedford's site](http://bedford.io) and heavily modified.

Content and presentation are separated.  To add content to the site, you will simply need to update or add new markdown files, commit your changes this repo's master branch and those changes will automatically be deployed to the public site.

We chose this platform for the lab's website to enable the "crowdsourcing" of the website's content: lab members will be responsible for maintaining their own member webpages and publication authors will be responsible for adding links to their publications on the site's Papers pages.  A handful of lab members will be responsible for maintaining the Tools, Portals and Join (i.e., job listings) pages.

# Editing the site

Here's a step-by-step guide to making modifications to the site. We will first focus on adding the most common content (member pages and paper pages).  We will then discuss creating/updating the remaining content categories.

## Software Requirements

You'll need a working Unix-like environment and working knowledge of Git, [Markdown](https://daringfireball.net/projects/markdown/syntax), HTML, and Unix commands. You'll need a working Ruby installation, with gems for Jekyll, GitHub Pages, and their dependencies installed. Ruby and gem installation is quite straightforward, UNLESS you have one of the new M1 Macs.  We will be providing detailed instructions on how to do these installations.

## Clone the repository

If you're a member of the [all_getzlab team](https://github.com/orgs/getzlab/teams/all_getzlab), you have write access to the website repository.

To clone the repository, making a local copy on your machine:

	git clone https://github.com/getzlab/getzlab.github.io.git

Enter your local repository and check out the `staging` branch, where you'll make changes before promoting them to the `master` branch and publishing them:

	cd getzlab.github.io
	git checkout staging

## Overview of the structure

A site is a collection of HTML pages. For our site (and many others), there are page types, like a paper page, or a lab member page, which are the same in design but different in content. In the web-accessible site, these are indeed different pages. However, they are _generated_ from a single template file filled in with information from many paper- or member-specific data files. This generation is done every time the site changes; it's handled by GitHub Pages, the service we use.

The template files are weird-looking HTML files residing in the `_includes/themes/lab` folder.  You should not alter the contents of this folder.

## How to add content

For most common actions---adding a lab member, paper, or portal---you'll be making a new Markdown file in the proper location, naming it properly, and filling in the required fields. In almost all cases, you can (and should!) copy an existing item, change the name, and change its content, rather than trying to write a Markdown document from scratch.

For example, suppose you recently had a paper published and want it listed in the Getz Lab website.  Recently published papers (six most recently published) appear on the front page under the heading "Recent Papers" and all papers added to the website will appear under Selected Papers, navigated to by selecting Papers in the top nav bar. Creating a new paper "post" in the `papers/_posts` folder will add your new publication to the website's publications listings.  Go into the `news/_posts` folder. Copy one of the existing items into a new file named with today's date (it matters!) and a brief title:

	cp 2021-04-22-rebc-genomic-profile.md 2021-05-20-mm-immune-microenvironment.md

The date is used by the generator; it's inelegant and perhaps there's a way to do it differently, but that's how it is for now. Now edit the new file to make the content what you want. Just open it in your favorite editor and type away. By the time you're done, hopefully you have something like this:

	---
	layout: paper
	title: "Inflammatory stromal cells in the myeloma microenvironment"
	year: "2021"
	shortref: "Sklavenitis-Pistofidis et al. Nature Immunology 2021"
	nickname: 
	author: "X. Obsequious Trenchant"
	author_handle: "xot"
	image: /assets/images/news/default-news.png
	category: news
	tags: [breakthrough]
	---
	Today we are thrilled to announce a new strain of yeast that secretes beautifully oaked chardonnay. See more details in our [preprint](http://biorxiv.org/content/10.1101/0000000)!

Now add it to the repository:

	git add 2020-01-31-wine-yeast.md

And, when you're happy with it, commit and push:

	git commit -m "announcing new yeast strain"
	git push

This new announcement won't yet be public. The next section shows you how to do that.

The same basic process is used to add protocols, team members, etc.

## Updating the public site

All edits should be made on the `staging` branch. When you start work, make sure you're on the staging branch:

	git checkout staging

Once your edits are done, preview the site. Generate the pages and start the private webserver:

	rake preview

...and then open the local test site, http://127.0.0.1:4000. Look at anything you've changed and make sure it's good to go.

Then move the changes to the `master` branch:

	git checkout master
	git merge staging

and push to GitHub:

	git push

Changes won't be immediate, so wait a minute or two while GitHub's servers regenerate the site and publish it. Check to make sure the public site http://drummondlab.org looks the way you intend.

Finally, check out `staging` again so that you don't accidentally start working on the `master` branch the next time you sit down:

	git checkout staging

## Changing look and feel

Fonts, colors, spacing, and similar stylings are separate from the template pages. Like most sites, we use Cascading Style Sheets (CSS), 

### To-dos

See Issues on [the site](https://github.com/drummondlab/drummondlab.github.io).


## License

[MIT](http://opensource.org/licenses/MIT)
