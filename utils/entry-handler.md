# Entry Handler

### html
```html
<div id='app' class='main'>
  <section id='s1' class='section1'>
  </section>
  <section id='s2' class='section2'></section>
  <section id='s3' class='section3'>
    <div id='spot' class='spot'></div>
  </section>
  <section id='s4' class='section4'>
    <div id='spot2' class='spot'></div>
  </section>
  <section id='s5' class='section5'>

  </section>
</div>
```

### css
```css
body,
html {
  padding: 0;
  margin: 0;
}
.main {
  width: 100%;
  margin: 0 auto;
  border: 1px solid black;
  padding: 10px;
  overflow: hidden;
  box-sizing: border-box;
}
.main section {
  width: 100%;
  height: 400px;
  background-color: #eee;
  margin-bottom: 10px;
  transition: all 0.6s;
}
.main section.active {
  background-color: orange;
}

.spot {
  width: 20px;
  height: 20px;
  border: 1px solid red;
  transition: all 0.6s;
}

.spot.active {
  background-color: red;
}
```

### javascript
```js
// How to use
var entry_handler = new EntryHandler();

entry_handler.init({
  scope_top: 20,
  scope_bottom: 80,
  debug_mode: true
});

entry_handler.setActive("#spot");
entry_handler.exec("#spot2", function() {
  this.ref.style.padding = "20px";
  this.ref.style.backgroundColor = "red";
});
entry_handler.setActive("#s5");

// Entry Handler Constructor
function EntryHandler() {
  var _array = [];
  var _config = {};
  var body = document.querySelector("body");

  function init(config) {
    console.dir(window);
    console.dir(document);
    console.dir(body);
    console.log(body.clientHeight);
    _config.scope_top = config.scope_top || 0;
    _config.scope_top = _config.scope_top / 100 * window.innerHeight;
    _config.scope_bottom = config.scope_bottom || 0;
    _config.scope_bottom = _config.scope_bottom / 100 * window.innerHeight;

    if (config.debug_mode) {
      createDebugLine();
    }
    window.addEventListener("scroll", scopeDetect);
  }

  function createDebugLine() {
    create("scope_top", _config.scope_top);
    create("scope_bottom", _config.scope_bottom);

    function create(text, position_y) {
      var element = document.createElement("DIV");
      element.style.position = "fixed";
      element.style.zIndex = 9999;
      element.style.width = "100%";
      element.style.fontSize = "12px";
      element.style.color = "red";
      element.style.top = position_y + "px";
      element.style.paddingLeft = "5px";
      if (text === "scope_top") {
        element.style.borderTop = "1px solid red";
        element.innerText = "scope top";
      } else {
        element.style.borderBottom = "1px solid red";
        element.innerText = "scope bottom";
      }
      document.querySelector("body").appendChild(element);
    }
  }

  function scopeDetect() {
    for (var i = 0; i < _array.length; i++) {
      var rect = getPosition(_array[i].ref);
      var top = rect.top;
      var bottom = rect.top + rect.height;
      if (_config.scope_top <= top && top <= _config.scope_bottom) {
        handle_entry();
        return;
      } else if (
        _config.scope_top <= bottom &&
        bottom <= _config.scope_bottom
      ) {
        handle_entry();
        return;
      }
    }

    if (!_array.length) {
      window.removeEventListener("scroll", scopeDetect);
    }

    function handle_entry() {
      _array[i].callback();
      _array.splice(i, 1);
      repeat = true;
      scopeDetect();
    }
  }

  function getPosition(element) {
    var rect = element.getBoundingClientRect();
    return rect;
  }

  function setActive(query_string) {
    var element = document.querySelector(query_string);
    var obj = {
      ref: element,
      callback: function() {
        element.classList.add("active");
      }
    };
    _array.push(obj);
  }

  function exec(query_string, _callback) {
    var element = document.querySelector(query_string);
    var obj = {
      ref: element,
      callback: _callback
    };
    _array.push(obj);
  }

  return {
    init: init,
    exec: exec,
    setActive: setActive
  };
}
```
