---
layout: post
title: "CSS Grid Confession"
description: ""
---
I may have done the apparently [unforgivable](http://hugogiraudel.com/2013/03/04/css-grids/) as a front-end developer. I made my own CSS grid... kind of. I'll explain.

I've been working on some responsive web design stuff for work; doing some presentations on it, retrofitting some pages with it, and looking at what it might mean for future projects. I've been playing with and reading up on RWD on my own for a while now. During this time I've obviously come across many frameworks out there that have CSS grid systems in place for dealing a scalable layout solution for responsive webpages.

##Frameworks

One thing that is becoming quite common with these frameworks' grids is that they use some flavor of CSS preprocessor. I know, many of the popular ones also have versions that don't contain preprocessor code. But another common thing with frameworks is that they've made some design decisions already. So, two things:

<ol>
	<li>The team I work in is not ready for a CSS Preprocessor</li>
	<li>We don't need a framework making out-of-the-box design decisions; we definitely don't need to spend time learning a framework's ins and outs just to undo or override those decisions.</li>
</ol>

Number 1 maybe needs some explaining here. I *don't* mean "not ready" as in not smart enough. I mean "not ready" as in we are a large-ish front-end team that doesn't have the tools in place currently to make using a preprocessor worth the time to learn how. Sass needs ruby, Less needs node.js., or they need GUI tools that compile them (like Codekit for Mac or Mixture for Windows). We would all need to learn the language, purchase licenses for tools, or set up submit processes for compiling. This just won't work for us at the moment. Perhaps as our processes and work responsibilities mature, but not right now.

##The Grid

So, I kind of lied. I didn't exactly make my own grid. I *heavily* borrowed to build it.

Last year, I saw Chris Coyier's Don't Overthink It Grids post and screencast over on [CSS Tricks](http://css-tricks.com/video-screencasts/115-dont-overthink-it-grids/). And just recetly I came across Harry Roberts' [CSSWizardry Grids](http://csswizardry.com/csswizardry-grids/). Harry's grids use Sass, but an understanding of how grids can work from Chris' write up and demo, and Harry's well-commented CSS made it super easy for me to dissect what was all going on and why. Plus, I really liked how Harry was using [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) for naming things in his. 

So, late one night this week, I made a [mashup of these two approaches](http://codepen.io/keithwyland/full/FfqGo). Like I said, I *heavily* borrowed here because:

<ul>
	<li>I liked Harry's BEM and fraction column naming</li>
	<li>I didn't like the inline-block comments needed in Harry's, so I used float from Chris'. (though I end up having to do inline-block for centering grids. grr.)</li>
	<li>I didn't want to totally reinvent the wheel. :)</li>
</ul>

Here, I'll embed the codepen of it.

<pre class="codepen" data-height="400" data-type="result" data-href="FfqGo" data-user="keithwyland" data-safe="true"><code></code><a href="http://codepen.io/keithwyland/pen/FfqGo">Check out this Pen!</a></pre>
<script async src="http://codepen.io/assets/embed/ei.js"></script>


##Conclusion

So that's my CSS grid confession. Honestly, though, it's not intended for other's use. It's for me, and my teammates to test with and maybe build from. Plus, I just wanted to document what I did here on this 'ol blog. Done, check.