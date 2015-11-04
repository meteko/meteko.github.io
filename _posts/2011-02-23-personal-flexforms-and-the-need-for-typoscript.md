---
layout: post
title: Personal flexforms and the need for TypoScript
---

How do you cope with flexforms giving the user way to many possibility for "customization" - or should i say "frustrations" :-)

Original EXT:rgsmoothgallery flexform


Simplified EXT:rgsmoothgallery flexform


Configuring FlexForm field access in backend usergroups

When i first started with TYPO3 (from version 4.2) i loved the flexform concept! And I still do!

Later, when I started working with TYPO3 at work, a need for the flexforms to get more user friendly started to show. And then, what should I do? I couldn't/shouldn't change the flexform XML, then I would loose my changes at next update.

I found a temporary solution! I wrote a new FlexForm XML file and changed the original path through the $TCA array!

 
{% highlight php %}
<?php
	$TCA['tt_content']['columns']['pi_flexform']['config']['ds']['rgsmoothgallery_pi1,list'] = 'FILE:fileadmin/flexforms/rgsmoothgallery/flexform_ds.xml';
?>
{% endhighlight %}

The only disadvantage that I could find, is that every user will have that FlexForm, no matter what!

**But along came Kai!**
Then, one day a e-mail made it way to my mailbox (through the core list). It was a feature request, making it possible to decrease the number of fields available in a flexform!

http://bugs.typo3.org/view.php?id=16334

To demonstrate it, try installing Opens external link in new windowEXT:rgsmoothgallery and put the following in to your Page TSConfig

 

	TCEFORM.tt_content.pi_flexform {
		rgsmoothgallery_pi1 {
			advanced {
				disabled = 1
			}
			sDEF {
				heightgallery.disabled = 1
				widthgallery.disabled = 1
				height.disabled = 1
				width.disabled = 1
				startingpointrecords.disabled = 1
				text.disabled = 1
				time.disabled = 1
				mode.disabled = 1
			}
		}
	}
 

And you will see the SmoothGallery FlexForm being only a field where you can choose the folder of images.

I find that way more user friendly!

Now you might think: What about me and my admin rights? I should be able to see way more!

Then put the TSConfig inside

 

	[adminUser = 0] 
		// The code for custom flexform here 
	[GLOBAL]
 

**If you have many different editors/usergroups**
Along with Kais patch, he also introduced a way to handle the FlexForm access in backend usergroups! But, when new stuff is introduced to the core, extensions have to adjust to these new features aswell!

In order to make a field "excludable" on usergroup level, you will have to add a new tag to your FlexForm XML!

 

	538     <pages>
	539		<TCEforms>
	540             <exclude>1</exclude>
	541             <label>LLL:EXT:tt_news/locallang_tca.xml:tt_news.pi_flexform.startingpoint</label>                                                                                 
	542             <config>
 

The <exclude> tag is found by the core, and makes the field available when editing your backend usergroup. As you can see, EXT:tt_news has already adopted this <exclude> setting, but only on some of there FlexForm settings

**What about the missing settings?**
This is where the TypoScript comes in handy! If you want to give your users a user friendly FlexForm you need another way to set the settings the user doesn't have access to anymore!

With EXT:rgsmoothgallery it's no problem (I've done it myself at work) since it got great configuration possiblities! Just check out the Opens external link in new windowconfiguration reference!

Or read along

 

	plugin.tx_rgsmoothgallery_pi1 {
		mode = DIRECTORY
		lightbox = 1
		showThumbs = 1
		arrows = 1
		pathToJdgalleryCSS = fileadmin/extensions/jdgallery.css
		pathToSlightboxCSS = fileadmin/extensions/slightbox.css
		_LOCAL_LANG.dk {
			textShowCarousel = Billeder
			errorIncludeStatic = Fejl! Inkluder den statiske TypoScript skabelon
			textOpenImage = Vis billede
		}
	}
 

And now there s no doubt in how this extension is rendered, because the user only got one single setting in the FlexForm. And should the user request a new setting, and it's available in the FlexForm, I can easily activate it - but it's harder to remove a setting from a user, if they have getting used to it!

**So, dear TYPO3 extension developers!**

Remember the power of TypoScript! It makes the job so much easier for you and your TYPO3 Administrators to configure TYPO3 in a nice way!

Please read the Opens external link in new windowTypoScript - PHP Interaction wiki page, and get the TypoScript in there! :-)


