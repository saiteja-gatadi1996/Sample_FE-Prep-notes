### Convert String into an object

```js
Input - > stringToObject("a.b.c", "someValue");
Output -> {a: {b: {c: "someValue"}}}
```

```js
function stringToObject(str, finalValue) {
  // Split the string by the dots
  const keys = str.split('.');

  // Use reduceRight to build the object from the inside out
  const result = keys.reduceRight((value, key) => {
    return { [key]: value };
  }, finalValue);

  return result;
}

// Test the function
console.log(stringToObject('a.b.c', 'someValue'));

/*
Output:
{
    "a": {
        "b": {
            "c": "someValue"
        }
    }
}
*/
```
