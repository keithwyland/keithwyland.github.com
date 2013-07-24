---
layout: post
title: "Table Columns and Percentage Widths"
description: "A coworker came across an interesting issue while working with data tables and percentage widths applied to columns."
---

Another member of my web designer team at work came across an interesting issue dealing with data tables. The first column of the table had very short (one- to two-characters long) data needed to be restricted so that the others could expand for larger chunks of data.

{% highlight html %}
<table>
	<tr>
		<td class="col-one">xx</td>
		<td>Longer string of data</td>
		<td>Even longer string of dynamic data</td>
	</tr>
</table>
{% endhighlight %}

Initially, the width being assigned to `col-one` came from a copied template and had a small percentage value to keep it flexible if need be, but still quite small of a column.

{% highlight css %}
.col-one { width: 5%; }
{% endhighlight %}

However, this width was causing the table to appear to be expanding the entire width of it's parent, instead of just accommodating the length of the data inside the table. At first I thought it was strange that just applying any percentage width to only one column would cause a table to expand 100%. But when I dug a little deeper and did some basic testing on [CodePen](http://codepen.io), I learned what was really going on. 

Instead of repeat everything in this post, I'll just embed the pen below. Hope it's useful information for someone! I know I enjoyed learning it!

<p data-height="396" data-theme-id="2" data-slug-hash="plAIt" data-user="keithwyland" data-default-tab="result" class='codepen'>See the Pen <a href='http://codepen.io/keithwyland/pen/plAIt'>Test Case: table column % widths</a> by Keith Wyland (<a href='http://codepen.io/keithwyland'>@keithwyland</a>) on <a href='http://codepen.io'>CodePen</a></p>
<script async src="http://codepen.io/assets/embed/ei.js"></script>

