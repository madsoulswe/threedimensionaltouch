# threedimensionaltouch - JQuery Event

##Three-dimensional Touch. The next generation of Multi‑Touch

```
$.event.special.threedimensionaltouch = {
  setup: function() {
    var self = this,
      $self = $(self);
        
    $self.on('touchstart mousedown', function(startEvent) {
      var target = startEvent.target,
          timerEnded = false,
          timeOut;
        	
      function triggerEnd(endEvent) {
        clearTimeout(timeOut);
        
        $self.off('touchend mouseup', triggerEnd);
        
        if (timerEnded && target === endEvent.target) {
          $.event.simulate('threedimensionaltouch', self, endEvent);
        }
      }
      
      timeOut = setTimeout(function(endEvent) {
        timerEnded = true;
        $self.trigger('touchend');
      }, 1000);
      
      $self.on('touchend mouseup', triggerEnd);
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
