## Format a number as a currency string

**Approach Taken**

- paramAmount.toLocaleString which accepts the string of `en-US` and the object which has style and currency
- style key property holds the value of currency
- currency key property holds the value of USD

```js
function formatCurrency(amount) {
  return amount.toLocaleString('en-US', {
    style: 'currency',
    currency: 'USD',
  });
}
const number = 1234.56;
const currencyString = formatCurrency(number);
console.log(currencyString); // "$1,234.56"
```
