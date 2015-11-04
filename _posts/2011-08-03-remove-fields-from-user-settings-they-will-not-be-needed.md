---
layout: post
title: Remove fields from User Settings, they will not be needed
feature-img: "img/buzz-user-settings-personal.png"
---

[buzz-user-settings-personal]: /img/buzz-user-settings-personal.png "Way too many fields!"
[buzz-overridden-field]: /img/buzz-overridden-field.png "A field overridden (overruled?) by setup.override"
[buzz-user-settings-personal]: /img/buzz-user-settings-personal.png "Mmm, the field is removed - less to worry about by the user!"

**Have you ever wondered how to remove some of the fields from the User Settings module, without loosing important settings?**

![Way too many fields!][buzz-user-settings-personal]

	Way too many fields!

![A field overridden (overruled?) by setup.override][buzz-overridden-field]

	A field overridden (overruled?) by setup.override

![Mmm, the field is removed - less to worry about by the user!][buzz-user-settings-personal]

	Mmm, the field is removed - less to worry about by the user!

Lately, my focus have been more and more on the usability part and presenting new clients for the User Settings module have never been my favourite thing to do.

Did you know, that at this very moment, a default TYPO3 installation got 30 different fields in the User Settings module? 30 fields! How do you tell your user “not to care” about them, without them saying “Then, why is it there in the first place?”

**Using setup.override**
If you are aware of the TypoScript property “override” (which you should, it’s a Opens external link in new windowgreat feature) you know that you can set a value for a field, without the user being able to edit it. It will make the field greyed-out, but still visible to the user. Not cool!

Why should the user have a field, when it can’t be changed? Take this as an example

	setup.override.emailMeAtLogin = 1

This will give your user a greyed-out field in the User Settings. Can you imagine a call from a client asking why the field can’t be changed?

**Let’s remove it, but still give it a value**

Sometime it’s fun to dive into the core and look at code (and comments!). Try open the index.php file in sysext/setup/mod and go to line 313 and read the comment

	311 // Getting the 'override' values as set might be set in User TSconfig
	312 $this->overrideConf = $GLOBALS['BE_USER']->getTSConfigProp('setup.override');
	313 // Getting the disabled fields might be set in User TSconfig (eg setup.fields.password.disabled=1) 
	314 $this->tsFieldConf = $GLOBALS['BE_USER']->getTSConfigProp('setup.fields');

After I read that comment, I went through the TSconfig reference, and I haven’t been able to find that property (.disabled = 1) documented anywhere! But since we found, let’s try and use it!

Go and add the following two lines to the TSconfig for a backend user or usergroup

	setup.fields.emailMeAtLogin.disabled = 1
	setup.override.emailMeAtLogin = 1

The “Email me when i login” field is now removed, but you will still receive a e-mail when logged in!

This was a example. What is important to remember is, that the same setting (setup.fields.[fieldname].disabled & setup.override.[fieldname]) can be used for every single field in the User Setting module. Imagine removing fields like “Recursive Delete” and “File upload directly in Doc-module”, and still setting the value. And if in doubt what the name of the fields are, use the "Configuration" module and browse through the "User Settings" array.

I don’t know about you, but I think this is a great example of how flexible you can configure TYPO3 and give your users a great user experience!


