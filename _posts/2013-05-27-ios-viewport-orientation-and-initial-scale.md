---
layout: post
title: "iOS Viewport Orientation and initial-scale"
description: "When turning an iOS device from portrait to landscape on a responsive web page, the page and text zooms in instead of staying the same size and reflowing. initial-scale to the rescue!"
---

##TL;DR

This might be what you're looking for:

{% highlight html %}
<meta name="viewport" content="width=device-width, initial-scale=1.0">
{% endhighlight %}

Particularly, the `initial-scale=1.0` part. Slap that in your `<head>` tag and you should be set. Without that, in landscape orientation your responsive page might look more like it's zoomed in instead of actually reflowing to the extra width.

##Long Version

In my recent testing with responsive webpages, I came across something that wasn't exactly a deal breaker in any of my cases yet, but it just plain bothered me. When I would view the webpage on an iPhone or iPod Touch and change the orientation from portrait to landscape, everything (logo, header, text) seemed to almost double in size so that it took up the width of the viewport the same as it did in portrait orientation. The text had the same wrapping, the logo was in the same relative place, and it got so big that the only thing visible at the top of the page was the logo.

<figure>
<img src="/assets/images/initscl_none.png" alt="both orientations without initial-scale applied">
<figcaption>Showing portrait and landscape orientations as they initially appear. Landscape is zoomed in to flow the same as portrait.</figcaption>
</figure>

I knew that it was possible to do it differently because I had seen [microsoft.com](http://microsoft.com) do it successsfully. When viewing their homepage in landscape orientation, the text and elements flow differently than they do in portrait. I had googled around about this but many answers were talking about the text-size-adjust CSS solution to just the font size problem. So I cracked open developer tools to do some code comparison, and almost immediately saw something different in the `<meta name="viewport">` tag.

Mine just had:
{% highlight html %}
<meta name="viewport" content="width=device-width">
{% endhighlight %}

Theirs had an extra value in the `content` attribute:

{% highlight html %}
<meta name="viewport" content="width=device-width, initial-scale=1.0">
{% endhighlight %}

Here's how it looks after adding that value to my website:

<figure>
<img src="/assets/images/initscl.png" alt="both orientations with initial-scale applied">
<figcaption>Showing portrait and landscape orientations after adding initial-scale=1.0 to the viewport meta tag. Landscape flows different and allows more to be seen before scrolling.</figcaption>
</figure>

##Extra Credit

Is your font-size still looking strange in landscape? Along with initial-scale, you might also need to make use of the text-size-adjust CSS solution like this:

{% highlight css %}
html {
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
}
{% endhighlight %}

If you're using normalize.css, you're already covered; they've got it right towards the top.