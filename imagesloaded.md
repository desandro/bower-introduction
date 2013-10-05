
I have two projects, Masonry and Isotope. You might have seen them. Masony is a layout library that does this. And Isotope is the layout library that does Masonry and does filtering and sorting, so you can do this.

     _____    _____
    |     |  |     |
    |  M  |  |  I  |
    |_____|  |_____|

But there's a problem of using layouts. These libraries work by measuring the size of elements. An unloaded image can cause a problem, as it changes the size of an element after the image loads. Basically you need all images to be loaded before you trigger the layout.


## imagesLoaded

So I brought in this little script, called imagesLoaded.

imagesLoaded solves this problem!

Great!

So what did I do? I baked in imagesLoaded into the two different projects `jquery.masonry.js` and `jquery.isotope.js`.

     _____    _____    __
    |     |  |     |  |iL|
    | M __|  |  I__|  |__|
    |__|iL|  |__|iL|


At this point, a couple years ago, I dust off my hands, pat myself on the back, and walk away confidently thinking I have solved the problem.

Of course, there is a problem, it's clear enough looking at this picture. imagesLoaded is duplicated in three places.

I disobeyed one of the most fundamental rules of programming DRY

Don't
Repeat
Yourself

We all know this rule when it comes to our code. We know it makes for code that performs better, and is easier to read. The same rule applies for our projects.

This means any time I want to update imagesLoaded, I have to update it in three different places.

It sounds easy enough, but I have a hard time doing this tedious task. Here are the issues on GitHub

https://github.com/desandro/isotope/issues/351
https://github.com/desandro/isotope/issues/364
https://github.com/desandro/masonry/pull/254
https://github.com/desandro/masonry/issues/230

We shouldn't be commiting projects inside of one other.

I included imagesLoaded in my other projects because, hey, that's the way it was done a couple years ago. Users come to expect, you go to a page, you see big 'ol button. You click download, and then you have all the necessary parts you need. It's all wrapped up for you nice and neat.

This is the old distribution model.

---

Once 

## Other components

EventEmitter
