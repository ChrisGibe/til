# Create a custom scroll bar mixin

```
@mixin scroll_custom() {
  /* width */
  &::-webkit-scrollbar {
    width: 5px;
  }

  /* Track */
  &::-webkit-scrollbar-track {
    border-radius: 10px;
    border-right: 1px solid transparent;
    box-shadow: inset 0 0 5px transparent;
  }

  /* Handle */
  &::-webkit-scrollbar-thumb {
    background: #000;
    border-radius: 10px;
  }

  /* Handle on hover */
  &::-webkit-scrollbar-thumb:hover {
    background: #fff;
  }
}
```