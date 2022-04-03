# Create multiples CSS class with mutliples variables

For example, if you have a lot of font sizes for a website, and you don't want to create a class for each sizes.
You can easely create a `@each` with a `@mixin`.

```
// All your size gather by 2 (Font size on desktop, and when you are on mobile)

$f-sizes: ((36, 28), (32, 24), (24, 18), (20, 18), (18, 16), (16, 16),  
(14, 14), (13, 13), (12, 12), (10, 10));

// All your font weight
$f-weights: 500, 400;


// Mixin to return a font size on desktop and mobile, 
and line height on desktop and mobile

@mixin f-size($f-size-desktop, $f-size-mobile: $f-size-desktop){
  font-size: #{$f-size-mobile}px;
  line-height: #{$f-size-mobile + 4}px;
  @media only screen and (min-width: 991px) {
    font-size: #{$f-size-desktop}px;
    line-height: #{$f-size-desktop + 4}px;
  }
}

// Mixin to return a font weight 
@mixin f-weight($f-weight){
  font-weight: $f-weight;
}

@each $f-size-desktop, $f-size-mobile in $f-sizes {
    .txt-#{$f-size-desktop} {
      @include f-size($f-size-desktop, $f-size-mobile);
    }
}

@each $f-weight in $f-weights {
    .w-#{$f-weight} {
      @include $f-weight($f-weight);
    }
}
```

I can create automatically a lot of CSS class with all the font-sizes, mixed with the line-height and same things for my font weight.

Now in my HTML i can call all this class like that, example :

```
<h1 class="txt-36 w-500">My Title</h1>
<p class="txt-18 w-400">My text</p>
```

