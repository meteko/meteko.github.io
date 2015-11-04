---
layout: post
title: One word, a thousand meanings!
feature-img: "img/translation-pootle-translate-form.png"
---

[translation-lang-show-labels]: /img/translation-lang-show-labels.png "This is how your BE will look after enabling labels. Don't use in production!"
[translation-code-conf-debugkey]: /img/translation-code-conf-debugkey.png "The secret configuration setting!"
[translation-pootle-translate-form]: /img/translation-pootle-translate-form.png "Find/read the labels from the Pootle platform"
[translation-em-conf-settings]: /img/translation-em-conf-settings.png "EM settings in EXT:translationhelper"

**With great thanks to Dominique Feyer, we have a new and fantastic translation platform! Let's help our self to get a high translation quality! We all deserve it!**

![This is how your BE will look after enabling labels. Don't use in production!][translation-lang-show-labels]

	This is how your BE will look after enabling labels. Don't use in production!

![The secret configuration setting!][translation-code-conf-debugkey]

	The secret configuration setting!

![Find/read the labels from the Pootle platform][translation-pootle-translate-form]

	Find/read the labels from the Pootle platform

![EM settings in EXT:translationhelper][translation-em-conf-settings]

	EM settings in EXT:translationhelper

In case you haven't [read the news regarding the new translation server](http://typo3.org/news/article/new-translation-server-online/), please take your time and do that, before reading on.

Done? Good!

One of the difficult tasks, I've personally found, during translation, is to find out if my wording really fits the actually label. Does the wording really match the meaning of that particular textfield, radio button, checkbox etc.?

Sometimes translating just happens by "guessing" where in TYPO3 this label is found. Sad to say, but label names are not always as describing as they could be!

In order for you to get a better view of what labels are used where, and in what file can I find them, the [new extension translationhelper](http://typo3.org/extensions/repository/view/translationhelper) will help you.

Enable the the "Show label" settings in the backend and reload the backend. You will then see the labels for each and every string that is taken from a locallang file, using functions from the language class (getLL, getLLL etc.).

The project is [maintained at forge](https://forge.typo3.org/projects/extension-translationhelper).

If it happens, that you find some hardcoded labels, please be so kind and add them to the wiki

http://wiki.typo3.org/Hardcoded-labels

and create a issue for the TYPO3 Core Project

http://forge.typo3.org/projects/typo3v4-core/issues/new

Happy translating, it have never been easier!