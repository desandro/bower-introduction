# Results

I am an advocate of Bower not just becuase I work for Twitter. But because I needed Bower for my own projects.

Bower has been out for a year. I've been using it for just as long. It's made my job as a developer a lot better. Here's why.

## Escaping mono-file-ism

The first initial benefit of using Bower was that I no longer was constrained to develop in a single file. Developing across multiple files is of course nothing new to programming. But for front-end developers, I think have the ideal of the one file ingrained in our heads. We all know that we should be doing our darndest to keep HTTP requests to a minimum.

    <!doctype html>
    <html>
    <head>
      <meta charset="utf-8">
      <title>Great site</title>
      <link rel="stylesheet" href="styles.css">
    </head>
    <body>
      <h1>Great site</h1>
      <script src="scripts.js"></script>
    </body>
    </html>

Likewise, when we create resources, the most convienent to use are ones that boil down to one file (or at least one .css file, and one .js file).

> jquery.isotope.js - 1400 LOC

Because Bower can consume packages with multiple files, I no longer had to hold myself to this ideal.

The benefit of breaking out one file is more than just nicer organization. Sectioning off my code changed the way I thought about its structure. In programming, this is the concept of encapsulation.

For example, Packery is a layout library that uses a bin-packing algorithm. There's a lot that's going on. It's hard to explain all at once, but it's easy if I work backwards.

    Packery - packery.js
      - uses bin-packing logic to position a group of item elements
      - uses Packer, Item, Rect
    Item - item.js  - uses Rect
      - positions/transitions a single element
    Packer - packer.js  - uses Rect
      - bin-packing algorithm
    Rect - rect.js
      - A mathmetical rectangle

Packery is a layout library that uses a bin-packing algorithm to position item elements. That all happens in packery.js. Looking at that previous sentence, I see there's two separate concepts, the bin-packing algorithm, and an item element. Each concept gets its own file and its own class. These classes are distinct in that the Rect has no concept of the Packer, and likewise, the Packer has no concept of an Item, or of Packery. Each class is then purpose built.

It helps keep the code clean. More importantly, it helps my mind make sense of what's going on. I don't need to keep the mental model of this entire library in my head. By sectioning it out, I only have to worry about the one class I am working with.

I imagine most of the developers in this room feel like they're observing a bumbling babe take his first steps. Here I am taking about separating my code into different files; building separate, distinct classes; and thinking about the structure of my project. But this was a big deal for me.

Front-end development is still a young profession. 
