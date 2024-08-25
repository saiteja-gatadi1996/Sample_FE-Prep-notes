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

----

# <--- SAMPLE CONTENT ENDS --->