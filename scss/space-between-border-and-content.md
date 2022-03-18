# Space between border and content

To make a space between order and content you can use a before to do that.
Example with a circle : 

![Circle example](./img/circle.png)

```
// Your container
.circle {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  border: 1px solid black;
  border-radius: 50%;
  z-index: 1;
  height: 100px;
  width: 100px;

// The before who's gonna stop at 5px to the border and make that litle space
  &::before {
    content: '';
    position: absolute;
    background: blue;
    border-radius: 50%;
    z-index: -1;
    top: 5px;
    right: 5px;
    bottom: 5px;
    left: 5px;
  }
}
```