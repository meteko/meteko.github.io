---
layout: post
title: baseURL is dead - long live absRefPrefix
---

In a world where CI and flexibility is the new new, I think it's time to wave goodbye to a dear old friend!

When I first started working with TYPO3 in 2003, one of the first settings to set in my TypoScript template was

	config.baseURL = whatever.local

This was really great, then all my links was prepended with the correct url.

But, when I moved it to a new installation - and a different domain - my urls was wrong :-(

Not a big deal, I can just add it as a constant and change the value... Well, yes... But how cool is it to do manual changes when ever you deploy your installation to a new platform.

Imagine having to create test environments for a team of developers, then this change will have to be made every time - uncool if you ask me.

## But how can I work around this?

Instead of prefixing your URI with a specific hostname, you can rely on the hostname requesting your installation.

**If you are having a multisite tree, it's important to create a domain record on each page level - but you most likely done that all ready :-)**

You can do this by writing the following in your TypoScript setup

	config.absRefPrefix = /

and of course, remove any instances of config.baseURL!

in this way, we tell TYPO3 to prefix all links with a "/" and don't really care about a baseURL!

And by this, you are able to move your installation around, with out caring about the baseURL - all paths are correctly written and you have removed yet another dependency on your local environment.

## What if I develop/deploy in a subfolder?

Then you can add whatever the folder name is, to the end of the value ex.:

	config.absRefPrefix = /foldername/

and then of course expect the same folder name on the production server.

## What do I actually benefit from this?

In a automatic deploy process, imagine having to replace all instances of "config.baseURL = ###" with a value of the new server environment?

I'm not a regex guru - but I've tried in once and it wasn't nice and some not wanted changes was made - plus it was hardcoded on searching for a specific hostname.

In this way, your deployment can run, without having to worry about the hostname changes.