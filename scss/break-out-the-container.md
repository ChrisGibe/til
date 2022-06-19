# Break out the container

Your container is inside a layout, for example he have a margin left and right of 120px.
But inside this container, sometime you need to give a full width for a specific block.
The 2 tricks in CSS

```
// Tricks one

.full-width {
    width: 100vw;
    margin-inline-start: 50%;
    transform: translateX(-50%);
}

// Tricks two

.full-width {
   box-shadow: 0 0 0 100vmax #000; (color depend of the background of your block)
   clip-path: inset(0 -100vmax);
}
```

Ressource find on Youtube with this [video](https://www.youtube.com/watch?v=MywezIxlp8Y&t=415s)