---
layout: post
title: FLUIDTEMPLATE selector and backend_layout
feature-img: "img/fluid-layout-new-record.png"
---

I present to you EXT:fluidlayout! Use your FLUIDTEMPLATES with a nice selector and give your user a nice backend to work with! [Download it here and get started!](http://typo3.org/extensions/repository/view/fluidlayout)

[fluid-layout-typoscript-checkboxes]: /img/fluid-layout-typoscript-checkboxes.png "Create a TypoScript template, and remember to "check" these boxes"
[fluid-layout-static-templates]: /img/fluid-layout-static-templates.png "Add these three static templates"
[fluid-layout-new-record]: /img/fluid-layout-new-record.png "OMG! A new record type!"
[fluid-layout-tce-form]: /img/fluid-layout-tce-form.png "Fields known from the FLUIDTEMPLATE TypoScript setup + backend layout selector"
[fluid-layout-template-selector]: /img/fluid-layout-template-selector.png "Select your FLUIDTEMPLATE and the backend layout will automatically be set"
[fluid-layout-page-module]: /img/fluid-layout-page-module.png "Your "Page" module looks like your frontend!"

![Create a TypoScript template, and remember to "check" these boxes][fluid-layout-typoscript-checkboxes]

	Create a TypoScript template, and remember to "check" these boxes

![Add these three static templates][fluid-layout-static-templates]

	Add these three static templates

![OMG! A new record type!][fluid-layout-new-record]

	OMG! A new record type!

![Fields known from the FLUIDTEMPLATE TypoScript setup + backend layout selector][fluid-layout-tce-form]

	Fields known from the FLUIDTEMPLATE TypoScript setup + backend layout selector

![Select your FLUIDTEMPLATE and the backend layout will automatically be set][fluid-layout-template-selector]

	Select your FLUIDTEMPLATE and the backend layout will automatically be set

![Your "Page" module looks like your frontend!][fluid-layout-page-module]

	Your "Page" module looks like your frontend!

Did you know about the [new cObject (since 4.5) called FLUIDTEMPLATE?](http://typo3.org/documentation/article/the-fluidtemplate-cobject) (Credits to **Rens Admiraal** for this article!)

If not, I will suggest you to read through that article to get an understanding of FLUIDTEMPLATE.

And did you know about [The Grid View a.k.a. Backend Layout](https://typo3.org/news/article/typo3-45-lts-the-grid-view-a-new-concept-for-a-backend-that-matches-your-layout/), from TYPO3 4.5 LTS?

If not, you might look at that article as well! (good stuff for you to read! Very nice!)

Well, now you should be ready to get the meaning of this post! To keep it simple, it's a mixup between **backend_layout** and the cObject([eh, cObject?](http://wiki.typo3.org/TSref/cObject)) **FLUIDTEMPLATE**. But I (my personal opinion!) think this is also going to be the easiest way, for you, as a new TYPO3 user, to get your homepage "out there" through TYPO3! And still have a good user experience!

And if you are a more experienced TYPO3 user (with a love for TypoScript) there is also a lot of fun for you guys! I know you are reading this! :)

## Okay, how do I get started?

I expect you to have page tree and a HTML file (uploaded somewhere in your TYPO3 installation) with your final markup. This means everything between _<body>_ and _</body>_. FLUIDTEMPLATE (or, actually the PAGE object) will automatically add the _<head></head>_ part

	To those of you thinking: "What about layouts and partials" this will not be covered here! But feel free, you can still use it! :)

Create a new record through the List module and select the record type **Template** just below the **FLUIDTEMPLATE and backend_layout** header.

Enter a (describing..!) name of this template in the field **Template name**, this is the name which will be visible in **Page properties**, when you (or your users) selects a template.

Browse your file structure to find your HTML template file.

This is actually the only two things required in order to get your HTML structure(!) outputted.

## Adding a nice backend layout to the template

I don't like to reinvent the wheel, so I will point you to the great article mentioned above (The Grid View a.k.a. Backend Layout) on the topic of **creating a backend layout**.


Add the created backend layout to your **FLUIDTEMPLATE records** from the selector box (see image 4 to the right)

## Using your FLUIDTEMPLATE


Now, go to the **List** module and click on your root page of your page tree. Create a new **Template**, found below the **System records** headline. Type a name (in this article I will use the name **Main template**) in the required field and go to the tab **Options**. Make sure the fields **Constants**, **Setup** and **Rootlevel** is checked (see image on the right). Go to the tab named **Includes** and include the three items as shown in the picture to the right. Click the **Save & close** button in the top.

Now to the root page of your page tree and select **Page Properties**, go to the tab Appearance and select your newly created template.

Click **Save**, go and **clear the cache** and browse your homepage. If all went well, you should now be able to see your HTML structure (no CSS included yet, be right there!) outputted.

## How do I add my CSS & JavaScript?

Due to lack of stdWrap ([eh, stdWrap?](http://dmitry-dulepov.com/article/typo3-stdwrap-explained-part-1.html)) you will have to add your CSS files through TypoScript in the **Template** named **Main template**. Edit the **Main template** record, by click the yellow pencil (or right-click the icon to the left of **Main template** and click **Edit**).

Find the **Setup** field in the tab **General** and write the following line

	page.includeCSS.file1 = fileadmin/path/to/your/file.css

you can add many more files by changing "file1" to "file2" etc. The same goes for javascript

	page.includeJS.file1 = fileadmin/papth/to/your/file.js

You might wonder how the *page* part can do this "magic"? Inside the two static files we included earlier, the variable **page** was defined as a **PAGE** object, and this object contains a lot of great functionality!

If you are interested in reading more about the possibilities in the **PAGE** object, go on and [read the TYPO3 Wiki on the subject.](http://wiki.typo3.org/TSref/PAGE)

## So, what about the content my good man?

As a little "service" for you to get started, the extension already included content objects for three different columns. The three columns covered **Left column**, **Normal column** & **Right column**.

If you are familiar with the **TypoScript Object Browser** you can find the definition of these [CONTENT objects](http://wiki.typo3.org/TSref/CONTENT) by expanding the object tree. The path is

	page.10.variables

In order for you to use these predefined content objects simply place on the following three lines of "Fluid HTML" (Fluid HTML tag, which takes care of formatting, in this case) in your template, where you want the content to be shown.

For **Left column** content use:

	<f:format.html>{contentLeft}</f:format.html>

For **Normal column** content use:

	<f:format.html>{contentNormal}</f:format.html>

For **Right column** content use

	<f:format.html>{contentRight}</f:format.html>

