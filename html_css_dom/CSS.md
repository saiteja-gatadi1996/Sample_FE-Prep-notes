## 1. DIV and SPAN

![alt text](https://user-images.githubusercontent.com/42731246/142733551-fc0aeaf2-91b4-48c7-8ea8-53e7a5d380b1.png)

## 2. Inheritance in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733561-815fb9d9-d023-4514-809c-21c6c8119624.png)

## 3. CSS Specificity

![alt text](https://user-images.githubusercontent.com/42731246/142733573-96c4add1-fef6-4774-a344-3fe4df1dc0ad.png)

![alt text](https://user-images.githubusercontent.com/42731246/142733659-51908f7b-0f0d-486a-9c68-68dedaddd318.png)

## 4. RGB means:

![alt text](https://user-images.githubusercontent.com/42731246/142733665-b227e858-e1e6-4fd4-a65d-dbdad3c2f108.png)

## 5. RGBA (what is A):

![alt text](https://user-images.githubusercontent.com/42731246/142733674-610db881-ffde-473f-9aa9-7a3fd7d3a29b.png)

![alt text](https://user-images.githubusercontent.com/42731246/142733679-fd051132-d046-4a6a-9cca-44468d6a08d1.png)

## 6. HEX Values in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733689-1ab85c7a-bfb1-4c29-b44c-061e17a6ce2d.png)

![alt text](https://user-images.githubusercontent.com/42731246/142733694-8887e58e-9fc3-46d0-a7a0-1fac74c3eb84.png)

## 7. Pixels, Font-Size, Width, Height in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733702-d16b9ab2-48ed-4728-9ca0-ebc6d2783ae5.png)

## 8. Percent in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733706-53b6cc8d-27bb-4924-aa3d-847a5b11fc76.png)

## 9. Em units in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733713-52492351-69b0-4d88-95f1-1b7b5b341546.png)

## 10. Rem in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733717-771535a6-c2d0-4666-a73b-466ea2505a58.png)

## 11. ViewPort Units in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733725-a61bc826-acbe-4754-8540-85eb87257e16.png)

## 12. Calc in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733773-0a7a0eff-ae6d-4fcc-b2d4-7bcc1e274467.png)

## 13. Min height in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733783-42582d11-e605-4696-a6e9-59060acffb06.png)

## 14. Max height in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733788-e205bac0-b0ad-466f-9329-cdc7bff467e7.png)

## 15. Font-Stack Generic Fonts

![alt text](https://user-images.githubusercontent.com/42731246/142733791-12aa07b5-5b3c-454f-95a2-196f4ffaaecb.png)

Instead of one option, we supply multiple. And you can think of it as a fallback system. If none of the five families we passed in are supported by the user browser at the end of the stack we can pass in generic Fonts family and the browser is going to use generic font family to get similar looking fonts.

![alt text](https://user-images.githubusercontent.com/42731246/142733795-36130bd4-a433-421d-8c13-c2b483dbeba9.png)

## 16. Font-weight, Font Style

![alt text](https://user-images.githubusercontent.com/42731246/142733823-2637d6e2-e135-48fc-a240-07a7f767bd23.png)

## 17. Text Indent in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733828-29818aef-4e5e-4975-834c-1cd561ccec9b.png)

```js
<div class='a'>
  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam
    at erat pulvinar, at pulvinar felis blandit. Vestibulum volutpat tellus
    diam, consequat gravida libero rhoncus ut.
  </p>
</div>
```

```css
div.a {
  text-indent: 50px;
}
```

![alt text](/html_css_dom/images_used/text-indent.png)

## 18. Other Text Properties

![alt text](https://user-images.githubusercontent.com/42731246/142733834-a9b525ea-c681-4f12-b196-7ed88e242e9e.png)

## 19. CSS Box Model

![alt text](https://user-images.githubusercontent.com/42731246/142733839-947f5d14-da02-43cc-8214-af0d5f7bd2fd.png)

## 20. Display Property in CSS

![alt text](https://user-images.githubusercontent.com/42731246/142733842-82c1bfc7-e0dd-4cd9-82cf-a67d5abea88e.png)

![alt text](https://user-images.githubusercontent.com/42731246/142733843-098d468e-e2df-4b0b-aef1-5ffd8fa9b87c.png)

```js
<div><span class="a">Aliquam</span> <span class="a">venenatis</span></div>
<div><span class="b">Aliquam</span> <span class="b">venenatis</span></div>
<div><span class="c">Aliquam</span> <span class="c">venenatis</span></div>
```

```css
/* for class 'a', browser doesn't increase width and height because display:inline doesn't respect width and height */
span.a {
  display: inline; /* the default for span */
  width: 100px;
  height: 100px;
  padding: 5px;
  border: 1px solid blue;
  background-color: yellow;
}
/* display inline-block doesn't starts in a new line but respects width and height, whereas not applying doesn't take the full width (I mean by default it acts like inline + doesn't span full width) */
span.b {
  display: inline-block;
  padding: 5px;
  border: 1px solid blue;
  background-color: yellow;
}

/* display block starts in a new line and takes full width by default and respects width and height*/
span.c {
  display: block;
  padding: 5px;
  border: 1px solid blue;
  background-color: yellow;
}
```

![alt text](/html_css_dom/images_used/display_inline_vs_block_vs_inline-block.png)

#### display inline-block doesn't starts in a new line but respects width and height

![alt text](/html_css_dom/images_used/display_inline-block_respects_width_and_height.png)

---

## 54. Can you explain the difference between px, em and rem as they relate to font sizing?

- #### px (Pixels):

  - A px is a unit of measure **corresponding to <u>a single pixel</u> on a screen**.
  - Pixel values are fixed and **_<u>do not change based on the parent element's font size</u>_**. **This makes px very straightforward to use**, as 1px will always be the same size, providing consistency across different elements and layouts.
  - `px` is useful **<u>when you need precise control over element sizing, such as with borders or fixed-size elements</u>**.
  - However, because it's an absolute unit, **<u>it's less flexible when creating responsive designs or improving accessibility for users**</u> who may prefer larger text sizes.

- #### em (Relative to Parent Element)

  - An `em` is a scalable unit that is **relative to the <u>font size of its parent element</u>**.
  - If you set a font size in `em` for an element, **<u>it will be calculated relative to the font size of its direct or nearest specified parent</u>**.
  - **Ex:** For example, **<u>if a parent element has a font size of 16px, 1em in a child element would equal 16px</u>**. If the child element's font size is set to 2em, it would be 32px.
  - `em` is particularly **useful for creating scalable designs that maintain relative sizes within components**. It's beneficial for responsive typography and elements that should scale according to their parent element's font size.

- #### rem (Relative to Root Element)
  - The rem unit is similar to em, but it's relative to the root element (html) of the document, not the parent element.
  - This means that 1rem is always equal to the font size of the root element. If the root element's font size is 16px (which is the default in most browsers), then 1rem equals 16px. Changing the font size of the root element will scale all rem-based sizes throughout the document.
  - rem is excellent for establishing a consistent, scalable foundation for your site's typography and layout spacing. It's especially useful for global sizing and spacing (like margins and paddings), allowing for easy scaling and adjustments while maintaining consistency across the site.

### Summary:

- `px`: Fixed size, good for precision but less flexible for responsive designs.
- `em`: Relative to the parent's font size, great for component-specific scaling.
- `rem`: Relative to the root element's font size, ideal for global site typography and layout consistency.

---


## 62. Which unit of measurement would you prefer among px, em, %, or pt, and why?

#### px(pixels):

- **<u>Preferred for: Fixed layouts</u>**, and when precise control over element sizes is needed.
- preferred for desktop-centric designs or where exact dimensions are required but modern web practices increasingly favor responsive design

#### em :

- **<u>Preferred for: Scalable layouts</u>, typography, and when relative sizing to the parent element is desired**.

#### % :

- **_<u>Preferred for: Responsive layouts</u>, fluid designs, and when you want sizes to be relative to parent container dimensions_**.

#### pt(points) :

- **_<u>Preferred for: Print stylesheets, where physical dimensions are more relevant_**</u>.

---


## 67. Can you name some pseudo-classes you have used in CSS?

- In CSS, pseudo-classes are used to define a special state of an element.

1. **:hover** - Applies when the user hovers over an element with the mouse pointer.
2. **:focus** - Applies when an element has focus.
3. **:active** - Applies when an element is being activated by the user, typically through clicking or tapping.
4. **:visited** - Applies to links that have been visited by the user.
5. **:link** - Applies to links that have not yet been visited.
6. **:first-child** - Targets the first child element within its parent.
7. **:last-child** - Targets the last child element within its parent.
8. **:nth-child(n)** - Targets the nth child element within its parent, where n can be a number, a formula, or even keywords like 'even' or 'odd'.
9. **:nth-of-type(n)** - Similar to `:nth-child(n)` but targets the nth element of a specific type within its parent.
10. **:not(selector)** - Excludes elements that match the given selector.
11. **:checked** - Applies to input elements that are checked, like checkboxes or radio buttons.
12. **:disabled** - Targets elements that are disabled.
13. **:enabled** - Targets elements that are enabled.
14. **:focus-within** - Applies to an element if it or any of its descendants are focused.
15. **:root** - Targets the document's root element, typically `<html>`.

---

## 68. How do you vertically and horizontally align a `<p>` element to the center inside a `<div>`?

```html
<div class="div-container">
  <p>This is a paragraph.</p>
</div>
```

#### Method 1: Flexbox

```js
.div-container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  height: 200px; /* Set to desired height */
}
```

---

#### Method 2: Grid

```js
.div-container {
  display: grid;
  place-items: center; /* Center both vertically and horizontally */
  height: 200px; /* Set to desired height */
}
```

---

#### Method 3: Absolute Positioning

```js
.div-container {
  position: relative;
  height: 200px; /* Set to desired height */
}

.div-container p {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%); /* Adjust for the element's own dimensions */
}

```

----

# <--- SAMPLE CONTENT ENDS --->