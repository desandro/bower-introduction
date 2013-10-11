# Results

I am an advocate of Bower not just because I work for Twitter. But because I needed Bower for my own projects.

Bower has been out for a year. I've been using it for just as long. It's made my job as a developer a lot better. Here's why.

I maintain a couple projects, Masonry, Isotope, and imagesLoaded.

## Encapsulation

I'm sure 'encapsulation' has a proper definition, but I think its most obvious definition works best - Encapsulation is putting things into capsules. In other words, breaking up something into smaller pieces that are easier to swallow.

Encapsulation is a core tenet of programming. We all know we shouldn't write code like this

    _processStyleQueue : function( $elems, callback ) {
      // are we animating the layout arrangement?
      // use plugin-ish syntax for css or animate
      var styleFn = !this.isLaidOut ? 'css' : (
            this.isUsingJQueryAnimation ? 'animate' : 'css'
          ),
          animOpts = this.options.animationOptions,
          onLayout = this.options.onLayout,
          objStyleFn, processor,
          triggerCallbackNow, callbackFn;
      
      // default styleQueue processor, may be overwritten down below
      processor = function( i, obj ) {
        obj.$el[ styleFn ]( obj.style, animOpts );
      };
      
      if ( this._isInserting && this.isUsingJQueryAnimation ) {
        // if using styleQueue to insert items
        processor = function( i, obj ) {
          // only animate if it not being inserted
          objStyleFn = obj.$el.hasClass('no-transition') ? 'css' : styleFn;
          obj.$el[ objStyleFn ]( obj.style, animOpts );
        };
    
      } else if ( callback || onLayout || animOpts.complete ) {
        // has callback
        var isCallbackTriggered = false,
            // array of possible callbacks to trigger
            callbacks = [ callback, onLayout, animOpts.complete ],
            instance = this;
        triggerCallbackNow = true;
        // trigger callback only once
        callbackFn = function() {
          if ( isCallbackTriggered ) {
            return;
          }
          var hollaback;
          for (var i=0, len = callbacks.length; i < len; i++) {
            hollaback = callbacks[i];
            if ( typeof hollaback === 'function' ) {
              hollaback.call( instance.element, $elems, instance );
            }
          }
          isCallbackTriggered = true;
        };
    
        if ( this.isUsingJQueryAnimation && styleFn === 'animate' ) {
          // add callback to animation options
          animOpts.complete = callbackFn;
          triggerCallbackNow = false;
      
        } else if ( Modernizr.csstransitions ) {
          // detect if first item has transition
          var i = 0,
              firstItem = this.styleQueue[0],
              testElem = firstItem && firstItem.$el,
              styleObj;
          // get first non-empty jQ object
          while ( !testElem || !testElem.length ) {
            styleObj = this.styleQueue[ i++ ];
            // HACK: sometimes styleQueue[i] is undefined
            if ( !styleObj ) {
              return;
            }
            testElem = styleObj.$el;
          }
          // get transition duration of the first element in that object
          // yeah, this is inexact
          var duration = parseFloat( getComputedStyle( testElem[0] )[ transitionDurProp ] );
          if ( duration > 0 ) {
            processor = function( i, obj ) {
              obj.$el[ styleFn ]( obj.style, animOpts )
                // trigger callback at transition end
                .one( transitionEndEvent, callbackFn );
            };
            triggerCallbackNow = false;
          }
        }
      }
      // process styleQueue
      $.each( this.styleQueue, processor );  
      if ( triggerCallbackNow ) {
        callbackFn();
      }  
      // clear out queue for next time
      this.styleQueue = [];
    },

Ugh this terrible. I know because I wrote it. It has conditionals within conditionals and sometimes I'm overwriting a function. It's hard to follow becuase it cannot be parsed. You can't make sense of it.

To resolve this terrible code, I would begin by figuring out where I can start sectioning stuff off.  Breaking something big down into smaller pieces that are easier to swallow.

Here is the kicker: We can apply this same great concept, not just to our code, but to our projects.

##

## Growing out of mono-file-ism

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





## De-duping baked-in code



---

---

---

