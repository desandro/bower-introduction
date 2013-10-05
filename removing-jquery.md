# Removing jQuery from Masonry & Isotope

About a year ago I started considering what it would take to remove jQuery as a dependency from Masonry and Isotope. IE7 and IE6 are long dead and forgotten. If you are targeting for IE8 and better, you can actually do a lot with out forking your code like crazy to handle the older browser edge cases.

But there are a couple things that I needed to replace jQuery with something else. 

+ measuring elements
+ adding event listeners
+ triggering on document ready

Before I started writing code, it was clear that Masonry and Isotope would both be re-using a lot of the same underlying components or dependencies. This would be difficult.

I knew it would be difficult because I was already failing to manage just one component.

## imagesLoaded

Masonry and Isotope work by measuring the size of elements. An unloaded image can cause a problem, as it changes the size of an element after the image loads. Basically you need all images to be loaded before you trigger the layout.

In order to resolve this problem, I added another bit of code to Masonry and Isotope, called imagesLoaded.

So I brought in this little script, called imagesLoaded. imagesLoaded solves this problem! Great!

So what did I do? I baked in imagesLoaded into the two different projects `jquery.masonry.js` and `jquery.isotope.js`. 

     _____    _____    __
    |     |  |     |  |iL|
    | M __|  |  I__|  |__|
    |__|iL|  |__|iL|

I included imagesLoaded in my other projects because, hey, that's the way it was done a couple years ago. Users come to expect, you go to a page, you see big 'ol button. You click download, and then you have all the necessary parts you need. It's all wrapped up for you nice and neat.

At this point, a couple years ago, I dust off my hands, pat myself on the back, and walk away confidently thinking I have solved the problem.

Of course, there is a problem, it's clear enough looking at this picture. imagesLoaded is duplicated in three places.

I disobeyed one of the most fundamental rules of programming: **DRY**

_Don't_
_Repeat_
_Yourself_

We all know this rule when it comes to our code. We know it makes for code that performs better, and is easier to read. The same rule applies for our projects.

This means any time I want to update imagesLoaded, I have to update it in three different places.

It sounds easy enough, but I have a hard time doing this tedious task. Here are the issues on GitHub

https://github.com/desandro/isotope/issues/351
https://github.com/desandro/isotope/issues/364
https://github.com/desandro/masonry/pull/254
https://github.com/desandro/masonry/issues/230

In the words of Marty Huggins _It's a mess!_

## Adopting Bower

Adopting Bower allowed me to offload taking care of one thing that is used in multiple things. Instead of worrying about copying code over, I can rely on keeping separate functionality separate. 

For each of these purposes, I built a small library to handle it.

+ measuring elements - getSize, 180 LOC
+ adding event listeners - eventie, 74 LOC
+ triggering on document ready - docReady, 69 LOC

I am able to do so, by leveraging my favorite feature of Bower: dependency management.
That's because Bower's best feature is _dependency management_.
