# Scroll Bar

### pug

```pug
div.box#box
  div.wrapper#wrapper
    div.content#content
  div.scroll_bar_box
    div.scroll_bar#scroll_bar
```
### sass

```sass
body
  background-color: #45c9b5

.box
  width: 250px
  height: 400px
  border: 2px dotted #FFF
  margin: 0 auto
  padding: 10px 5px 10px 10px
  box-sizing: border-box
  border-radius: 10px
  position: relative
  
  .wrapper
    width: 92%
    height: 100%
    overflow-y: scroll
    // border: 1px solid red
    display: inline-block
    &::-webkit-scrollbar
      display: none

  .content
    width: 100%
    height: 2400px
    border-radius: 20px
    background-color: #c67bbf
    background-image: url("https://www.transparenttextures.com/patterns/cubes.png")
    
  .scroll_bar_box
    width: 4%
    height: 100%
    display: inline-block
    position: relative
    // border: 1px solid green
    
  .scroll_bar
    width: 6px
    height: 10px
    background-color: #36a191
    position: absolute
    top: 0
    right: 0
    border-radius: 5px
```

### javascript

```js
var ScrollBox = (function() {
  var wrapper = document.getElementById('wrapper');
  var content = document.getElementById('content');
  var scroll_bar = document.getElementById('scroll_bar');
  
  wrapper.addEventListener('scroll', scroll_percent);
  
  function trigger() {
    // scrollHeight = 內容高度, 包含因捲動而未顯示的內容
    // scrollTop = 因捲動而未顯示的內容高度
    var scroll_height = wrapper.clientHeight / wrapper.scrollHeight * wrapper.clientHeight;
    if (scroll_height >= wrapper.clientHeight) {
        scroll_height = 0;
    }
    scroll_bar.style.height = scroll_height + 'px';
    scroll_bar.style.top = 0;
  }
  
  function scroll_percent(event) {
    var percent = (this.scrollTop / this.scrollHeight) * 100;
    percent += "%";
    scroll_bar.style.top = percent;
  }
  
  return {
    trigger: trigger
  }
  
})();

ScrollBox.trigger();
```

https://codepen.io/krmfla/pen/gOYrWeg
