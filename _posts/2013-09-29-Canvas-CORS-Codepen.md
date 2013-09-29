---
layout: post
description: drawImage. toDataURL. FAIL. And then...
title: Canvas. CORS. Codepen.
---

I'm going to be working on a project that might require some fancy combining of images to make one image on-the-fly, as well as some simple animation and other "flashy" stuff. Finally, a real perfect reason to learn HTML5 canvas!

I set aside some time to hack away at it with some tutorials and decided to use [Codepen](http://codepen.io) as my playground. I'm assuming the project will involve receiving some image files for the end web product, so I went with that scenario. First, I grabbed some simple icon images from [Raphael](http://raphaeljs.com/icons/), used [SVG-edit](http://svg-edit.googlecode.com/svn/branches/2.6/editor/svg-editor.html) to export them as PNGs, and uploaded them to [imgur](http://imgur.com/) to easily reference on Codepen.

## The ol' college try
Then, I got crackin' on Codepen with this html and javascript:

{% highlight html %}
<canvas id="myCvs" width="400" height="400"></canvas>
{% endhighlight %}

{% highlight js %}
var img = new Image,
    src = "http://imgur.com/url/here",
    cvs = document.getElementById('myCvs'),
    ctx = cvs.getContext('2d');
    
img.onload = function() {
  ctx.drawImage( img, 100, 100 );
}

img.src = src;
{% endhighlight %}

Which worked great. The canvas showed the icon. Awesome! I'm rollin'! And then I tried adding this:

{% highlight html %}
<img id="myImg" src="" alt="image from canvas" />
{% endhighlight %}

{% highlight js %}
img.onload = function() {
  ctx.drawImage( img, 100, 100 );
  var imgTag = document.getElementById('myImg');
  var dataURL = cvs.toDataURL();
  imgTag.src = dataURL;
}
{% endhighlight %}

and got this lovely in the console:
    Uncaught SecurityError: An attempt was made to break through the security policy of the user agent.
    
FAIL. Sounds serious, eh?

## Tainted
Apparently, when you pull in a resource from an external domain, or cross-domain, and use it on the canvas, the canvas becomes "tainted" and will no longer allow you to pull data out of it. The good news for me is that I'm pretty sure for my project the images will be local on the same server that the web page lives on.

But, I couldn't leave it there. I wanted to figure out how to get around the tainted canvas if I ever did have a real use case for doing so. I found [this short article on MDN](https://developer.mozilla.org/en-US/docs/HTML/CORS_Enabled_Image) that described exactly the problem I was having and offered a solution. The domain that serves the image files must also serve the proper CORS headers. Basically, the CORS header has to specify that the domain that is using the image is OK to use it.

## Try, try again
Codepen PRO has asset hosting, but I don't have Codepen PRO (yet). So I tweeted them to find out if their assets serve the proper headers. They do! And they forked the pen I sent them, and I forked it back to add in the crossOrigin javascript bits from that MDN article. Success! Embedded below is the final codepen testing that this actually works. Enjoy!

<p data-height="400" data-theme-id="2" data-slug-hash="umova" data-user="keithwyland" data-default-tab="result" class='codepen'>See the Pen <a href='http://codepen.io/keithwyland/pen/umova'>Canvas toDataURL with CrossOrigin</a> by Keith Wyland (<a href='http://codepen.io/keithwyland'>@keithwyland</a>) on <a href='http://codepen.io'>CodePen</a></p>
<script async src="http://codepen.io/assets/embed/ei.js"></script>




