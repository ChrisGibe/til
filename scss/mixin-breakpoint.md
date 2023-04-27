# Mixin breakpoint

Use media queries and automatically generate specific css.
Inspired by https://github.com/nex3/sass/issues/408#issuecomment-6086901

```
$media-queries: true !default; // true by default

@mixin breakpoint($min-width: false, $max-width: false, $prefix: false) {
  @if $media-queries {
    @if $min-width {
      @if $max-width {
        @media all and (min-width: $min-width) and (max-width: $max-width) {
          @if $prefix {
            #{"." + $prefix} {
              @content;
            }
          }

          @else {
            @content;
          }
        }
      }

      @else {
        @media all and (min-width: $min-width) {
          @if $prefix {
            #{"." + $prefix} {
              @content;
            }
          }

          @else {
            @content;
          }
        }
      }
    }

    @else if $max-width {
      @media all and (max-width: $max-width) {
        @if $prefix {
          #{"." + $prefix} {
            @content;
          }
        }

        @else {
          @content;
        }
      }
    }
  }

  @else if $min-width and $min-width <= $max-desktop and
    (not $max-width or $max-width and $max-width >= $max-desktop) {
    @content;
  }
}
```