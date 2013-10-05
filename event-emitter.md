# Event Emitter

One of the bigger problems I had was callbacks. Let me give you an idea.

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

Well, that's embarrassing. What I'm trying to resolve with this ugly beast is when to trigger a callback. A callback occurs when all the items have stopped moving. But because when you filter someting in Isotope, not all the items may move. So I need to check for that. And there's an issue with CSS transitions, vs. jQuery animation, so I check for that.

If I can sum up what's going on, is that I'm doing this wild conditional checking for every item.

I'm basically going through each one and checking "Are you done? Okay, tell me when you will be. Are you done? Okay, good. got it. Are you done?..." It's ridiculous. And the worst part is, it's still unreliable and buggy.

This is a basic publish/subscribe model. It's a solved problem.

---

EventEmitter is a small component library that done that and only that. You go

    var ee = new EventEmitter();
    ee.on( 'sup', function(){ console.log('yo') });
    // sometime later...
    ee.emit('sup');
    // >> yo

This is incredible useful, becuase I don't have to write 90 lines of buggy code. I can rely on EventEmitter to get the job done, so I can focus on the actual task at hand of simply triggering that callback at the right time.

EventEmitter is so useful, it's a core component to all my libraries

Draggabilly
imagesLoaded
Packery
Masonry
Isotope

