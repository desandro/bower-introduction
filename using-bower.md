# Using Bower

Bower is a node package.

If you've never installed Node - try it! It's actually pretty easy.

Once you install node, you can install Bower via the command line

## 5 minute intro to using bower

### Installing Bower

install with node

    sudo npm install -g bower

_Watch out Command Line._

> You probably have one of two reactions. For the hard-core devs are thinking "HELL YEAH ABOUT TIME TO SEE SOME COMMAND LINE ACTION." Totally pumped, and the other half is "Oh crap, this is going to be a super neck-beardy." But don't worry, Bower works via the command line, but it's not obnoxious about it. Bear with me, nearly all the commands are super simple.

### Installing packages

Now that we have Bower, we can use it to get stuff.

Let's get jQuery.

    bower install jquery

Bower has installed jQuery v2.0.x.

Now, I still care about IE8, so I want to install jquery v1

    bower install jquery#1.x

That #1.x indicates the version of jQuery I want to install.

By 'installing' all Bower really has done is put some files in `bower_components`. So I have `jquery.js` in `bower_components/jquery/jquery.js`

### Search

Let's get Normalize.css. (Yes, Bootstrap has normalize.css baked in, but play long for this example) I don't know the Bower package name normalize.css, so search for it.

    bower search normalize
    
    normalize-css git://github.com/necolas/normalize.css.git
    normalize-scss git://github.com/appleboy/normalize.scss.git
    normalize.scss git://github.com/JohnAlbin/normalize.css-with-sass-or-compass.git
    normalize-for-search git://github.com/ikr/normalize-for-search.git
    normalize-stylus git://github.com/skw/normalize.stylus.git
    normalize.styl git://github.com/bymathias/normalize.styl.git
    underscore.normalize git://github.com/michael-lawrence/underscore.normalize.git
    modularized-normalize-scss git://github.com/hail2u/normalize.scss.git
    _normalize.scss git://github.com/jjt/_normalize.scss.git
    scss-normalize git://github.com/kaishin/scss-normalize.git
    string-normalize git://github.com/pammacdotnet/JSStringNormalizer.git


Yeah, I want the one from Necolas

    bower install normalize-css

### Creating bower.json

Now I have this stuff on my computer. If want I re-start this same project on another computer, or provide this same config to a co-worker, I can do that with a manifest file that keeps track of all the packages. That's **bower.json**.

Once we have some packages installed, we run:

    bower init

And it asks a bunch of questions. All the defaults are good, so just like any over-confident developer, I'm just going to keep pressing enter till its done.

**Adding files after bower.json**

    bower install bootstrap --save

Updates bower.json

Now that we have `bower.json`, we can re-use this manifest file, and Bower will install the necessary files.

    rm -rf bower_components/
    bower install

    bower jquery#~2.0.3             cached git://github.com/components/jquery.git#2.0.3
    bower jquery#~2.0.3           validate 2.0.3 against git://github.com/components/jquery.git#~2.0.3
    bower bootstrap#~3.0.0          cached git://github.com/twbs/bootstrap.git#3.0.0
    bower bootstrap#~3.0.0        validate 3.0.0 against git://github.com/twbs/bootstrap.git#~3.0.0
    bower normalize-css#~2.1.3      cached git://github.com/necolas/normalize.css.git#2.1.3
    bower normalize-css#~2.1.3    validate 2.1.3 against git://github.com/necolas/normalize.css.git#~2.1.3
    bower jquery#>= 1.9.0           cached git://github.com/components/jquery.git#2.0.3
    bower jquery#>= 1.9.0         validate 2.0.3 against git://github.com/components/jquery.git#>= 1.9.0
    bower normalize-css#~2.1.3     install normalize-css#2.1.3
    bower jquery#~2.0.3            install jquery#2.0.3
    bower bootstrap#~3.0.0         install bootstrap#3.0.0

    normalize-css#2.1.3 bower_components/normalize-css

    jquery#2.0.3 bower_components/jquery

    bootstrap#3.0.0 bower_components/bootstrap
    └── jquery#2.0.3

Your colleague is like "what r u workin on?" You supply git://github.com/user/project.git. They clone the git repo. They have Bower installed. They do `bower install`. And boom they have all the necessary components.

### List

Let me take a look at what I've installed so far

    bower list
    
    bower check-new     Checking for new versions of the project dependencies..
    tmp /Users/dave/Desktop/tmp
    ├─┬ bootstrap#3.0.0 extraneous
    │ └── jquery#2.0.3
    ├── jquery#2.0.3 extraneous
    └── normalize-css#2.1.3 extraneous

Right, I've installed jQuery, Bootstrap, and Normalize.css. 



## Benefits

+ No need to download/clone other projects just to get that one file (normalize.css, jQuery, underscore)
+ No longer check in other projects into to your repo
+ Keeps packages outside of project file directory all up in `bower_components`

## Why Bower and not ______

**Un-opinionated**

Bower does not prescribe a methodology for how you consume packages. 

Volo, Component, Jam, Ender

+ Confusing
+ Made it harder for devs to adopt

---


Encapsulation
