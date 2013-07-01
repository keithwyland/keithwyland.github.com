---
published: true
layout: post
title: Getting Comfortable
description: My Jekyll Implementation Story
---

I like to think I'm a fairly quick learner when it comes to the basics of things or concepts. But sometimes I need to chew on the details a while before I actually digest them.

I've never used Jekyll before this blog, I'm only a novice at command line, and I needed an easy way to deploy this thing as an actual website. I had some chewing to do.

## Command Line ##
First, I needed to be a little more comfortable with command line. Up until now I really would only copy and paste commands and watch the black magic happen. This learning actually came before I even thought of using Jekyll for this site. I got a [Treehouse](http://referrals.trhou.se/keithwyland "Treehouse website") subscription for a great deal through [AppSumo](http://appsumo.com "AppSumo website"). One of Treehouse's latest courses is called Console Foundations. So I'm a *little* bit more comfortable in Terminal now. I no longer have fears of accidentally sending a metaphorical missle at my hard drive.

## Jekyll ##
Next, [Jekyll](https://github.com/mojombo/jekyll "Jekyll github repository"). The install instructions assume some experience with Ruby and gems. First timer! I ran into some errors that were mentioned in a couple of the install instructions and follwed the links. It took a little time but ended up being no too bad. There is hope for me, yet!

## Deployment ##
When I got this stuff working locally, I was looking into where to host it. I have some web hosting space already, but I was looking for something easier. On the [Deployment](https://github.com/mojombo/jekyll/wiki/Deployment "Jekyll deployment options") page I came across Amazon S3 and was quite intrigued by that at first. I had no idea you could actually host a website and point a domain directly at S3. Nor did I know that S3 had a free level of their hosting plans. I got through most of the set up, and even installed [jekyll-s3](https://github.com/laurilehmijoki/jekyll-s3 "jekyll-s3 github repo"). But somewhere along the way I also learned I could pretty much do the same thing with github. 

Hosting a Jekyll site on GitHub is crazy easy. Every GitHub page is actually [powered by Jekyll already](https://help.github.com/articles/using-jekyll-with-pages "Using Jekyll with Github Pages"). I decided on this option because I wouldn't have to upload an entire compiled site everytime I made a change. Since Jekyll is running on GitHub, it takes care of all the compiling for me. So I can just commit a new markdown post file and boom, that's a new post live on my site. [Pointing my domain](https://help.github.com/articles/setting-up-a-custom-domain-with-pages "Setting Up a Custom Domain with Github Pages") at my github page was easy and started working instantly. I mean, within seconds, no joke.

## Extras ##
Along the way I got sidetracked and went down a couple rabbit trails. At one point, for some reason (I don't remember why now) I was convinced I needed a different version of Ruby on my machine. Probably because of some error I was getting. I started getting into rvm and even installed it. But then the `jekyll` command wasn't working in Terminal anymore. So I ditched that, and the `jekyll` command still didn't work. Restarted Terminal and everything was fine. So maybe the installation of rvm would have been fine, too, if I just had restarted Terminal, but I'll leave that adventure for another day. 

Also, when it came to deploying to Github I found jekyllbootstrap and decided it was the easiest way to install on my Github username repo. I was initially having issues setting the repo url and all that jazz. But I ended up ditching jekyllbootstrap, too. Too much junk I didn't need yet. Plus, I wanted to know what was in the HTML. I did keep the .gitignore file that came with it though, so my commits only contain the stuff Github needs to compile the site.

Another learning I've taken from all this is `rake`. As I was exploring Jekyll, I kept coming across people using rake commands to automate this and that. I ended up grabbing the Rakefile from jekyllbootstrap in order to do a `rake post title="Title"` command for easily creating a new post markdown file. For some reason the other simpler Rakefiles I was finding on other pages were giving me errors in Terminal. I'll probably look more closely at that some other time because the Rakefile I have now again has a bunch of bloat. I even yanked a few lines of code out of it already. Rake is apparently something tied with automating Ruby development... something I am only dipping my pinkie toes into by putting this blog together.

Well, that's my story!
