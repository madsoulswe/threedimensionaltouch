# threedimensionaltouch - JQuery Event

##Three-dimensional Touch. The next generation of Multi‑Touch

```
$.event.special.threedimensionaltouch = {
  setup: function() {
    var self = this,
      $self = $(self);
        
    $self.on('touchstart mousedown', function(startEvent) {
      var timeOut;
        	
      function triggerClear() {
        clearTimeout(timeOut);
        $(document).off('touchend mouseup', triggerClear);
      }
            
      timeOut = setTimeout(function() {
        triggerClear();
        $.event.simulate('threedimensionaltouch', self);
      }, 1000);
            
      $(document).on('touchend mouseup', triggerClear);
    });
  }
};
```

###Usage

```
$([element]).on("threedimensionaltouch", function() {
  alert("Three-Dimensional-Touch"); 
});
```

*No, actually it's just a delayed touchend-event and not a pressure sensing technology*
