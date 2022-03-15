# Create multiples CSS class with mutliples variables

For example, if you have a lot of font sizes for a website, and you don't want to create a class for each sizes.
You can easely create a `@each` with a `@mixin`.

```
$f-sizes: 36, 32, 28, 24, 20, 18, 16, 14, 13, 12, 10;
$f-weights: 500, 400;

// Mixin for my font sizes and line height
@mixin f-size($f-size){
  font-size: #{$f-size}px;
  line-height: $f-size+4px;
}

// Mixin for my font weights
@mixin f-weight($f-weight){
  font-weight: $f-weight;
}

@each $f-size in $f-sizes {
    .txt-#{$f-size} {
      @include f-size($f-size);
    }
}

@each $f-weight in $f-weights {
  .w-#{$f-weight} {
    @include f-weight($f-weight);
  }
}

```

Has you can see, i can create automatically a lot of CSS class with all the font-sizes, mixed with the line-height and same things for my font weight.

Now in my HTML i can call all this class like that, example :

```
<h1 class="txt-36 w-500">My Title</h1>
<p class="txt-18 w-400">My text</p>
```

