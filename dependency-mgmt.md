# Dependency Management

Dependency management is basically when you say "Hey, get me X," the manager will get you X and all the other things that X depends on to work.

So for example, if you `bower install bootstrap`...

    bower install bootstrap
    bower bootstrap#*               cached git://github.com/twbs/bootstrap.git#3.0.0
    bower bootstrap#*             validate 3.0.0 against git://github.com/twbs/bootstrap.git#*
    bower jquery#>= 1.9.0           cached git://github.com/components/jquery.git#2.0.3
    bower jquery#>= 1.9.0         validate 2.0.3 against git://github.com/components/jquery.git#>= 1.9.0
    bower bootstrap#~3.0.0         install bootstrap#3.0.0
    bower jquery#>= 1.9.0          install jquery#2.0.3
    
    bootstrap#3.0.0 bower_components/bootstrap
    └── jquery#2.0.3
    
    jquery#2.0.3 bower_components/jquery

Bower installs Bootstrap and jQuery. Because Bootstrap depends on jQuery for its plugins.

For my purposes, I could build Isotope and Masonry, have them depend on the same things

    isotope
    ├── get-size
    ├── eventie
    └── doc-ready

    masonry
    ├── get-size
    ├── eventie
    └── doc-ready

---

Once I started going down this path, of breaking up these libraries into smaller components, it became clear that I could go one step further, and abstract a general layout library class.

    outlayer
    ├── doc-ready
    ├── eventEmitter
    ├── eventie
    ├── get-size
    ├── jquery-bridget
    └── matches-selector
    
    isotope
    └── outlayer
    
    masonry
    └── outlayer
    
    packery
    └── outlayer

When building other libraries, like a revision on imagesLoaded, or Draggabilly, I was able to take advantage of the smaller component libraries.

    draggabilly
    ├── classie
    ├── eventEmitter
    └── eventie
    
    imagesloaded
    ├── eventEmitter
    └── eventie

Componentization and encapsulation is nothing new to programming. Ruby has gems, and Python has eggs, node has npm.




