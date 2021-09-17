# The Getz Lab website

Our website, [www.getzlab.org](http://www.getzlab.org), is a [GitHub Pages](https://pages.github.com/) site built with [Jekyll](https://jekyllrb.com/) (a static site generator written in ruby) and [Bootstrap](http://getboostrap.com).  The software framework was forked from [Alan Drummond's site](http://drummondlab.org), which was originally pulled from [Trevor Bedford's site](http://bedford.io) and heavily modified.

Content and presentation are separated.  To add content to the site, you will simply need to update or add new markdown files, commit your changes to this repo's master branch and those changes will automatically be deployed to the public site.

We chose this platform for the lab's website to enable "crowdsourcing" of the website's content: lab members will be responsible for maintaining their own member webpages and publication authors will be responsible for adding links to their publications on the site's Papers pages.  A handful of lab members will be responsible for maintaining the Tools, Portals and Join (i.e., job listings) pages.

# Editing the site

Here's a step-by-step guide to making modifications to the site. We will first focus on adding the most common content (member pages and paper pages).  We will then discuss creating/updating the remaining content categories.

## Software Requirements

You'll need a working Unix-like environment and working knowledge of Git, [Markdown](https://daringfireball.net/projects/markdown/syntax), HTML, and Unix commands. You'll need a working Ruby installation, with gems for Jekyll, GitHub Pages, and their dependencies installed. Ruby and gem installation is quite straightforward, UNLESS you have one of the new M1 Macs.  We will be providing detailed instructions on how to do these installations.

## Clone the repository

If you're a member of the [all_getzlab team](https://github.com/orgs/getzlab/teams/all_getzlab), you have write access to the website repository.

Clone the repository, making a local copy on your machine:

	git clone https://github.com/getzlab/getzlab.github.io.git

Enter your local repository and check out the `staging` branch, where you'll make changes before promoting them to the `master` branch and publishing them:

	cd getzlab.github.io
	git checkout staging

## Overview of the structure

A site is a collection of HTML pages. For our site (and many others), there are page types, like a paper page or a lab member page, which are the same in design but different in content. In the web-accessible site, these are indeed different pages. However, they are _generated_ from a single template file filled in with information from many paper- or member-specific data files. This generation is done every time the site changes; it's handled by GitHub Pages, the service we use.

The template files are weird-looking HTML files (containing jekyll site variables and control logic) residing in the `_includes/themes/lab` folder.  You should not alter the contents of this folder.

## How to add content

For most common actions---adding a lab member, paper, or portal---you'll be making a new Markdown file in the proper location, naming it properly, and filling in the required fields. The markdown files contain a YAML front matter block which is processed by Jekyll.  Different categories of website content (e.g., paper, member, portal) have different YAML dictionary keys in their front matter, so in almost all cases you can (and should!) copy an existing item, change the name, and change its content, rather than trying to write a Markdown document from scratch.

For example, suppose you recently had a paper published and want it listed in the Getz Lab website.  Recently published papers (six most recently published) appear on the front page under the heading "Recent Papers" and all papers added to the website will appear under Selected Papers, navigated to by selecting Papers in the top nav bar. Creating a new paper "post" in the `papers/_posts` folder will add your new publication to the website's publications listings.  Go into the `news/_posts` folder. Copy one of the existing items into a new file whose name is prefaced with the paper's publication date (this is important!) and a abbreviated version of the title.  For example, we want to add a recent (5/1/2021) Cancer Discovery paper co-authored by are large team of researchers where Gaddy wasis a co-senior author and Yosi Maruvka is a co-first author.  The paper's title is "DNA Polymerase and Mismatch Repair Exert Distinc Microsatellite Instability Signatures in Normal and Malignant Human Cells".  First thing we do is cd to the papers/_posts subdirectory and, using a recent paper post as a template, create a file for our new publication:

	cp 2021-04-22-rebc-genomic-profile.md 2021-05-01-mismatch-repair-msi-signatures.md

The date is used by the static file generator; it's inelegant and perhaps there's a way to do it differently, but that's how it is for now. Now edit the new file to make the content what you want. Just open it in your favorite editor and type away. By the time you're done, hopefully you have something like this:

	---
	layout: paper
	title: "DNA Polymerase and Mismatch Repair Exert Distinct Microsatellite Instability Signatures in Normal and Malignant Human Cells"
	year: "2021"
	nickname: mismatch-repair-msi-signatures
	journal: "Cancer Discovery"
	volume: 
	author: "Chung J, Maruvka YE, Sudhaman S, Kelly J, Haradhvala NJ, Bianchi V, Edwards M, Forster VJ, Nunes NM, Galati MA, Komosa M, Deshmukh S, Cabric V, Davidson S, Zatzman M, Light N, Hayes R, Brunga L, Anderson ND, Ho B, Hodel KP, Siddaway R, Morrissy AS, Bowers DC, Larouche V, Bronsema A, Osborn M, Cole KA, Opocher E, Mason G, Thomas GA, George B, Ziegler DS, Lindhorst S, Vanan M, Yalon-Oren M, Reddy AT, Massimino M, Tomboc P, Van Damme A, Lossos A, Durno C, Aronson M, Morgenstern DA, Bouffet E, Huang A, Taylor MD, Villani A, Malkin D, Hawkins CE, Pursell ZF, Shlien A, Kunkel TA, Getz G, Tabori U"
	first_authors: "Chung J, Maruvka YE"
	senior_authors: "Getz G, Tabori U"
	corresponding_authors: "Getz G, Tabori U"
	image:
	pdf:
	pdflink: https://cancerdiscovery.aacrjournals.org/content/11/5/1176.long
	doi: 10.1158/2159-8290.CD-20-0790
	pmid: 33355208
	pmicd: PMC8223607
	category: paper
	published: true
	peerreview: true
	tags: []
	---

	# Abstract

        Although replication repair deficiency, either by mismatch repair deficiency (MMRD) and/or loss of DNA polymerase proofreading, can cause hypermutation in cancer, microsatellite instability (MSI) is considered a hallmark of MMRD alone. By genome-wide analysis of tumors with germline and somatic deficiencies in replication repair, we reveal a novel association between loss of polymerase proofreading and MSI, especially when both components are lost. Analysis of indels in microsatellites (MS-indels) identified five distinct signatures (MS-sigs). MMRD MS-sigs are dominated by multibase losses, whereas mutant-polymerase MS-sigs contain primarily single-base gains. MS deletions in MMRD tumors depend on the original size of the MS and converge to a preferred length, providing mechanistic insight. Finally, we demonstrate that MS-sigs can be a powerful clinical tool for managing individuals with germline MMRD and replication repair–deficient cancers, as they can detect the replication repair deficiency in normal cells and predict their response to immunotherapy.

        **Significance**: Exome- and genome-wide MSI analysis reveals novel signatures that are uniquely attributed to mismatch repair and DNA polymerase. This provides new mechanistic insight into MS maintenance and can be applied clinically for diagnosis of replication repair deficiency and immunotherapy response prediction.

Now add it to the repository:

	git add 2021-05-01-mismatch-repair-msi-signatures.md

And, when you're happy with it, commit and push:

	git commit -m "Yosi's mismatch repair msi signature paper"
	git push

This new paper won't yet be public. The next section shows you how to do that.

The same basic process is used to add other content classes; i.e., portals, positions, and team members.  We will describe in subsequent sections the contents of the YAML front matter block for each content class.  A different process, which we will also describe in a subsequent section, is used to add content about a tool to the website (tool information is drawn from the tool's public github repository).

## Updating the public site

All edits should be made on the `staging` branch. When you start work, make sure you're on the staging branch:

	git checkout staging

Once your edits are done, preview the site. Generate the pages and start the private webserver:

	rake preview

...and then open the local test site, http://127.0.0.1:4000. Look at anything you've changed and make sure it's good to go.

[Rake](https://github.com/ruby/rake) is a Make-like program implemented in ruby and part of the ruby/jekyll environment on which our website is built.

To move the changes to the `master` branch:

	git checkout master
	git merge staging

and push to GitHub:

	git push

Changes won't be immediate, so wait a minute or two while GitHub's servers regenerate the site and publish it. Check to make sure the public site [www.getzlab.org](http://www.getzlab.org) looks the way you intend.

Finally, check out `staging` again so that you don't accidentally start working on the `master` branch the next time you sit down:

	git checkout staging

We will probably want to implement a pull request procedure for review of new content before it is published to the public site.

## Changing look and feel

Fonts, colors, spacing, and similar stylings are separate from the template pages. Like most sites, we use Cascading Style Sheets (CSS).  Much of this is borrowed from the [Alan Drummond's site](http://drummondlab.org) but may be updated over time (based on input from the web designers in the Broad's [Patterns team](https://pattern.broadinstitute.org/).

# Content Classes
## papers
## team
## portals
## positions
## tools

# To-dos

See Issues on [the site](https://github.com/drummondlab/drummondlab.github.io).


# License

[MIT](http://opensource.org/licenses/MIT)
