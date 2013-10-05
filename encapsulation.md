I'm sure 'encapsulation' has a proper definition, but I think its most obvious definition works best - Encapsulation is putting things into capsules. In other words, breaking up something into smaller pieces that are easier to swallow.

This is another foundational concept from programming that we all apply in our code. You know you shouldn't be writing code like this.

    this.layout = function() {
      this.getSize();
      this._getMeasurement( 'columnWidth', 'outerWidth' );
      this._getMeasurement( 'gutter', 'outerWidth' );
      this.measureColumns();
      
      if ( this.stamps && !this.stamps ) {
        this._getBoundingRect();
        for ( var i=0, len = this.stamps.length; i < len; i++ ) {
          var stamp = this.stamps[i];
          this._manageStamp( stamp );
        }
      }
      
      items = this._getItemsForLayout( items );
      this._layoutItems( items, isInstant );
    };


Instead of big functions that do everything, you can section off portions of it. This gives structure to your code. It helps you understand the code as you don't have to keep the entire mental model in your head.

    this.layout = function() {
      this.resetLayout();
      this.manageStamps();
      this.layoutItems();
    };
    
    this.resetLayout = function() {
      this.getSize();
      this._getMeasurement( 'columnWidth', 'outerWidth' );
      this._getMeasurement( 'gutter', 'outerWidth' );
      this.measureColumns();
    }
    
    this.manageStamps = function() {
      if ( !this.stamps || !this.stamps.length ) {
        return;
      }
      this._getBoundingRect();
      for ( var i=0, len = this.stamps.length; i < len; i++ ) {
        var stamp = this.stamps[i];
        this._manageStamp( stamp );
      }
    };
    
    this.layoutItems = function() {
      var items = this._getItemsForLayout( items );
      this._layoutItems( items, isInstant );
    };

This same principle of encapsulation can be put to our projects.

### EventEmitter


