# Text Border

### pug

```pug
p 
  span 123
```

### scss

```scss
// Stroke font-character
// @param  {Integer} $stroke - Stroke width
// @param  {Color}   $color  - Stroke color
// @return {List}            - text-shadow list
@function stroke($stroke, $color) {
  $shadow: ();
  $from: $stroke*-1;
  @for $i from $from through $stroke {
   @for $j from $from through $stroke {
      $shadow: append($shadow, $i*1px $j*1px 0 $color, comma);
    }
  }
  @return $shadow;
}
// Stroke font-character
// @param  {Integer} $stroke - Stroke width
// @param  {Color}   $color  - Stroke color
// @return {Style}           - text-shadow
@mixin stroke($stroke, $color) {
  text-shadow: stroke($stroke, $color);
}

p {
  padding: 10px;
  span {
    font-size: 36px;
    font-weight: bold;
    color: blue;
    @include stroke(5, orange);
  }
}
```

https://codepen.io/krmfla/pen/VwZKdrR
