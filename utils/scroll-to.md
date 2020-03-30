# Scroll To

```javascript
var scroll_to = (function() {
  var range = 50;
  var target_y = null;
  var active = false;
  var timer;
  
  return function(element) {
    if (typeof element === 'object' && active) {
      console.warn('active');
      return;
    }
    if (!target_y) {
      target_y = element.offsetTop;
      active = true;
    }

    var top = document.documentElement.scrollTop || document.body.scrollTop;
    if (Math.abs(target_y - top) >= range) {
      if (target_y > top) {
        window.scrollTo(0, top + range);
      } else {
        window.scrollTo(0, top - range);
      }
      if (typeof window.requestAnimationFrame === 'function') {
          window.requestAnimationFrame(scroll_to);
      } else {
        timer = setTimeout(() => {
          scroll_to();
        }, 1000 / 60);
      }
      
    } else {
      window.scrollTo(0, target_y);
      clearTimeout(timer);
      target_y = null;
      active = false;
    }
  }
})();

// example
var main = document.getElementById('main');
var p = document.getElementById('p');

main.onclick = function() {
  scroll_to(p);
}
```

https://codepen.io/krmfla/pen/zYGLzBz
