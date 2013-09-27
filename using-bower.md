## 5 minute intro to using bower

install with node

    sudo npm install -g bower

_Watch out Command Line._

> You probably have one of two reactions. For the hard-core devs are thinking "HELL YEAH ABOUT TIME TO SEE SOME COMMAND LINE ACTION." Totally pumped, and the other half is "Oh crap, this is going to be a super neck-beardy." But don't worry, Bower works via the command line, but it's not obnoxious about it. Bear with me, nearly all the commands are super simple.

**Install packages**

    bower install jquery

**Find packages**

    bower search normalize

**Creating bower.json**

    bower init

**Adding files after bower.json**

    bower install bootstrap --save

Updates bower.json

Now that we have `bower.json`, we can re-use this manifest file, and Bower will install the necessary files

Your colleague is like "what r u workin on?" You supply git://github.com/user/project.git. They clone the git repo. They have Bower installed. They do `bower install`. And boom they have all the necessary components.

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
