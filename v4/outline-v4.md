# outline v4

## The problem

**front-end package management**

## The solution

**Bower**

## The reason

**unopinionated**

## The results

Been using it, it's amazing

### surface level

#### fix imagesLoaded debacle

+ imagesLoaded duplicated in three places, `jquery.isotope.js`, `jquery.masonry.js`, `jquery.imagesloaded.js`.
+ Disobeyed a cardnal rule of programming: DRY - Don't repeat yourself
+ Led to problems, couldn't easily manage it

---

Led me break apart other pieces of code that were duplicated, 

+ jquery-bridget
+ get-size
+ get-style-property
+ doc-ready
+ eventie
+ event

+ Each package has its own repository, with its own issue tracker, and its own changelog

Like for example...

#### masonry#417

+ problem identified in Masonry, but actually with getSize
+ fix implemented in getSize, cut new version
+ update masonry
    bower update
    deploy
+ not only do I fix this problem in Masonry, but I fix it in all the packages that depend on getSize
  - Packery
  - Isotope
  - Draggabilly

### Encapsulation

+ Literal naive definition: making capsules - Breaking down something large into smaller pieces, easier to swallow

+ Like DRY, it's a principal quality of good programming. One that we can take

### personal level

+ focus just at the task at hand
+ no longer have to keep the whole mental model in my head