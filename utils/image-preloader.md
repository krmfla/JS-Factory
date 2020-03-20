# Image Preloader

```js
var data = [
  'https://krmfla.github.io/example/sample_video/city.jpg',
  'https://krmfla.github.io/example/sample_video/cheese.png'
];

Preload(data);

function Preload(data_array, init_action, when_done, when_complete) {
    var counts = 0;
    var body = document.querySelector('body');
    var wrapper = document.createElement('DIV');
    var handle_loaded = function() {
        counts += 1;
        if (typeof when_done === 'function') {
            when_done(counts);
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
