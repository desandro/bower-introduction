
Intro: making websites today

Intro to Bower

Consuming packages



Building Packery, Masonry & Isotope

+ updating getSize, easily update

---

Package management is a real problem.

Bower takes care of package management.

Bower is special because it is unopinionated. You can consume packages however you want.

Front-end development with dependencies promotes encapsulation. 

---

### Package management is a real problem.

front end dev today. collecting a lot of shit

### Bower takes care of package management.

+ intro to using Bower

+ Used by Google (Yeoman, Angular), Twitter (Flight), jQuery

### Bower is special because it is unopinionated.

+ Others in the market - Component, npm, Volo, Jam, Ender, Browserify, git submodules

+ It doesn't even have to be a package, can just be http

+ You can consume packages however you want.

+ Component, you have to buy-in to CommonJS

+ Grunt, RequireJS, or straight <link>

+ Reason why I chose it. I didn't want to prescribe a methodology on to my users.

### Example: Masonry, Isotope & Packery

+ mono-file-ism

+ each dependency has its own repo, its own changelog, its own issue tracker

+ I have a automated way for updating projects down-tree

    bower update
    // deploy

    Masonry, Isotope, Packery, imagesLoaded, Draggabilly

+ Docs for th

+ I can still generate packaged files for quick & easy <link>ing -- like in CodePen, or jsFiddle.

+ Front-end development with dependencies promotes encapsulation.
