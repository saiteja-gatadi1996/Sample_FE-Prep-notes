## NodeList into array

```js
function convertNodeListIntoArray(nodeList) {
  return [...nodeList];
  // you can also use this, return Array.from(nodeList)
}

const divs = document.querySelectorAll('div'); // NodeList
const divsArray = convertNodeListIntoArray(divs);
console.log('divsInArray', divsArray);
```
