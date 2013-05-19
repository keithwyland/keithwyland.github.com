---
layout: post
title: "jQuery Object to Cookie and Back"
description: "I needed to store a session cookie for use by other pages, and I wanted to use an object with key : value pairs to initially store all of the data, and then read it back to an object."
---

I was working on a little web app that has multiple screens that show or hide on one web page, and javascript very temporarily stores small amounts of data entered in form fields by the user. Kind of like a quiz with results at the end.

I needed to store a session cookie for use by other pages, and I wanted to use an object with key : value pairs to initially store all of the data. The cookie needed to have 'multiple values', so basically a long string of parameters similar to URL parameters. That part was fairly easy after utilizing the [jquery-cookie](https://github.com/carhartl/jquery-cookie) plugin and jQuery's .param() function.

{% highlight javascript %}
var obj = {
	foo: "bar",
	stuff: "here",
	test: "blah"
};
$.cookie( 'NameOfCookie', $.param(obj) );
{% endhighlight %}

That worked fine. 

Now, when the user got to a certain point in the little app, I didn't want a page refresh to bring them back to the beginning of the app. I wanted javascript to check for the cookie, and if it existed, use the values from the cookie to repopulate data on the screens. Thing is, I needed to get the data from the cookie back into the object using the exact same key names to assign values to. I know there are other plugins for 'unserializing' strings of data, but I was already using a few other jQuery plugins for the project and just wanted to keep this piece to a few lines of my own code.

If the cookie shown above is stored, then its value looks like this:

`foo=bar&stuff=here&test=blah`

So, first I needed to check for the cookie and read it into a variable.

{% highlight javascript %}
if ($.cookie('NameOfCookie')) {
	var readCookie = $.cookie('NameOfCookie');
}
{% endhighlight %}

Then, looking at the cookie's value above, I needed to split it up a couple times. First, each key value pair is separated by an &amp;, so:

{% highlight javascript %}
readCookie = readCookie.split('&');
//readCookie == ['foo=bar', 'stuff=here', 'test=blah']
{% endhighlight %}

Now readCookie is an array. Next, each key and value are separated by an =. So I looped through the array index and split each by = then used the array index to set the appropriate object key to the cookie's value:

{% highlight javascript %}
for (i=0; i<readCookie.length; i++) {
	readCookie[i] = readCookie[i].split('=');
	//readCookie[1] == ['foo', 'bar'], readCookie[1][0] == 'foo', etc.
	obj[readCookie[i][0]] = readCookie[i][1];
}
{% endhighlight %}

There might be a better way of doing it, but this worked great for my little project! Plus, I didn't find anywhere else that had given examples without using another plugin. Hope it helps you, too!