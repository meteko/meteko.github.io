---
layout: post
title: Create a download action with Extbase
feature-img: "img/fdf-fotodatabase-single-view.png"
---

Do you want to make some statistic etc. before letting a user download a file. You can use a standard Extbase action to fullfill your needs :)

[fdf-fotodatabase-single-view]: /img/fdf-fotodatabase-single-view.png "Single view in FDFs Mediadatabase"

![Single view in FDFs Mediadatabase][fdf-fotodatabase-single-view]

	Single view in FDFs Mediadatabase

Lately I've been working on a mediadatabase for the danish [scout-like organization Frivilligt Drenge- Og Pige-Forbund, FDF](http://www.fdf.dk). 

As a natural part of a mediadatabase, a visitor should be able to download the media file. But, we would also like to make some statistic on each download. So, instead of creating links directly to the original media file, I created a downloadAction inside my mediaController.

But, normally actions shows the corresponding HTML template.. So I've had to "manipulate" the response object Extbase gives me. 

{% highlight php %}
<?php

class ImageController extends ActionController {

	public function downloadAction(Tx_Mediadatabase_Domain_Model_Media $media) {
		/**
		 Do something "fun" here.. Statistic, counting, notify, etc.
		 **/
		$this->response->setHeader('Cache-control', 'public', TRUE);
		$this->response->setHeader('Content-Description', 'File transfer', TRUE);
		$this->response->setHeader('Content-Disposition', 'attachment; filename=FILENAME.jpg', TRUE);
		// ATTENTION: I've hardcoded the Content-Type, you might have to change this!
		$this->response->setHeader('Content-Type', 'image/jpeg', TRUE);
		$this->response->setHeader('Content-Transfer-Encoding', 'binary', TRUE);
		// As the very last thing, I send the headers to the visitor, before Extbase comes to the part, where it renders a HTML template
		$this->response->sendHeaders();
		// $this->media is my domain model, add you own file path here :-) 
		@readfile($this->media->getOriginalResource());
		exit();
	}
}

{% endhighlight %}

Another fun part in this project, was using the [FLUIDTEMPLATE as template engine](http://typo3.org/documentation/article/the-fluidtemplate-cobject). As the mediadatabase was the only content in this pagetree (no text, text with image etc. element) I was able to take full advantage of Fluid with Layouts and Partials beside the normal templates for each actions.

