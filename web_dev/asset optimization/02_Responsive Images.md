

## Responsive Images

-  Following HTML and CSS code helps us to <ins>***display an image of a cat with responsive sizing and resolution switching based on the viewport width or device's display capabilities***</ins>.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="index.css" />
  </head>
  <body>
    <img
      src="cat-500.jpg"
      srcset="cat-500.jpg 500w, cat-1000.jpg 1000w, cat-1500.jpg 1500w"
    />
  </body>
</html>
```

```css
img {
  /* width: 500px; */
  width: 100%;
}
```

### Summary:

### `srcset`: 
  - Defines **a set of images along with their widths in pixels** (500w, 1000w, 1500w). 
  - The **browser will choose the most appropriate image based on the current viewport width and the device's pixel density**. 
  - This attribute is used for responsive images, allowing the browser to select a smaller image for smaller viewports and a larger image for larger viewports or high-density displays, optimizing load times and visual quality.
- cat-500.jpg 500w: Indicates that **cat-500.jpg is 500 pixels wide** and should be used for viewports requiring up to 500 pixels width images.
- cat-1000.jpg 1000w: Indicates that **cat-1000.jpg is 1000 pixels wide**, suitable for larger viewports.
- cat-1500.jpg 1500w: For even larger viewports or high-density screens, **cat-1500.jpg, which is 1500 pixels wide**, may be selected.