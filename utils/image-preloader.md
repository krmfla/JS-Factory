# Image Preloader

```js
// sample code
var data = [
  'https://krmfla.github.io/example/sample_video/city.jpg',
  'https://krmfla.github.io/example/sample_video/cheese.png'
];

var loadbar_handle = function(obj) {
  console.log(obj.current + '/' + obj.total);
}

Preload(data, null, loadbar_handle);


// Preload Method
function Preload(data_array, init_action, when_done, when_complete) {
    var counts = 0;
    var body = document.querySelector('body');
    var wrapper = document.createElement('DIV');
    var handle_loaded = function() {
        console.log('image loaded');
        counts += 1;
        if (typeof when_done === 'function') {
            when_done({
              current: counts,
              total: data_array.length
            });
        }
        if (counts === data_array.length) {
            console.warn('all loaded');
            if (typeof when_complete === 'function') {
                when_complete();
            }
        }
    }
    wrapper.style.position = 'fixed';
    wrapper.style.top = '-200%';
    wrapper.style.left = '-200%';
    wrapper.style.width = '1px';
    wrapper.style.height = '1px';
    wrapper.style.overflow = 'hidden';
    for (var i = 0; i < data_array.length; i++) {
        console.log(i);
        var img = document.createElement('IMG');
        img.onload = handle_loaded;
        img.src = data_array[i];
        wrapper.appendChild(img);
    }
    body.appendChild(wrapper);
    if (typeof init_action === 'function') {
        init_action();
    }
}
```

https://codepen.io/krmfla/pen/ExxPqKr
