# The problem

We are here today because we make websites.

I want you consider your own process -- when you roll up your sleaves, sit down, and start the act of making a website. Your first step looks like creating a new folder.

And then you start to add stuff. Scripts, libraries, templates, resources, assets, utilities, frameworks.

+ Foundation
+ Bootstrap
+ normalize.css
+ fitvid.js
+ video.js
+ Modernizr
+ jQuery
+ d3
+ underscore / lo-dash
+ Backbone
+ Angular JS
+ Effeckt.css
+ HTML Boilerplate
+ Masonry
+ RequireJS
+ Font Awesome
+ Compass

jQuery plugins

+ jQuery UI
+ Easing
+ form
+ gallery
+ Lightbox
+ modal

Own scripts

+ default styles
+ helper JS

Utilizing these resources is great because they have taken care of all the heavy lifting. They are reliable, well-documented, and have tremendous usage. We get to take advantage of all that.

Consider how do you get this stuff?

+ Download
+ Clone git repo
+ already saved locally

Where do you put it?

+ lib/
+ lib/vendor/
+ assets/js/vendor, assets/css/vendor, etc.

How do you keep track of it?

+ Store all assets on server
+ If in git, commit it to repo
+ If in git, use submodules

---

Employing various resources has tremendous advantages, but it comes with this meta problem of dealing with all the stuff.

Whenever you have a lot of stuff, you have a lot of hassle. If your desk is too messy, you won't have enough space to do your work. You will be slowed down in your creative process, trying to find where the heck you put that thing you just had in your hand. Your messy desk will hamper collaboration with others, as you have to explain just how to make sense of the work space to your colleagues. What good is a desk if you spend just as much time cleaning it up, as you do actually working on it.

For us web developers, this is the problem of package management -- the problem of dealing with all the stuff that put in to make a website.

This is a real problem in front-end development. We have a lot of stuff, and we need a way to manage of all it. Trying to manage it yourself might work. But you eventually hit a problem of scale:

- when you add a lot of resources
- when you collaborate with a team
- when you revisit the project in 6 months

Front-end resource management is a real problem. Today, I am going to talk about the solution.

Bower

---

Here's what we have in store for the next 25 minutes.

The Problem: Front-end development
The Solution: (Hint: It's Bower)
The Reason: Why Bower?
The Results: Storytime

