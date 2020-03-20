# Deep Clone

```js
// Deep Clone
function Deep_clone(object){
  var new_obj = {};
  for(var item in object) {
    if(object.hasOwnProperty(item)) {
      if (typeof item === 'object') {
        if(Array.isArray(item)) {
          new_obj[item] = [];
          for(var i = 0, max = item.length; i < max; i++) {
             new_obj[item].push(item[i]);
           }
        } else {
          if(item !== object) {
             new_obj[item] = Deep_clone(item);
          } else {
            new_obj[item] = object;
          }
        }
      } else if(typeof item === 'function') {
        
      }
      else {
        new_obj[item] = object[item];
      }
    }
  }
  return new_obj;
}
```

sample code

```js
var a = {
  'number': 1,
  'string': 'is A',
  'boolean': true,
  'empty': null,
  'undef': undefined,
  'not_number': NaN,
  'obj': {
    b: {
      c: 2
    }
  },
  'arr': [2, 3, 4],
  'func': function() {
    console.log('yo');
  },
  'date': new Date()
};

var b = Deep_clone(a);
b.string = "is B"
console.log(b);

// replace origin object
a.number = 0;
a.boolean = false;
a.empty = 'fill';
a.undef = '';
a.not_number = -1;
a.obj = {
  c: 0
};
a.arr = [0, 0, 0];
a.func = function() {
  console.log('hey');
}
a.date = new Date(900000000000);
//
console.log(a);
console.log(b);

// By doing this you will lose any Javascript property that has no equivalent type in JSON, 
// like Function or Infinity. Any property that’s assigned to undefined will be ignored by JSON.stringify, 
// causing them to be missed on the cloned object.
var c = JSON.parse(JSON.stringify(b));
c.string = 'is C'
console.log(c);
```

https://codepen.io/krmfla/pen/mNWRep
