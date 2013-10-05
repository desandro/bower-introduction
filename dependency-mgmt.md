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


## npm

A large part of the success of Node JS as a platform is its package management, provided by npm.

So let's say you want to do some fun stuff with Twitter, you can do so! Because someone else has already built a Twitter client

https://github.com/AvianFlu/ntwitter

That person was able to build the twitter client, because someone else already built an Ouath client

https://github.com/ciaranj/node-oauth

A package that gets built upon another package gets to take advantage of the work done by a previous author. With each package that gets registered, the benefits start piling up recursively.

<!-- Ideally, any novice programmer can build an application with serious complexity, by utilizing packages that are d -->

Oh man, don't you want that? Right now our packages are fractured. Some are wrapped up in monolithic libraries, and some have CSS, and some are JS, and some need to be downloaded, and some need to be cloned and built.

---

Yes, 