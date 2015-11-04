---
layout: post
title: Get more out of your boring TypoScript constants!
feature-img: "img/constantsextended-extension-manager.png"
---

[constantsextended-extension-manager]: /img/constantsextended-extension-manager.png "How you can make your extension constants more dynamic and useful"
[constantsextended-constant-editor]: /img/constantsextended-constant-editor.png ".. and you can use it inside your constant editor!"
[imageautoresize-extension-manager]: /img/imageautoresize-extension-manager.png "Even flexforms! This is sweet!"

**Many extensions requires you to select some sort of record. Mostly this is done, by finding the correct uid and then enter it into a field.. This can be done a lot more "beautiful"!**

![How you can make your extension constants more dynamic and useful][constantsextended-extension-manager]

	How you can make your extension constants more dynamic and useful

![.. and you can use it inside your constant editor!][constantsextended-constant-editor]

	.. and you can use it inside your constant editor!

![Even flexforms! This is sweet!][imageautoresize-extension-manager]

	Even flexforms! This is sweet!

First of all, I can not take full credit for this post! A big ton of credit goes to [Georg Ringer](http://www.just2b.com), he wrote a proof-of-concept extensions, showing how these functions can be used! And many other extensions uses the same functions, big credit to these developers as well, for spreading the usage of great usability!

This post is based on the code from [the extension EXT:constantsextended.](http://typo3.org/extensions/repository/view/constantsextended) The picture to the right, show the extension manager right after you installed the extension. Pretty impressive and really good looking.

Just imagine your own extensions with these settings, where the field actually gives the user (your **customer**?) the possibility to choose a record - not write some "random integer".



## But that's not a constant editor?

No, I'm very well aware of that, and the headline of this post does promise you something to spice up your constants - so here comes! :-)

Start by looking at the second picture - you got the same fields there aswell! The "secret" (well, not really a secret :P) is that ext_conf_template.txt and your included constants.txt file uses the same syntax, when it comes to rendering a form. Just look at the constants.txt file.

For the technical interested person, it's parsed through the function _t3lib_tsparser_ext::printFields_ so if you are interested go through that code.

## Why should i use it? Is anybody even doing this?

The two quick answers is

1.	Because it makes your extensions (meaning your work and "porfolio") look professionals
2.	Yes! Indeed!

Another (important!) reason for you to use such functions is: You are "insured" (you may not depend 100% on the data, still do your checks!) that you get the correct data and not a mistyped integer, when the user should actually select a usergroup!

And when it comes to the extension have a look at **EXT:templatevoila** and the corresponding userfunction file.

And a another example would be EXT:image_autoresize where a flexform is integrated in to the extension configuration!

## But i don't know how to do!! :'(

I didn't know how to walk, bike, swim, TYPO3 etc. either, before I tried and learned from my mistakes :-)

I really think that these great examples gives you a lot of code that you can base your own work on. And if you still got questions, Opens external link in new windowuse the maillists to get help. And remember to share your own experiences, so that others can learn from that!

